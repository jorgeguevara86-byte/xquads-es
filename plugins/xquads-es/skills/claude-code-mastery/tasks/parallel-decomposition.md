# Task: Parallel Task Decomposition for Agent Execution

** ID de la lista:** parallel-decomposition
**Version:** 1.0
**Purpose:** Descomponer una tarea compleja en subtaces para paralelo multi-agent Ejecución
**Orquestador:**swarm-orchestrator (Nexus)
**Modelo:** Interactivo (elicito: verdadero)
**Estado de calidad:** Gráfico de dependencia validado, sin dependencias circulares, estrategia de fusión probada

---

## Overview

Esta tarea analiza una carga de trabajo, identifica subtaks independientes, diseña un plan de ejecución paralela y configura agentes para la ejecución simultánea.*maximum El paralelismo viene de minimizar las dependencias, no maximizando agentes**.

```
INPUT (INPUT)task_description + limitaciones)
    |
[FAPACIDAD 1: ANÁLISIS DE TASK]
    - Emplea la tarea en subtaces atómicos
    - clasificar la complejidad de cada subtarea
    - Estimar tiempo de ejecución por subtask
    |
[FAPOS 2: DEPENDENCIA QUE SE PUEDE]
    - identificar las dependencias de datos entre subtaces
    - Nombrar conflictos de recursos (same archivos, mismas APIs)
    - Gráfico de dependencia de Build
    |
[PLAN DE EJECUCIÓN]
    - Grupo de expertos subtase en olas
    - asignar agentes a cada onda
    - Configurar la ejecución de antecedentes vs
    |
[FAPACIDAD 4: CONFIGURACIÓN CONVENIDA]
    - Crear o seleccionar definiciones de agente
    - Establecer fichas modelo por complejidad de subtasca
    -Configurar permisos de herramientas
    |
[FAPÉS 5: MERGE STRATEGY]
    - Confeccionar cómo combinan los productos de agente
    - &quot; Manejar cambios conflictivos &quot;
    - Verificación de integración de planes
    |
[FAPÍTULO 6: MONITORIA]
    - Establecer seguimiento de progreso
    - Definir los umbrales de tiempo
    - Recuperación de fracaso del Plan
    |
OUTPUT: Plan de ejecución + gráfico de dependencia + configuración de agente + estrategia de fusión
```

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
| task_description TENEDA TENIDO TENIDO Usuario TENIDO sí TENIDO Descripción completa del trabajo para paralelizar TENIDO
| max_parallel_agents Silencio número Silencio Usuario o predeterminado Silencio no Silencio Máximo agentes simultáneos (default: 4) Silencio
| isolation_mode Silencio enum Silencio Usuario Silencio no Silencio compartido / worktree / branch (default: shared) Silencio
| time_constraint Silencio Silencio Silencio Silencio Silencio Silencio Silencio
| cost_constraint Silencio enum Silencio Usuario Silencio no Silencio bajo / medio / alto (selección de modelos de defectos) Silencio

---

## Preconditions

1. La tarea es lo suficientemente grande como para beneficiarse de la paralización (2+ subtás independientes)
2. El Código Claude está en funcionamiento con la herramienta del Agente disponible
3. Límites de tasa de API suficientes para llamadas de agentes paralelos
4. El repositorio de Git es limpio (sin cambios no comprometidos) si se utiliza el aislamiento del árbol de trabajo

---

## Phase 1: Task Analysis

** Objetivo:** Descomponer la tarea en las unidades de trabajo independientes más pequeñas.

### Steps

1.1. Lea la descripción completa de la tarea.
1.2. Identificar subtásicos atómicos: cada uno debe ser:
   - Completamente por un solo agente
   - Probables independientemente
   - Producir un artefacto de salida clara
1.3. Clasificar cada subtarea:

TENIBLE Complejidad TENED Líneas de Cambio TENIDO Modelo TENIDO Tiempo estimado TENIDO
|------------|----------------|-------|----------------|
Silencio Trivial Silencio ANTERIED 20 líneas ANTE Haiku ANTE 1-2 min ANTE
Silencio Simple Silencio 20-100 líneas Silencio sonnet Silencio 3-5 min Silencio
Silencio Silencio Silencio 100-500 líneas Silencio sonnet Silencio 5-15 min Silencio
Silencio complejo Silencio 500+ líneas Silencioso opus Silencio 15-30 min Silencio

1.4. Crear una tabla de inventario de subtascos:

```markdown
| ID | Subtask | Complexity | Est. Time | Dependencies |
|----|---------|-----------|-----------|--------------|
| S1 | ...     | simple    | 3 min     | none         |
| S2 | ...     | standard  | 10 min    | S1           |
```

---

## Phase 2: Dependency Mapping

** Objetivo:** Construir un gráfico de dependencia para identificar oportunidades de paralelización.

### Tipos de dependencia

Silencio Tipo Silencio Descripción Silencioso
|------|-------------|--------|
Silencio **Data** Silencio S2 necesita salida de S1 Silencio Debe secuenciar 
Silencio **Resource** Silencio S1 y S3 modifican el mismo archivo Silencio Debe secuenciar o aislar Silencio
Silencio **Semántic** Silencio S2 debe saber lo que S1 decidió Silencio Puede utilizar el archivo de contexto compartido Silencio
Silencio **None** Silencio S1 y S4 son completamente independientes Silencio Puede paralelizar Silencio

### Steps

2.1. Para cada par de subtascos, determinar el tipo de dependencia.
2.2. Construir un gráfico de dependencia:

```
Plantilla de la función:

S1 -----------------------------
  \                 ^
   \               /
S2 ---------

Leyenda: Arrow = "Debe completar antes"
Paralelo: {S1, S2} puede correr juntos
Secuencial: S3 espera a S1, S4 espera a S2
Join: S5 espera a S3 y S4
```

2.3. Detectar dependencias circulares (de ser encontradas).
2.4. Calcular el camino crítico (cadena secuencial más larga).

---

## Phase 3: Execution Plan

** Objetivo:** Grupo subtarea en ondas de ejecución paralelas.

### Patrones de paralelización

Silencio Pattern Silencio Descripción Silencioso Uso Cuando Silencio
|---------|-------------|----------|
| **Fan-Out/Fan-In** ← Dispatch N agentes, recoger todos los resultados Silencio Subtascos independientes con fusión compartida ←
Silencio **Pipeline** Silencio Agentes de cadena A - título B - confianza C TENCIÓN Transformación secuencial TENIDO
Silencio **Scatter-Gather** Silencioso Despacha la misma tarea a los agentes N, elegir el mejor TEN Necesita diversos enfoques para el mismo problema TENIDO
Silencio **Espera** Silencio Grupos de tareas paralelas con puntos de sincronización ← Dependencias mixtas ←

## Wave Planning

3.1. Subtitulares de asignación a olas basadas en el gráfico de dependencia:

```
1. [S1, S2] -- ninguna dependencia, ejecutar paralelo
Wave 2: [S3, S4] -- depende de Wave 1, corre paralelo
Wave 3: [S5] -- depende de la onda 2
```

3.2. Para cada onda, determinar el modo de ejecución:

Silencioso Silencioso Silencio Silencio Cuándo utilizar 
|------|-----------|-------------|
Silencio **Background** Silencioso herramienta de agente con bandera de fondo Silencio Fire-and-forget subtitulos ANTE
Silencio **Pasaje** Silencioso Agente Secuencial llamadas herramienta ← Necesita resultado antes del próximo paso Silencio
Silencio **Parque de paralelo** Silencio Múltiples llamadas en el mismo mensaje Silencio submarinos independientes, necesitan todos los resultados TENIDO

3.3. Documentar el calendario de ejecución:

```
Time ->
  [==S1========S3===========S5====================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================
  [====S2===========S4====]
```

---

## Fase 4: Configuración del agente

** Objetivo:** Crear o asignar agentes para cada subtarea.

### Steps

4.1. Para cada subtarea, decida:
   - ¿Uso la definición de agente existente? `.claude/agents/`)
   - ¿Crear nuevo agente? create-agent-definition tarea)
   - ¿Usa la herramienta genérica del agente con la inline?

4.2. Configurar el modelo por subtasco basado en la complejidad de la fase 1.
4.3. Establecer permisos de herramientas -- restringir al mínimo necesario:
   - Subtareas sólo lectura: agente de tipo Explorar
   - Modificación del código: Propósito general Write/Edit
   - Investigación: Explorar tipo con Bash para herramientas web

4.4. Conjunto `max_turns` por agente basado en la complejidad:
   - Trivial: 5 vueltas
   - Simple: 10 vueltas
   - Estándar: 20 vueltas
   - Complejo: 40 vueltas

---

## Phase 5: Merge Strategy

** Objetivo:** Definir cómo las salidas de agente paralelo se combinan en un resultado final.

#### Merge Strategies

Silencio Silencio Silencio Silencio Silencio Silencio Silencio Silencio
|----------|-------------|--------------|
Silencio **Piedad de propiedad** Silencio Cada agente posee archivos específicos ← Ninguno TENIDO
Silencio ** Propiedad de la dirección** Silencio Cada agente posee un directorio ← Ninguno TENIDO
Silencio **Git merge** Silencio Cada agente en una rama, fusionarse al final TEN ANTE ANTE ANTE ANTE TENIDO
Silencio **Revisión manual** Silencio Reseñas humanas y fusiones Silencio Bajo (pero lento) Silencio
Silencio **Merge automatizado** Silencio Script fusiona las salidas por convención TEN Low TEN

### Steps

5.1. Assign file/directory propiedad de cada agente.
5.2. Definir el proceso de fusión:
   - Recoger salidas de todos los agentes
   - Verificar no conflictos (samo archivo modificado por 2+ agentes)
   - Si existen conflictos, aplique la estrategia de resolución
   - Realizar pruebas de integración en el resultado fusionado
5.3. Si se utiliza el aislamiento de árbol de trabajo, planifique la secuencia de fusión de rama.

---

## Phase 6: Monitoring

** Objetivo:** Seguimiento de los avances y manejo de los fracasos.

### Steps

6.1. Definir los puestos de control de los progresos realizados:
   - Cada agente escribe el estado a un archivo de progreso compartido
   - La terminación de onda activa la próxima ola
6.2. Establecer umbrales de tiempo por subtasco (2 veces tiempo estimado).
6.3. Definir el manejo de fallas:
   - Tiempo de salida del agente: Matar e informar resultados parciales
   - Error del agente: Retrocede una vez con el mismo config
   - Fallo repetido: Escalar a la humanidad
6.4. Plan de reversión si la fusión falla:
   - Retírense pre-execution estado
   - Informe que subtástasis tuvo éxito vs falló

---

## Formato de salida

```yaml
parallel_decomposition_result:
  total_subtasks: 5
  total_waves: 3
  estimated_sequential_time: "35 min"
  estimated_parallel_time: "15 min"
  speedup: "2.3x"
  critical_path: ["S1", "S3", "S5"]
  waves:
    - wave: 1
      subtasks: ["S1", "S2"]
      mode: "parallel-foreground"
    - wave: 2
      subtasks: ["S3", "S4"]
      mode: "parallel-foreground"
    - wave: 3
      subtasks: ["S5"]
      mode: "foreground"
  merge_strategy: "file-ownership"
  agents_created: [...]
  dependency_graph: "S1 - título S3 - título S5\nS2 - título S4 - título S5"
```

---

## Condiciones de veto

Silencio Silencio Silencio Silencio Silencio Silencio
|-----------|--------|
TEN- TEN- TERIAL DE LA DECISIÓN Circular detectada en el gráfico TEN-
tención Todos los subtareas son dependientes secuencialmente TEN- no beneficio de paralelización, uso de un agente único TEN
Silencio Conteo Subtask excede 10 Silencio HALT - grupo en higher-level unidades primera latitud
TEN Múltiples agentes deben escribir al mismo archivo TEN HALT -- rediseñado con propiedad de archivos o worktree TEN
TENIDO El tiempo de trayectoria crítica excede el tiempo de restricción TEN WARN -- considerar la descomposición de los subtiscos de ruta crítica más TEN
TENIDO El costo estimado supera el presupuesto TEN HALT - modelos de baja o reducir el paralelismo TEN
