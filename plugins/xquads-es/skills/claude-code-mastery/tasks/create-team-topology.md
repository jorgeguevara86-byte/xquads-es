# Task: Configuración del equipo del agente de diseño

** ID de la lista:** create-team-topology
**Version:** 1.0
**Purpose:** Diseñar y configurar un multi-agent equipo con topología definida, roles y patrones de comunicación
**Orquestador:**swarm-orchestrator (Nexus)
**Modelo:** Interactivo (elicito: verdadero)
** Estándar de calidad:** dry-run, todos los agentes cargan con éxito

---

## Overview

Esta tarea diseña una configuración del Equipo de Agentes donde múltiples subagentes colaboran en una carga de trabajo. Cubre la selección de topología, definición de roles, patrones de comunicación y estrategias de aislamiento.

```
INPUT (workload_description + team_size + isolation_needs)
    |
[FAPACIDAD 1: DECOMPOSICIÓN DE LA TRABAJO]
    - &quot; Analizar la carga de trabajo de las unidades paralelisibles &quot;
    - identificar requisitos estatales compartidos
    - necesidades de coordinación de términos
    |
[FAPACIDAD 2: DEFINICIÓN ROL]
    - Definir la responsabilidad de cada agente
    - Modelos de asignación por función
    - Establecer permisos de herramienta por agente
    |
[FAPACIDAD 3: CREACIÓN DE PALABRAS]
    - Crear .claude/agents/{name}.md para cada miembro
    - Configurar la primera máquina (nombre, modelo, herramientas)
    - Escribe role-specific instrucciones
    |
[FAPACIDAD 4: TOPOLOGY DESIGN]
    - patrón de topología selecta
    - Confidencialidad de flujo de comunicación
    - Set max_turns por agente
    |
[FAPOS 5: PATTERNS DE COMUNICACIÓN]
    - Definir protocolo de despido entre agentes
    - Establecer contexto compartido (films, directorios)
    - Configurar criterios de terminación
    |
[FILSO 6: COMPLETION CRITERIA]
    - Definir lo que "hace" significa para cada agente
    - Confía en lo que "hace" significa para el equipo
    - agregación de la producción de planes
    |
OUTPUT: Archivos de equipo de agentes + diagrama de topología + espectro de comunicación
```

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
| workload_description TENEDA TENIDO TENIDO Usuario TENIDO sí TENIDO Descripción clara de la tarea completa TENIDO
| team_size TENN NÚMERO TENIDO Usuario o auto TEN NO ANTERIENTE Número sugerido de agentes (por defecto: auto-detect) |
| isolation_mode Silencio enum Silencio Usuario Silencio no Silencio compartido (default) / worktree / none Silencio
| topology_preference Silencio en el futuro Silencioso usuario Silencio no Silencio hub-spoke / tubería / pares / auto TEN
| max_budget TENEDA TENIDO TENIDO Usuario TENIDO NO TENIDO Cost limitt (por ejemplo, "Mantenlo barato") TENIDO

---

## Preconditions

1. `.claude/agents/` directorio existe
2. El volumen de trabajo está claramente definido y abarcado
3. Al menos 2 subtásitos distintos identificados en el volumen de trabajo

---

## Phase 1: Workload Decomposition

** Objetivo:** agent-sized unidades.

### Steps

1.1 Analizar la descripción del volumen de trabajo para las distintas preocupaciones separables.
1.2. Identificar qué subtarea puede funcionar en paralelo vs secuencialmente.
1.3. Recursos compartidos en mapas (archivos, bases de datos, API) en subtaces.
1.4 Determinar el tamaño mínimo del equipo sobre la base de preocupaciones distintas.

#### Lista de verificación de descomposición

Cada subtarea tiene una sola responsabilidad clara.
- [ ] Se identifican las dependencias entre subtaces
- [ ] Los conflictos estatales compartidos se documentan
- [ ] Las oportunidades de paralización están marcadas

---

## Phase 2: Role Definition

** Objetivo:** Asignar funciones claras a cada agente.

### Steps

2.1. Para cada subtarea, definir un papel de agente:

```yaml
roles:
  - name: "{role-name}"
    responsibility: "¿Qué hace este agente?" 
    inputs: "Lo que recibe" 
    outputs: "Lo que produce" 
    model: "{opus turbasonnet turbaiku}" 
    tools: ["{tool1}", "{tool2}"]
```

2.2. Modelos de asignación basados en la complejidad de las tareas:
   - Coordinator/orchestrator: soneto (necesita juicio, no análisis profundo)
   - Análisis complejo: opus (arquitectura, revisión de seguridad)
   - Generación de código: soneto (ejecución estándar)
   - Tareas simples: haiku (formatamiento, extracción de datos)

2.3. No se verifica que dos agentes tengan responsabilidades superpuestas.

---

## Fase 3: Creación de Archivos de Agente

** Objetivo:** Crear los archivos de definición de agente.

### Steps

3.1. Para cada función de la fase 2, crear `.claude/agents/{role-name}.md`.
3.2. Use el create-agent-definition formato de tarea para cada archivo.
3.3. Incluido team-specific instrucciones en cada agente:
   - ¿Qué otros agentes existen en el equipo?
   - Dónde escribir salidas ( directorio compartido)
   - Cómo señalizar la terminación

---

## Phase 4: Topology Design

** Objetivo:** Seleccione la topología correcta para la interacción con el agente.

### Topology Compararison

Silencio Topología Silencio Estructura Silencio Mejor Para Silencio Coordinación Costo Silencio
|----------|-----------|----------|-------------------|
Silencio **Hub-and-Spoke** Silencio Un coordinador envía a especialistas ← Tareas mixtas, variada complejidad TEN Medium TEN
Silencio **Pipeline** Silencio Agente Una salida alimenta Agente B introduccion Silencio Proceso secuencial, transformación de datos Silencio Bajo Silencio
Silencio **Peer** Silencio Todos los agentes trabajan independientemente, fusionarse al final Silencio tareas indefensos
Silencio **Herario** Silencioso Coordinadores multinivel con sub-teams Silencio Proyectos complejos grandes Silencio

#### Decisión de selección

```
¿Son los subtasecos independientes sin estado compartido?
  Sí - superiorología de Peer
  NO - ¿Los subtaces forman una cadena secuencial?
    Sí - título topología Pipeline
    NO - ¿Hay un "cerebro" especialistas en coordinación?
      Sí - Universidad de Hub-y-Spoke topology
      NO - ES TERIORÍA Hierarchical topology
```

4.1. Seleccione topología basada en el análisis de descomposición.
4.2. Documentar la topología con un diagrama ASCII.
4.3. Conjunto `max_turns` guía por agente:
   - Tareas simples: 5-10 vueltas
   - Tareas estándar: 15-25 vueltas
   - Complejo de tareas: 30-50 vueltas

---

## Fase 5: Patrones de Comunicación

** Objetivo:** Defina cómo los agentes comparten información.

#### Communication Strategies

Silencio , Estrategia , Mecanismo , , , , , . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
|----------|-----------|----------------|
Silencio **Con base en el archivo** Silencio Agents escribe al directorio compartido Silencio Low (same repo) Silencio
Silencio **Worktree** Silencio Cada agente tiene su propio git worktree TEN High (separate working trees) TEN
Silencio **Branch** Silencio Los agentes trabajan en ramas separadas ¦ Medium (same repo, diferentes ramas) Silencio

### Steps

5.1. Defina un directorio de salida compartido (por ejemplo, `.claude/team-output/{task-id}/`).
5.2. Definir el formato de desvío (cómo un agente indica la terminación):
   - Escribe un `{agent-name}-done.md` archivo con sumario y productos
   - O escribir a un compartido `progress.yaml` archivo
5.3 Definir la resolución de conflictos si los agentes pueden modificar los mismos archivos:
   - Usar aislamiento de árbol de trabajo high-risk escenarios
   - Uso file-level propiedad medium-risk
   - Uso merge-at-end para low-risk

---

## Phase 6: Completion Criteria

** Objetivo:** Defina lo que significa "hacer".

### Steps

6.1. Para cada agente, definir la terminación como:
   - Archivos de salida escritos
   - Control de calidad aprobado (insignia, prueba, etc.)
   - Señal de terminación enviado

6.2. Para el equipo, definir la terminación como:
   - Todos los agentes reportan hechos
   - Productos agregados
   - Examen de integración aprobado (si es aplicable)

6.3. Definir el manejo de fallas:
   - El agente falla - título reingreso una vez, luego escalar a coordinador
   - El coordinador falla - título escalate a humano
   - Timeout - Agente de matar a título personal, reporte resultados parciales

---

## Formato de salida

```yaml
team_topology_result:
  topology: "{hub-spokeTENPIPELÓSTPOS ANTERIJERO TERRITORIOS" 
  agents:
    - name: "{agent-1}"
      file: ".claude/agents/{agent-1}.md"
      model: "sonnet-4"
      role: "{responsibility}"
    - name: "{agent-2}"
      file: ".claude/agents/{agent-2}.md"
      model: "haiku-4"
      role: "{responsibility}"
  communication:
    strategy: "{file-basedSilencioso, silencio." 
    shared_dir: ".claude/team-output/{task-id}/"
    handoff_format: "completion-file"
  completion:
    all_agents_done: true
    outputs_aggregated: true
  diagram: "[Coordinador]\n    |\n+---+---+\n|       |\n[A1] [A2]"
```

---

## Condiciones de veto

Silencio Silencio Silencio Silencio Silencio Silencio
|-----------|--------|
tención La carga de trabajo no puede ser descompuesta en 2+ subtásicos distintos TEN-
tención El tamaño del equipo excede a 6 agentes TEN HALT - descomposición en sub-teams primera tención
Silencio Todos los agentes necesitan tener acceso a los mismos archivos TEN HALT -- rediseñado con propiedad de archivos o aislamiento de worktree TEN
Silencio No hay criterios de terminación definidos Наниваний -- definir "do" antes de crear equipo удены
tención Los costos modelo exceden la limitación presupuestaria establecida TEN- modelos de baja o reducen el tamaño del equipo TEN
