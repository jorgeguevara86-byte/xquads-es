---
task: diagnose()
responsavel: "@vision-chief"
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
  - "[ ] Consulta analizada con intención y función comercial" 
  - "[ ] Respuesta rápida proporcionada" 
  - "[ ] Ruta ejecutada o respuesta directa dada" 
---

# Tarea: Diagnóstico - Equipo de nivel C

## Metadata

| Campo | Valor |
|---------------|----------------------------------------------------|
| ID de tarea | `c-level:diagnose` |
| Command       | `@c-level diagnose "{query}"`                      |
| Orchestrator  | `vision-chief`                                     |
| Propósito | Analice la solicitud del usuario, proporcione una respuesta rápida y diríjala al mejor ejecutivo de C-suite |

## Inputs

| Entrada | Fuente | Requerido | Descripción |
|--------------|-------------|----------|------------------------------------------|
| `query` | Mensaje de usuario | Sí | La pregunta o petición del usuario |
| `context` | Sesión | No | Contexto de conversación anterior |
| `role_hint` | User/Auto | No | Función de nivel C sugerida (CEO, COO, etc.) |

## Preconditions

- Configuración del escuadrón cargada (`config/config.yaml`)
- Catálogo de enrutamiento disponible (`data/routing-catalog.yaml`)
- Existe al menos una definición de agente especialista en `agents/`

## Phases

### Fase 1: Analizar (vision-chief)

1. Lea la consulta del usuario y extraiga:
   - **Intención**: Lo que el usuario quiere lograr
   - **Palabras clave del dominio**: coincidencia con las palabras clave del catálogo de enrutamiento
   - **Función empresarial**: Qué dominio de C-suite (visión, operaciones, marketing, tecnología, infraestructura, IA)
   - **Complejidad**: Simple (respuesta directa) vs Complejo (necesita especialista)

2. Clasifique el tipo de consulta:
   - `question` — Necesita una respuesta informativa
   - `strategy` — Necesita un plan o dirección estratégica
   - `decision` — Necesita executive-level marco de decisión
   - `assessment` — Necesita evaluación del estado actual
   - `transformation` — Necesita gestión del cambio o plan de transformación digital

### Fase 2: Enrutamiento del partido

1. Load `data/routing-catalog.yaml`
2. Califique cada dominio según las palabras clave extraídas
3. Identify:
   - **Agente principal**: mejor coincidencia (mayor superposición de palabras clave)
   - **Agente secundario**: Backup o perspectiva complementaria
   - **Nivel de confianza**: ALTO (>= 3 coincidencias de palabras clave), MEDIO (2 coincidencias), BAJO (0-1 coincidencias)

4. Guía de enrutamiento ejecutivo:
   | Área problemática | Agente principal | Agente secundario |
   |-----------------------------|------------------|------------------|
   | Vision/strategy/fundraising | vision-chief     | coo-orchestrator |
   | Operations/scaling/process  | coo-orchestrator | vision-chief     |
   | Marketing/brand/GTM         | cmo-architect    | vision-chief     |
   | Technology/architecture     | cto-architect    | cio-engineer     |
   | Infrastructure/security     | cio-engineer     | cto-architect    |
   | AI/ML/digital transformation| caio-architect   | cto-architect    |

### Fase 3: Respuesta

1. **Proporcione siempre primero una respuesta rápida**: de 2 a 4 oraciones que aborden directamente la consulta
2. Include:
   - Respuesta directa a la pregunta desde la perspectiva del CEO
   - Qué rol ejecutivo es más relevante
   - Qué profundidad estratégica agregaría el especialista

### Fase 4: Ruta (si es necesario)

1. Si la confianza es ALTA o MEDIA:
   - Anuncie el objetivo de enrutamiento: "Enrutamiento a @{agent} para asesoría ejecutiva"
   - Pasar contexto: consulta original + intención analizada + función empresarial
2. Si la confianza es BAJA:
   - NO enrutar: responde directamente como vision-chief
   - Ofrece al usuario una opción de ejecutivos si la consulta abarca varios dominios.

## Formato de salida

```yaml
diagnosis:
  query_summary: "{resumen de 1 línea}" 
  intent: "{pregunta|estrategia|decisión|evaluación|transformación}" 
  business_function: "{visión|operaciones|marketing|tecnología|infraestructura|ai}" 
  quick_answer: "{respuesta directa de 2 a 4 oraciones}"
  routing:
    confidence: "{ALTO|MEDIO|BAJO}" 
    primary_agent: "{agent-id}"
    secondary_agent: "{agent-id}"
    reason: "{por qué este ejecutivo es la mejor opción}" 
  routed: {true|false}
```

## Reglas de veto

1. **NUNCA enrute sin proporcionar primero una respuesta rápida**: el usuario siempre debe obtener valor inmediato
2. **NUNCA realice rutas con BAJA confianza**: responda directamente y ofrezca opciones en su lugar
3. **NUNCA dirija a más de un agente simultáneamente** — Elija al mejor ejecutivo
4. **NUNCA brinde consejos tácticos sin un marco estratégico**: conéctese siempre con los resultados comerciales
5. **NUNCA haga promesas sobre resultados financieros específicos**: proporcione marcos, no garantías

## Criterios de finalización

- [ ] Consulta analizada con intención y clasificación de funciones comerciales
- [ ] Catálogo de enrutamiento consultado y puntuación de confianza
- [ ] Se proporciona respuesta rápida (obligatoria, independientemente de la ruta)
- [ ] Ruta ejecutada si confianza >= MEDIA, o respuesta directa si BAJA
- [ ] El formato de salida coincide con el esquema anterior
