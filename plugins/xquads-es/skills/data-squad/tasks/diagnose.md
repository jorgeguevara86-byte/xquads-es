---
task: diagnose()
responsavel: "@data-chief"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: query
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: diagnosis
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Consulta analizada con intención y clasificación de dominio" 
  - "[ ] Respuesta rápida proporcionada" 
  - "[ ] Ruta ejecutada o respuesta directa dada" 
---

# Task: Diagnose — Data Squad

## Metadata

| Campo | Valor |
|---------------|----------------------------------------------------|
Silencioso ID de tareas `data-squad:diagnose`                              |
| Command       | `@data-squad diagnose "{query}"`                   |
| Orchestrator  | `data-chief`                                       |
TEN Purpose TENPIR La solicitud del usuario, proporcionar una respuesta rápida y la ruta al mejor experto en datos TEN

## Inputs

| Entrada | Fuente | Requerido | Descripción |
|--------------|-------------|----------|------------------------------------------|
| `query` | Mensaje de usuario | Sí | La pregunta o petición del usuario |
| `context` | Sesión | No | Contexto de conversación anterior |
| `domain_hint`| User/Auto   Silencio No Silencio Dominio sugerido (análisis, crecimiento, etc.)

## Preconditions

- Configuración del escuadrón cargada (`config/config.yaml`)
- Catálogo de enrutamiento disponible (`data/routing-catalog.yaml`)
- Existe al menos una definición de agente especialista en `agents/`

## Phases

### Fase 1: Parse (data-chief)

1. Lea la consulta del usuario y extraiga:
   - **Intención**: Lo que el usuario quiere lograr
   - **Palabras clave del dominio**: coincidencia con las palabras clave del catálogo de enrutamiento
   - **Vantura de datos**: Donde está el usuario (sin datos, analítica básica, avanzada)
   - **Complejidad**: Simple (respuesta directa) vs Complejo (necesita especialista)

2. Clasifique el tipo de consulta:
   - `question` — Necesita una respuesta informativa
   - `analysis` - Necesidades de análisis o interpretación de datos
   - `strategy` - Necesita un growth/retention/community plan
   - `framework` — Necesita un marco específico de experto aplicado
   - `troubleshoot` — Necesita diagnosticar un problema métrico

### Fase 2: Enrutamiento del partido

1. Load `data/routing-catalog.yaml`
2. Califique cada dominio según las palabras clave extraídas
3. Identify:
   - **Agente principal**: mejor coincidencia (mayor superposición de palabras clave)
   - **Agente secundario**: Backup o perspectiva complementaria
   - **Nivel de confianza**: ALTO (>= 3 coincidencias de palabras clave), MEDIO (2 coincidencias), BAJO (0-1 coincidencias)

4. Guía de selección de expertos:
   Silencioso Área de Problemas Silencio Agente Primario Silencioso Agente Secundario
   |---------------------------|-------------------|------------------|
   | Web/marketing analytics   | avinash-kaushik   | sean-ellis       |
   | Customer value/segmentation | peter-fader     | nick-mehta       |
   | Growth/acquisition        | sean-ellis        | avinash-kaushik  |
   | Audience/content          | wes-kao           | david-spinks     |
   | Retention/churn           | nick-mehta        | peter-fader      |
   | Community                 | david-spinks      | nick-mehta       |

### Fase 3: Respuesta

1. **Proporcione siempre primero una respuesta rápida**: de 2 a 4 oraciones que aborden directamente la consulta
2. Include:
   - Respuesta directa a la cuestión
   - El marco de un experto es el más relevante
   - ¿Qué valor más profundo daría el especialista

### Fase 4: Ruta (si es necesario)

1. Si la confianza es ALTA o MEDIA:
   - Anunciar al objetivo de la ruta: "Routing to @{agent} para un análisis más profundo"
   - Pase context: consulta original + intención parisada + clasificación de dominio
2. Si la confianza es BAJA:
   - NO enrutéis — responda directamente como data-chief
   - Ofrezca al usuario una selección de expertos si la consulta es ambigua

## Formato de salida

```yaml
diagnosis:
  query_summary: "{resumen de 1 línea}" 
  intent: "{pregunta sobre la tortura, la tortura, la tortura, la muerte, la muerte, la muerte, la muerte, la muerte, la muerte, la muerte, la muerte, la muerte, la muerte, la muerte, la muerte, la muerte, la muerte, la muerte, la muerte, la muerte, la muerte." 
  domain: "{análisis de la vida privada}" 
  quick_answer: "{respuesta directa de 2 a 4 oraciones}"
  routing:
    confidence: "{ALTO|MEDIO|BAJO}" 
    primary_agent: "{agent-id}"
    secondary_agent: "{agent-id}"
    reason: "¿Por qué este experto es el mejor partido?" 
  routed: {true|false}
```

## Reglas de veto

1. **NUNCA enrute sin proporcionar primero una respuesta rápida**: el usuario siempre debe obtener valor inmediato
2. **NUNCA realice rutas con BAJA confianza**: responda directamente y ofrezca opciones en su lugar
3. **Nunca ruta a más de un agente simultáneamente** — Elija el mejor experto
4. **Nunca recomendar un marco sin nombrar al experto** — Cuestiones de atribución
5. **Nunca adivinar los datos que el usuario no ha proporcionado** — Pregunte primero por los detalles

## Criterios de finalización

- [ ] Consulta analizada con la clasificación de intenciones y dominios
- [ ] Catálogo de enrutamiento consultado y puntuación de confianza
- [ ] Se proporciona respuesta rápida (obligatoria, independientemente de la ruta)
- [ ] Ruta ejecutada si confianza >= MEDIA, o respuesta directa si BAJA
- [ ] El formato de salida coincide con el esquema anterior
