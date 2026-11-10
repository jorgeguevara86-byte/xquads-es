# Task: Git Worktree Isolation Strategy

** ID de la lista:** worktree-strategy
**Version:** 1.0
**Purpose:** Planifique y configure el aislamiento de git worktree para multi-agent escenarios de desarrollo
**Orquestador:**swarm-orchestrator (Nexus)
**Modelo:** Interactivo (elicito: verdadero)
**Calidad estándar:** Se prueba el ciclo de vida de Worktree end-to-end, limpieza verificada

---

## Overview

Esta tarea planea git worktree isolation para equipos de agentes donde múltiples agentes modifican código simultáneamente. Worktrees le dan a cada agente su propio directorio de trabajo y sucursal, eliminando conflictos de fusión durante la ejecución y postergando la integración a una fase de fusión controlada.

```
INPUT (agents_count + shared_files_risk + merge_strategy)
    |
[ASE 1: ASESORAMIENTO DE ISOLATION]
    - Valorar fusionar el riesgo de conflicto
    - Determinar si se necesita aislamiento de árbol de trabajo
    - identificar estrategias alternativas
    |
[FAPEL 2: BRANCH STRATEGY]
    - convención de designación de ramas de Define
    - selección de rama base Plan
    - Establecer protección de rama
    |
[FAPACIDAD 3: CONFIGURACIÓN DE TRABAJO]
    - Crear árboles de trabajo para cada agente
    - Configurar directorios de trabajo de agente
    -Verificar cada árbol de trabajo es funcional
    |
[FAPACIDAD 4: Administración de LIFECYCLE]
    - Confeccionar - Trabajar para confianza - Confeder - flujo de limpieza
    - Configurar los disparadores de limpieza automatizados
    - Plan stale worktree detection
    |
[FAPÉS 5: MERCÉ Y CLEANUP]
    - Define orden de fusión (dependency-aware)
    - Manole fusiona conflictos
    - excluir los árboles de trabajo después de la fusión exitosa
    |
OUTPUT: Worktree config + estrategia de rama + plan de ciclo de vida
```

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
| agent_count Silencio número Silencio De la topología del equipo Silencio sí Silencio Número de agentes que necesitan aislamiento TENIDO
| base_branch TENTER TENER MÁS DE AUTO Auto-detect o usuario TEN NO ANTERIENTE Branch para crear árboles de trabajo desde (por defecto: actual) TEN
| task_id Silencio Silencio Silencio Silencio usuario Silencio sí Silencio Identificador para esta sesión de trabajo paralela Silencio
| shared_files TENTER TERRITORIO TENIDO Análisis TEN NO ANTE Archivos que múltiples agentes podrían modificar TEN
| auto_cleanup TEN-BOLA TENIDO Usuario TENIDO NO TENIDO Remove worktrees after merge (default: true) TEN

---

## Preconditions

1. El repositorio de Git se inicializa y tiene al menos un commit
2. El árbol de trabajo actual es limpio (sin cambios no comprometidos)
3. `git worktree` comando is available (Git 2.5+)
4. Espacio de disco suficiente para copias N del directorio de trabajo

---

## Phase 1: Isolation Assessment

** Objetivo:** Determinar si el aislamiento de la pista de trabajo es realmente necesario.

### When to Use Worktrees vs Shared Repo

Silencios Silencio Silencio Silencio Silencio Silencio
|----------|----------|--------|
Silencio Agentes modifican diferentes archivos Silencio **Descanso compartido** Silencio No hay riesgo de conflicto, configuración más simple Silencio
Silencio Agentes modifican los mismos archivos Silencio **Worktree** Silencio Impides el tiempo de ejecución fusionar conflictos Silencio
TENIDO Oleoducto secuencial (A then B) TEN **Recuerdo compartido** TEN No simultáneo escribe TEN
Silencio Agentes paralelos con solapa de archivos Silencio **Worktree** Silencio Cada agente necesita estado limpio Silencio
TENIDO Único agente con long-running tarea ← **Shared repo** Silencio No hay necesidad de aislamiento
| CI/CD ejecución de prueba paralela ← _Worktree** TEN-Torpretes necesita ambientes independientes TEN

### Steps

1.1. Analizar las asignaciones de agentes de la topología del equipo.
1.2. Construir un file-ownership matriz:

```
         
---------|---------|---------|---------|
file1.ts
file2.ts Silencio Silencio Silencio W Silencio Silencio ANTERIED
file3.ts
```

1.3. Si algún archivo tiene múltiples entradas W (escribir) se recomienda el aislamiento de la pista de trabajo.
1.4. Si no hay conflictos, documente la decisión de utilizar reposo compartido y las fases restantes del SKIP.

---

## Phase 2: Branch Strategy

** Objetivo:** Defina cómo las ramas mapa a los agentes y los árboles de trabajo.

## Branch Naming Convention

```
{task-id}/{agent-name}

Examples:
  feature-auth/code-reviewer
  feature-auth/test-writer
  feature-auth/docs-updater
```

### Steps

2.1 Definir la rama base (donde las hojas de trabajo se ramifican de):
   - Usar rama actual para el trabajo de historia
   - Uso `main` para el trabajo de características independientes

2.2. Crear un plan de rama:

```yaml
branches:
  base: "feature/auth-system"
  worktree_branches:
    - name: "feature/auth-system/api-agent"
      agent: "api-agent"
      files_owned: ["src/api/**"]
    - name: "feature/auth-system/test-agent"
      agent: "test-agent"
      files_owned: ["tests/**"]
    - name: "feature/auth-system/docs-agent"
      agent: "docs-agent"
      files_owned: ["docs/**"]
```

2.3. Verificar que ninguna rama no tenga conflictos con las ramas existentes.

---

## Fase 3: Configuración de Worktree

** Objetivo:** Crear y configurar los árboles de trabajo para cada agente.

### Worktree Location

Los Worktrees se crean como directorios hermanos al repo principal:

```
proyecto/
project-wt-api-agent- ¿Qué? api-agent
project-wt-test-agent- ¿Qué? test-agent
project-wt-docs-agent- ¿Qué? docs-agent
```

### Steps

3.1. Para cada agente, cree un árbol de trabajo:

```bash
# Create branch and worktree together
git worktree add ../project-wt-{agent-name} -b {branch-name} {base-branch}
```

3.2. Verificar cada árbol de trabajo es funcional:

```bash
git worktree list
# Should show main + N worktrees
```

3.3. Configure cada agente para utilizar su directorio worktree como directorio de trabajo.
3.4 Instalar dependencias en cada árbol de trabajo si es necesario (por ejemplo, `npm install`).

---

## Phase 4: Lifecycle Management

** Objetivo:** Definir el texto completo create-work-merge-cleanup ciclo de vida.

### Lifecycle Flow

```
CREATE WORK MERGE CLEANUP
  |                     |                       |                    |
  Crear worktree - Trabaja con el agente - Confeccion Merge branch - Empuje worktree
  Crear rama en aislamiento a base Borrar rama
  Instalar deps Commites a ramas Conflictos resueltos Verificar limpio
  |                     |                       |                    |
  [Automatizado] [Agente-driven] [Orquestado] [Automated]
```

### Steps

4.1. Documentar el ciclo de vida para esta tarea específica:

```yaml
lifecycle:
  create:
    trigger: "Inicio de tareas" 
    steps: ["crear obra" , "crear rama" , "instalar desperdicio" ]
    estimated_time: "1-3 min"
  work:
    trigger: "Activación del agente" 
    duration: "Variable"
    monitoring: "Archivo de progreso en ubicación compartida" 
  merge:
    trigger: "Todos los agentes completan" 
    order: ["api-agent", "test-agent", "docs-agent"]
    conflict_resolution: "manual"
  cleanup:
    trigger: "Combinar completo + verificado" 
    steps: ["quitar el árbol de trabajo" , "Sustitución" ]
    auto: true
```

4.2. Definir la detección de árboles de madera de estuche:
   - Worktree sin compromiso en 24 horas = potencialmente establo
   - Árbol de trabajo deleted/merged rama = definitivamente escalón
4.3. Establecer el comando de limpieza:

```bash
# Remove a specific worktree
git worktree remove ../project-wt-{agent-name}

# Prune stale worktree references
git worktree prune
```

---

## Fase 5: Combinación y Limpieza

** Objetivo:** Intensificar con seguridad todo agente que trabaja de nuevo a la rama base.

#### Merge Order

5.1. Intensidad en el orden de dependencia (agentes cuyo trabajo depende de la fusión primero):

```
1. api-agent    (sin dependencia de otros agentes)
2. test-agent   (puede importarse de api-agent's code)
3. docs-agent   (documentos lo que api-agent + test-agent construidos)
```

5.2. Para cada fusión:

```bash
# Switch to base branch
git checkout {base-branch}

# Merge agent branch
git merge {agent-branch} --no-ff -m "merge: {agent-name} work for {task-id}"

# If conflict:
#   1. Identify conflicting files
#   2. Resolve manually or with orchestrator guidance
#   3. Commit resolution
```

5.3. Después de que todo se fusione completo:
   - Ejecute la suite de prueba completa en el resultado fusionado
   - Si fallan las pruebas, identifique qué fusión introdujo el fracaso
   - Arreglar o revertir según sea necesario

5.4. Cleanup:

```bash
# Remove all worktrees for this task
git worktree remove ../project-wt-api-agent
git worktree remove ../project-wt-test-agent
git worktree remove ../project-wt-docs-agent

# Delete merged branches
git branch -d feature/auth-system/api-agent
git branch -d feature/auth-system/test-agent
git branch -d feature/auth-system/docs-agent

# Prune any lingering references
git worktree prune
```

---

## Formato de salida

```yaml
worktree_strategy_result:
  isolation_needed: true
  reason: "2 agentes modifican archivos superpuestos en src/" 
  worktrees:
    - agent: "api-agent"
      path: "../project-wt-api-agent"
      branch: "feature/auth-system/api-agent"
      status: "created"
    - agent: "test-agent"
      path: "../project-wt-test-agent"
      branch: "feature/auth-system/test-agent"
      status: "created"
  merge_order: ["api-agent", "test-agent"]
  auto_cleanup: true
  lifecycle_documented: true
```

---

## Condiciones de veto

Silencio Silencio Silencio Silencio Silencio Silencio
|-----------|--------|
TENJE repositorio no tiene compromisos TEN- inicializar repo primera TEN
← Cambios no comprometidos en el árbol de trabajo TEN-comend -- comprometer o guardar antes de crear árboles de trabajo TEN
TENIDO espacio de disco insuficiente para N worktrees TEN- estima ~size de repo per worktree TEN
TENCIÓN DE LA VENTA DE LA VENTA DE LA VIDA AL HACER - Actualización de la git para soporte de la pista de trabajo
Silencio No se detectan conflictos de archivos entre agentes Silencio SKIP - use reposo compartido en lugar (simpler) Silencio
dura Worktree creaciones falla TEN HALT -- verifique los archivos de bloqueo de git y los espacios de trabajo existentes TEN
