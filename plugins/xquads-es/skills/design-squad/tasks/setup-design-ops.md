---
task: setupDesignOps()
responsavel: "@dave-malouf"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: team_context
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: current_pain_points
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: designOpsPractice
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Estado actual evaluado con cuellos de botella identificados" 
  - "[ ] flujo de trabajo de diseño definido con etapas, actividades y puertas" 
  - "[ ] Metrices definidas para el seguimiento de la salud en curso" 
---

# Task: DesignOps Practice Setup

** ID de usuario: ** DESIGN-003
**Version:** 1.0.0
**Command:** `*setup-design-ops`
Dave Malouf (en inglés)dave-malouf)
**Purpose:** Establecer una práctica DesignOps para escalar la calidad del diseño y la eficacia del equipo.

---

## Inputs

| Entrada | Fuente | Requerido |
|-------|--------|----------|
| `team_context` ← Diseño tamaño del equipo, estructura, madurez TENIDO TENIDO
| `current_pain_points` ← Los mayores desafíos operacionales Silencio Silencio
| `tools_in_use` Silencio Herramientas de diseño y colaboración actuales Silencio
| `engineering_workflow` ← Cómo funciona el equipo dev (agile, kanban, etc.) TENIDO TERRENO
| `budget_constraints` Silencio Presupuesto disponible tools/hires Silencio

## Preconditions

1. El equipo de diseño existe (aunque sea pequeño)
2. Se identifican y reconocen los puntos de dolor
3. Liderazgo buy-in para mejorar las operaciones de diseño

## Fases de Ejecución

## Fase 1: Evaluar el estado actual

1. Mapa del flujo de trabajo de diseño actual de producto breve a envío
2. Identificar los cuellos de botella — ¿dónde se atasca o retrasa el trabajo?
3. Evaluar el paisaje de herramientas - ¿son herramientas consistentes? ¿Rodundant? ¿Perdiendo?
4. Evaluar la calidad de la entrega de mano — ¿qué tan bien traducen los diseños al código?
5. Revisión de la reunión y la estructura de la ceremonia - ¿Están ocurriendo revisiones de diseño?
6. Evaluar las prácticas de documentación del diseño - ¿Se captan los conocimientos institucionales?
7. Interview/survey el equipo - ¿qué más necesitan?

### Fase 2: Diseño de flujo de trabajo

1. Definir las etapas de flujo de trabajo del diseño:
   *Descubre** — Investigación, información de los usuarios, configuración de problemas
   **Definir** - Requisitos, limitaciones, criterios de éxito
   **Diseño**: Exploración, iteración, refinamiento
   **Deliver** — Handoff, QA, implementation support
   * Medida**: análisis posterior al lanzamiento, planificación de la iteración
2. Para cada etapa, definir:
   - Entradas requeridas (lo que debe existir antes de comenzar)
   - Actividades (lo que ocurre durante esta etapa)
   - Productos producidos (lo que debe existir antes de avanzar)
   - Revise las puertas (que revisan y qué criterios)
3. Mapear el flujo de trabajo al proceso de ingeniería - ¿dónde se intersectan?
4. Definir la cadencia de diseño sprint - ¿cuánto tiempo es un ciclo de diseño?
5. Establecer ritos críticos y de revisión:
   - Crítica de diseño (semana, compañeros)
   - Examen del diseño (por hito, partes interesadas)
   - Diseño QA (pre-ship, diseñador + ingeniero)

### Fase 3: Define People Ops

1. **Definiciones completas** — Establece expectativas claras para cada función de diseño
   - Diseñador UX, Diseñador UI, Ingeniero de Sistemas de Diseño, Investigador UX, Líder de Diseño
2. **Marco de carrera** — Sendas de crecimiento para los diseñadores
   - IC track: Junior → Medio → Senior → Staff → Principal
   - Track: Lead → Manager → Director → VP
3. ** Matriz de matar** - Competencias previstas en cada nivel
4. **A bordo** — Cómo los nuevos diseñadores se levantan para acelerar
   - Guía de configuración de herramientas
   - Introducción del sistema de diseño
   - Normas y rituales de equipo
   - Primera semana, first-month hitos
5. ** Gestión de conocimientos** - Cómo se documentan las decisiones y la justificación de diseño
   - Registros de decisiones para las principales opciones de diseño
   - Documentación para soluciones reutilizables
   - Repositorio de investigación para las ideas de los usuarios

### Fase 4: Implementar herramientas e infraestructura

1. ** Herramientas de diseño** — Normalizar en una herramienta de diseño primario (Figma recomendado)
   - Organización de archivos y convenciones de nombres
   - Estructura de la biblioteca para componentes compartidos
   - Prácticas de control de versiones
2. ** Herramientas de colaboración** — Cómo las acciones de diseño funcionan con ingeniería y producto
   - Ejecuciones de diseño y herramienta de desvío
   - Plataforma de documentación de componentes
   - Herramientas de retroalimentación y anotación
3. ** Herramientas de búsqueda** — Pruebas de usuario, análisis, recopilación de comentarios
4. ** Gestión de activos** — biblioteca de iconos, sistema de ilustración, activos de marca
5. **Metrics Dashboard** — Track design ops health:
   - Hora del ciclo (refugio a envío)
   - Tasa de trabajo (cuántas veces los diseños cambian después de la entrega)
   - Tasa de adopción del sistema de diseño
   - Marcas de satisfacción del equipo
   - Tasa de cumplimiento de la accesibilidad

## Formato de salida

```yaml
design_ops:
  architect: "dave-malouf"
  team_size: 0
  maturity_level: "Ad Hoc ← Emergentes Silencio Definido Silencio Managed ← Optimizado" 
  workflow:
    stages: [discover, define, design, deliver, measure]
    sprint_cadence: "{duration}"
    rituals:
      - name: "{ritual}"
        frequency: "{cadence}"
        participants: ["{roles}"]
  people_ops:
    roles_defined: ["{RÍNDICE}" ]
    career_framework: true
    onboarding_plan: true
    knowledge_management: "{approach}"
  tools:
    design: "{herramienta primaria}" 
    collaboration: "{tool}"
    research: "{tool}"
    asset_management: "{tool}"
  metrics:
    cycle_time: "{target}"
    rework_rate: "{target}"
    system_adoption: "{target}"
    team_satisfaction: "{target}"
  implementation_plan:
    week_1_2: ["{Inmediata configuración}" ]
    month_1: ["{foundation}"]
    month_3: ["{optimization}"]
```

## Condiciones de veto

- ** NUNCA** introducir herramientas sin definir primero el flujo de trabajo - las herramientas sirven proceso, no el revés
- **Nunca** saltar las operaciones de la gente - las operaciones de diseño fallan sin papeles claros y trayectorias de carrera
- **Nunca** copiar las operaciones de diseño de otra empresa al por mayor - adaptarse a la madurez de su equipo
* * * NUNCA* *continuará todo a la vez, la fase o el equipo estarán abrumados*
- ** NUNCA** construir operaciones de diseño en aislamiento de la ingeniería - debe integrar

## Criterios de finalización

- Estado actual evaluado con cuellos de botella identificados
- [ ] flujo de trabajo de diseño definido con etapas, actividades y puertas
- [ ] El flujo de trabajo mapeado al proceso de ingeniería
- [ ] Crítica y revisión rituales establecidos
- [ ] Definiciones de papel y marco de carrera creado
- [ ] Plan de embarque documentado
- [ ] pila de herramientas estandarizada con convenciones
- [ ] Metrices definidas para el seguimiento de la salud en curso
