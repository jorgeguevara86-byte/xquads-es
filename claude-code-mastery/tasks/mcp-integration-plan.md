# Task: Plan MCP Server Integration

** ID de la lista:** CCM-PI-005
**Version:** 1.0.0
**Command:** `*mcp-integration-plan`
**Agente:**Conduit (project-integrator)
**Purpose:** Planificar la integración del servidor MCP para un proyecto analizando necesidades, mapeando capacidades a servidores disponibles, estimando el impacto presupuestario contextual y priorizando por ROI.

---

## Overview

```
  Análisis de proyectos
       |
       v
  +---------------------+
  Silencio 1. Proyecto de análisis
  |    Needs             |
  +---------------------+
       |
       v
  +---------------------+
  Silencio 2. Capacidades del mapa
  Silencio para los PCM disponibles
  +---------------------+
       |
       v
  +---------------------+
  3. Contexto estimado
  Silenciosos en el presupuesto
  +---------------------+
       |
       v
  +---------------------+
  Silencio 4. Prioridad por ROI TEN
  +---------------------+
       |
       v
  +---------------------+
  Ø 5. Crear integración
  |    Plan              |
  +---------------------+
```

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
| project_path Silencio Silencio Silencio Usuario o cwd Silencio Sí Silencio Valid directorio de proyectos Silencio
Silencioso presupuesto Silencio en el futuro Usuario Silencio No Silencio `minimal` (1-2 MCPs), `standard` (3-5), `full` (sin límite) Silencio
Silenciosidad de prioridades Silencio string[] Silencio Usuario Silencio No TENIDO E.g., ["documentación", "búsqueda de laboratorio", "database", "prueba de navegador"] TENCIÓN

---

## Preconditions

- Directorio de proyectos accesible para análisis
- Comprensión del ecosistema disponible de PCM (oficial + comunidad)

---

## Fases de Ejecución

### Fase 1: Analizar las necesidades del proyecto

Examinar el proyecto para identificar dónde los servidores MCP añadirían valor:

1. **Apilación de tecnología**: qué marcos, idiomas, bases de datos se utilizan
2. **Con dependencia externa**: API consumidas, servicios integrados
3. ** Flujo de trabajo de desarrollo**: qué tareas repiten los desarrolladores con frecuencia
4. ** Necesidades de documentación**: las bibliotecas carecen de buenos documentos en línea
5. **Las necesidades de información**: pruebas del navegador, pruebas de API, escenarios E2E
6. **Necesita datos**: búsqueda web, raspado, tareas de investigación

Producir una matriz de necesidades:

← Necesidad de la categoría Silencio Necesitar una respuesta específica
|---------------|---------------|-----------|-----------------|
Silencio Documentación Silencio React docs lookup Silencio Daily Silencio Búsqueda manual del navegador Silencio
← Base de datos ← Ejecución de consultas Silencio Hora ← Copiar paso a psql Silencio
Silencio Buscar Silencio Buscar ejemplos de código Silencio Daily Silencio Manual Google search ←

### Fase 2: Capacidades de mapa para PCs disponibles

Necesidades identificadas de coincidencia para servidores MCP disponibles:

**Official/Stable MCPs:**
Silencio MCP Server Silencioso Capacidades Silencio transporte Silencioso
|------------|-------------|-----------|----------|
Silencio contexto7 Silencio documentación de la biblioteca Silencio stdio Silencio Framework/library docs ←
Silencios vivir la automatización del navegador ← stdio ← Pruebas web, capturas de pantalla ←
| postgres/supabase Silenciosos consultas de la base de datos Silencio Silencio Silencio
Silencio sistema de archivos Silencio Operaciones de archivo Silencio stdio Silencio acceso a la guía

**PRM de la comunidad:**
← MCP Server Silencioso Capacidades Silencio Maturity ← Mejor para Silencio
|------------|-------------|----------|----------|
Silencio exa Silencio Búsqueda en la Web Silenciosos Silenciosos Silenciosos
Silencioso apify Silencio Web scraping Silencio Estable Silencio
Silencio Silencio Silencio Silencio Silencio Silencio Silencio Issue/PR , gestión y gestión
| linear/jira Silencio Silencio Administrar proyectos Silenciosos Silenciosos

Para cada necesidad, lista de candidatos MCPs con puntuación de ajuste (1-5).

## Fase 3: Efecto del presupuesto de la estimación

Cada servidor MCP tiene un costo de contexto.

1. ** Costo de registro de la herramienta**: número de herramientas expuestas, descripción de cuenta de ficha
2. ** Costo por habitante**: promedio input/output tamaño de las llamadas de herramientas
3. **Iniciar latencia**: tiempo para inicializar el servidor
4. ** Pieza de memoria**: recursos consumidos mientras se ejecuta

Cálculo del presupuesto contextual:
```
Total context overhead = sum(s)tools_per_mcp * avg_description_tokens)
% de la ventana contextual de 200K utilizada por las inscripciones de MCP
```

**Directrices de los proyectos:**
Silencioso Presupuesto Nivel Silencio Max MCP Overhead Silencio Max Servers ←
|-------------|-----------------|-------------|

tención Estándar TENIDO ANTERIED 5% context window TENIDO 3-5 servidores TEN
Silencio Full TENIDO ANTERIED 10 % context window TENIDO No hard limit TEN 

Bandera cualquier MCP que registre más de 20 herramientas (context-heavy).

### Fase 4: Prioridad por ROI

Puntuación de cada candidato MCP:

```
ROI = (frequency_of_need * time_saved_per_use) / (context_cost + setup_effort)
```

Where:
- **frequency_of_need**: diario=5, semanal=3, mensual=1
- **time_saved_per_use**: minutos guardados vs manual acercamiento
- **context_cost**: token overhead (normalized 1-5)
- **setup_effort**: dificultad de configuración (1=trivial, 5=complejo)

Arranca a todos los candidatos por puntuación de ROI descendiendo.

## Fase 5: Crear Plan de Integración

Producir el plan final con la puesta en marcha gradual:

**Phase A (Día 1)**: MCP ROI más alta, configuración cero o mínima
**Phase B (Week 1)**: MCPs de ROI medio, configuración moderada requerida
**Phase C (Como se necesita)**: MCPs ROI más bajos, añadir cuando surge la necesidad específica

Para cada MCP en el plan:
1. Simpeto de configuración para settings.json
2. Variables o credenciales del entorno requerido
3. Comando de verificación para probar conectividad
4. Impacto previsto en el presupuesto por contexto

---

## Formato de salida

```markdown
## MCP Integration Plan

**Project:** {project_path}
**Budget:** {budget_level}
**Date:** {YYYY-MM-DD}

### Needs Analysis

| Need | Frequency | Matched MCP | ROI Score |
|------|-----------|-------------|-----------|
| {need} | {freq} | {mcp} | {score} |

### Context Budget

| MCP Server | Tools | Est. Tokens | % Window |
|------------|-------|-------------|----------|
| {mcp} | {N} | {N} | {N}% |
| **Total** | | | {N}% |

### Rollout Plan

#### Phase A: Immediate (Day 1)
1. **{mcp_name}**: {reason}
   - ROI: {score}
   - Config:
     ```json
     { "mcpServers": { "{name}": { ... } } }
     ```
   - Verify: {command}

#### Fase B: A corto plazo (ocio 1)
1. **{mcp_name}**: {reason}

#### Phase C: On-demand
1. **{mcp_name}**: {reason}

### Excluded MCPs

TENCIÓN MCP TENIDO Razón para la exclusión TEN
|-----|---------------------|
| {mcp} | {reason} |
```

---

## Condiciones de veto

**NO** recomendar MCPs que requieran credenciales que el usuario no haya acordado proporcionar
** NUNCA** supera el nivel presupuestario establecido sin la aprobación explícita del usuario
- **NO** recomendar MCP experimentales o abandonados sin un riesgo de madurez insignia
** NUNCA** instalar o configurar MCP en esta tarea: esta tarea produce un plan solamente

---

## Criterios de finalización

- [ ] Necesidades de proyecto analizadas con evaluación de frecuencias
- [ ] MCPs disponibles mapeados para necesidades identificadas
- [ ] Presupuesto de contexto estimado para cada candidato
- [ ] ROI puntuaciones calculadas y clasificadas
- [ ] Plan de integración gradual creado con los snippets de configuración
- [ ] Cumplir el presupuesto verificado
- Plan entregado en formato estándar
