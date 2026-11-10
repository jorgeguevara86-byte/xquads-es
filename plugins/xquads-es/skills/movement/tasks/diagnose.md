---
task: diagnose()
responsavel: "@movement-chief"
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
  - "[ ] Consulta analizada con intención y clasificación de fases" 
  - "[ ] Respuesta rápida proporcionada" 
  - "[ ] Ruta ejecutada o respuesta directa dada" 
---

# Task: Diagnose — Movement Squad

## Metadata

| Campo | Valor |
|---------------|----------------------------------------------------|
Silencioso ID de tareas `movement:diagnose`                                |
| Command       | `@movement diagnose "{query}"`                     |
| Orchestrator  | `movement-chief`                                   |
TEN Purpose TENPIR La solicitud del usuario, proporcionar una respuesta rápida y la ruta al mejor agente especialista TEN

## Inputs

| Entrada | Fuente | Requerido | Descripción |
|--------------|-------------|----------|------------------------------------------|
| `query` | Mensaje de usuario | Sí | La pregunta o petición del usuario |
| `context` | Sesión | No | Contexto de conversación anterior |
| `phase_hint` | User/Auto   Silencio No Silencio Fase de movimiento propuesta (1-5) Silencio

## Preconditions

- Configuración del escuadrón cargada (`config/config.yaml`)
- Catálogo de enrutamiento disponible (`data/routing-catalog.yaml`)
- Existe al menos una definición de agente especialista en `agents/`

## Phases

### Fase 1: Parse (movement-chief)

1. Lea la consulta del usuario y extraiga:
   - **Intención**: Lo que el usuario quiere lograr
   - **Palabras clave del dominio**: coincidencia con las palabras clave del catálogo de enrutamiento
   - **Fase de movimiento**: Mapa a una de las 5 fases (Spark, Identity, Ignition, Growth, Impact)
   - **Complejidad**: Simple (respuesta directa) vs Complejo (necesita especialista)

2. Clasifique el tipo de consulta:
   - `question` — Necesita una respuesta informativa
   - `creation` - Necesita un libre (manifiesto, marco de identidad, etc.)
   - `analysis` — Necesidades de análisis profundo (fenómeno, medición de impacto)
   - `strategy` - Necesita un plan o una hoja de ruta

### Fase 2: Enrutamiento del partido

1. Load `data/routing-catalog.yaml`
2. Califique cada dominio según las palabras clave extraídas
3. Identify:
   - **Agente principal**: mejor coincidencia (mayor superposición de palabras clave)
   - **Agente secundario**: Backup o perspectiva complementaria
   - **Nivel de confianza**: ALTO (>= 3 coincidencias de palabras clave), MEDIO (2 coincidencias), BAJO (0-1 coincidencias)

4. Cartografía de la fase de movimiento:
   Silencio Fase Silencio Agente Primario Silencioso Agente Secundario
   |--------------------|------------------------|-----------------------|
    movement-architect    |
   
    estrategista-de-ciclo |
   | Growth             | estrategista-de-ciclo  | analista-de-impacto   |
   | Impact             | analista-de-impacto    | movement-chief        |

### Fase 3: Respuesta

1. **Proporcione siempre primero una respuesta rápida**: de 2 a 4 oraciones que aborden directamente la consulta
2. Include:
   - Respuesta directa a la cuestión
   - ¿Qué fase de movimiento se relaciona con
   - Lo que el especialista recomendado añadiría

### Fase 4: Ruta (si es necesario)

1. Si la confianza es ALTA o MEDIA:
   - Anunciar al objetivo de la ruta: "Routing to @{agent} para un análisis más profundo"
   - Contexto de paso: consulta original + intención parisada + clasificación de fase
2. Si la confianza es BAJA:
   - NO enrutéis — responda directamente como movement-chief
   - Ofrezca al usuario una selección de especialistas si la consulta es ambigua

## Formato de salida

```yaml
diagnosis:
  query_summary: "{resumen de 1 línea}" 
  intent: "{pregunta sobre la tortura perpetuaanalysis sometidastrategy}" 
  movement_phase: "{Spark, la vida eterna, la vida eterna, la vida, la muerte, la muerte, la muerte, la muerte, la muerte, la muerte, la muerte, la muerte, la muerte, la muerte, la muerte, la muerte, la muerte, la muerte, la muerte, la muerte, la muerte, la muerte, la muerte, la muerte, la muerte, la muerte, la muerte, la muerte, la muerte, la muerte." 
  quick_answer: "{respuesta directa de 2 a 4 oraciones}"
  routing:
    confidence: "{ALTO|MEDIO|BAJO}" 
    primary_agent: "{agent-id}"
    secondary_agent: "{agent-id}"
    reason: "¿Por qué este agente es el mejor partido?" 
  routed: {true|false}
```

## Reglas de veto

1. **NUNCA enrute sin proporcionar primero una respuesta rápida**: el usuario siempre debe obtener valor inmediato
2. **NUNCA realice rutas con BAJA confianza**: responda directamente y ofrezca opciones en su lugar
3. **Nunca ruta a más de un agente simultáneamente** — Elija el mejor partido
4. **Nunca saltar clasificación de fase** — Cada mapa de consulta a una fase de movimiento
5. **Nunca inventar fases de movimiento** — Sólo use las 5 fases definidas

## Criterios de finalización

- [ ] Query se ha analizado con la clasificación de la intención y la fase
- [ ] Catálogo de enrutamiento consultado y puntuación de confianza
- [ ] Se proporciona respuesta rápida (obligatoria, independientemente de la ruta)
- [ ] Ruta ejecutada si confianza >= MEDIA, o respuesta directa si BAJA
- [ ] El formato de salida coincide con el esquema anterior
