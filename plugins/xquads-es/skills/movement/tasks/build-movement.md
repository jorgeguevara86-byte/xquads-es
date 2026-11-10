---
task: buildMovement()
responsavel: "@movement-chief"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: cause
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: audience
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: movement_build
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Análisis de chispa completado y validado" 
  - "[ ] Los 6 documentos entregables producidos" 
  - "Fin...to-end coherencia validada" 
---

# Task: Build Movement

**Task ID:** MOVEMENT-001
**Version:** 1.0.0
**Command:** `*build-movement`
**Agente:** Jefe de Movimiento (movement-chief)
**Purpose:** Orquestar el proceso completo de construcción de movimiento de 5 fases desde la chispa hasta el impacto

---

## Inputs

| Entrada | Fuente | Requerido | Descripción |
|-------|--------|----------|-------------|
| `cause` TENIDO TENIDO TENIDO TENIDO Sí TENIDO La causa, idea o marca para construir un movimiento alrededor de TEN
| `audience` Silencio invocar a un usuario Silencio Sí Silencio Público objetivo o descripción de la comunidad
| `context` Silencioso sesión Silencio No Silencio contexto de mercado, activos de marca existentes, competidores Silencio
| `phase_override` TENIDO Usuario TENIDO No TENIDO Comience desde una fase específica (esquema fases anteriores) TEN
| `intensity` Silencio Usuario Silencio No TENIDO Escala: bases, regionales, nacionales, globales TEN

## Preconditions

- Configuración del escuadrón cargada (`config/config.yaml`)
- Todos los agentes especializados disponibles: fenomenologo, identitario, manifestador, estrategista-de-ciclo, analista-de-impacto
- catálogo de rugidos cargados (`data/routing-catalog.yaml`)
- Marcos de movimiento cargados (`data/movement-frameworks.yaml`)

## Fases de Ejecución

### Fase 1: Spark (fenomenologo)

1. Identificar el **lived experiencia** que une al público objetivo
2. Mapa de la **collective tensión** - qué frustración, dolor o aspiración es compartida
3. Destapar el **shared narrativa** - ¿Qué historia se cuenta ya la gente
4. Articular el **movement chispa** - la visión cristalizada que ilue la acción
5. Validar la chispa contra el marco de análisis fenomenológico
6. Entrega `spark-analysis.md` con conclusiones

**Punto de comprobación:** movement-chief revisiones de la validez de la chispa antes de proceder

### Fase 2: Identidad (identitario)

1. Definir el **belief sistema** - creencias básicas que unen a los miembros
2. Diseño **tribal marcadores** - lenguaje, símbolos, identidad visual, rituales
3. Establezca el **Estadio de identidad**: valores  creencias √≠s √≠ comportamientos √≥ símbolos √≥ ritos de confianza
4. Crear **in-group señales** - cómo se reconocen los miembros
5. Definir el **out-group límite** - lo que el movimiento contradice
6. Entrega `identity-architecture.md` con el marco de identidad completo

**Punto de comprobación:** movement-chief valida la coherencia de identidad con chispa

## Phase 3: Ignition

1. Borrar el **manifesto** usando la anatomía de 7 componentes
2. Definir el **origin historia** - mitologie el momento de fundación
3. Crear el **battle c) Una sola frase que se moviliza
4. Diseño de la **first ritual** - la experiencia de entrada para nuevos miembros
5. Semilla el **founding círculo** - identificar y reclutar primero 10 creyentes
6. Entrega `manifesto.md` y `ignition-plan.md`

**Punto de comprobación:** movement-chief aprueba alineación manifiesta con identidad

### Fase 4: Crecimiento (estrategista-de-ciclo)

1. Diseño del **Frewheel de crecimiento**: Attract √® Activate √≥ Sustain √≥ Multiply
2. Plan **attraction canales** - dónde encontrar futuros creyentes
3. Crear **activation rituales** - cómo los recién llegados se convierten en miembros activos
4. Construir **sustain mecánica** - bucles de compromiso, cadencia de contenido, eventos
5. Diseño **multiplication dispara** - cómo los miembros reclutan nuevos miembros
6. Entrega `growth-strategy.md` con detalles de volante y cronología

**Punto de comprobación:** movement-chief valida la viabilidad del plan de crecimiento

## Fase 5: Impacto (analista-de-impacto)

1. Definir la pirámide **Impact** -- 5 niveles de conciencia a transformación
2. Conjunto **metrics indicadores cualitativos y cuantitativos
3. Diseño **community salud de panel** - compromiso, sentimiento, tasa de crecimiento
4. Calcular el índice **Vitality** - puntuación de salud compuesta
5. Crear **reporting cadencia** - pulso semanal, mensual deep-dive, examen trimestral
6. Entrega `impact-framework.md` con métricas y plan de medición

**Punto de comprobación:** movement-chief aprueba la integridad del marco de impacto

## Formato de salida

```yaml
movement_build:
  name: "{Nombre de movimiento}" 
  cause: "{causar sumario}" 
  spark: "{one-line chispa de la perspicacia" 
  identity:
    core_belief: "{confianza central}" 
    battle_cry: "{una frase}" 
    tribal_markers: ["{marker1}", "{marker2}", "{marker3}"]
  manifesto_status: "complete"
  growth_flywheel: "{attract √≠ activar √≥ mantener √≥n multiplicar}" 
  impact_metrics:
    vitality_index: "{score}/100"
    primary_kpi: "{metric}"
  deliverables:
    - spark-analysis.md
    - identity-architecture.md
    - manifesto.md
    - ignition-plan.md
    - growth-strategy.md
    - impact-framework.md
  status: "{completa para la vida eternain-progressSilencio." 
```

## Condiciones de veto

1. **Nunca saltar la fase Spark** - cada movimiento debe comenzar con una experiencia compartida genuina
2. **Nunca proceder a la identidad sin una chispa validada** - identidad construida sobre falsos colapsos locales
3. **Nunca escriba un manifiesto antes de definir la identidad** - manifiesta la identidad expresa, no lo cree
4. **Nunca el crecimiento de lanzamiento sin un manifiesto** - crecimiento sin mensaje es ruido
5. **Nunca mida el impacto sin métricas definidas** - la medición requiere un marco primero

## Criterios de finalización

- [ ] Análisis de chispa completado y validado por movement-chief
- [ ] Arquitectura de identidad definida con el Stack de identidad completo
Manifiesto escrito con los 7 componentes
- [ ] Volante de crecimiento diseñado con las 4 fases
- [ ] pirámide de impacto definida con métricas por nivel
- [ ] fórmula del índice de vitalidad establecida
[ ] Todos los 6 documentos disponibles producidos
- Fin...to-end coherencia validada (los hilos de parque hasta el impacto)
