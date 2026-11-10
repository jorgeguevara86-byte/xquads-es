# Task: Context Rot Audit

** ID de la lista:** context-rot-audit
**Version:** 1.0
**Purpose:** Audit CLAUDE.md, reglas, y auto-memory para el contexto establo, incorrecto o hinchado que degrada el rendimiento del Código Claude
**Orquestador:**project-integrator (Conduit)
**Mode:** Autonomotriz (elicitación: falsa)
**Estandar de calidad:** Marca de la rotación calculada, todas las referencias fijas identificadas, plan de rehabilitación generado

---

## Overview

Contexto de la podredumbre ocurre cuando CLAUDE.md, archivos de reglas, y auto-memory acumular instrucciones obsoletas, referencias a archivos borrados, patrones deprecatados y contenido hinchado. Esta auditoría detecta sistemáticamente la podredumbre y produce un plan de remediación.

```
INPUT (project_root)
    |
[FAPACIDAD 1: CLAUDE.MD SIZE AUDIT]
    - Conteo de línea de medición y tamaños de sección
    - bandera de más de 500 líneas
    - identificar secciones más grandes
    |
[FAPACIDAD 2: VALIDACIÓN DE REFERENCIA]
    -Consulte cada ruta de archivo referenciado en CLAUDE.md
    - usuario Compruebe cada ruta de archivo referenciado en reglas
    - Informe relativo missing/moved archivos
    |
[FAPACIDAD 3: INSTRUCCIÓN STALENESS]
    -Consulte para referencias de API obsoletas
    - Comprobación de paquetes deprecatados
    - Checan los patrones que entran en conflicto con el código actual
    |
[FAPACIDAD 4: RULES STRUCTURE AUDIT]
    -Verificar reglas coinciden con la estructura del directorio actual
    - &gt; Comprobar las reglas orfanatos (los caminos ya no existen)
    - patrones de trayectoria de la primera carta Validate
    |
[FAPOS 5: AUTO-MEMORY AUDIT]
    - Comprobación .claude/agent-memory/ para entradas de establo
    -Verify referenced files still exist
    - Comprobación de entradas contradictorias
    |
[FAPÍTULO 6: ROT SCORE AND REMEDIATION]
    - Calcular la puntuación general de la poda
    - Generar lista de fijación priorizada
    - Producir plan de rehabilitación
    |
OUTPUT: Marca de puntaje de punta + reporte de resultados + plan de rehabilitación
```

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
| project_root Silencioso cadena ← Auto-detect Silencio sí Silencio Valid directorio con .claude/o CLAUDE.md |
| fix_automatically Silencio booleano Silencio Usuario Silencio no Silencio auto-fix problemas simples (por defecto: falso) ←
TENEDEN VERBOSE TENIDO boolean ANTERIOR TENIDO NO TENED Mostrar todos los cheques incluyendo el paso (por defecto: falso) TEN

---

## Preconditions

1. El proyecto ha configurado el Código de Claude (Código de Claude)CLAUDE.md o .claude/ existe)
2. Repositorio de Git para el análisis de historia del cambio
3. Lea el acceso a todos los archivos de proyecto

---

## Phase 1: CLAUDE.md Auditoría de tamaño

** Objetivo: * Comprobar si CLAUDE.md ha crecido más allá del tamaño efectivo.

### Size Thresholds

TENEDA TENED ANTERIOR TENEDIDO TENIDO
|-------|--------|--------|
TENIDO ANTE 100 TENIDO Lean ANTE Optimal auto-memory |
Silencio 100-200 Silencio Normal Silencio bueno para la mayoría de proyectos Silencio
Silencio 200-500 Silencio Crecer Silencio Considerar dividirse en reglas Silencio
TEN 500+ TENIDO Bloated TEN Degrada el desempeño TENIDO

### Steps

1.1. Contar líneas totales en CLAUDE.md.
1.2. Medir el recuento de línea de cada sección.
1.3. Identificar las tres secciones más grandes.
1.4. Incorporar cualquier sección más de 50 líneas como candidato para la extracción a fichero de reglas.
1.5. Comprobar información duplicada en secciones.

## Findings Format

```yaml
size_audit:
  total_lines: 347
  status: "growing"
  largest_sections:
    - name: "Normas de código" 
      lines: 89
      recommendation: "Extracto .claude/rules/code-standards.md" 
    - name: "Referencia API" 
      lines: 67
      recommendation: "Extracto .claude/rules/api.md" 
  duplicates_found: 2
```

---

## Phase 2: Reference Validation

**El objetivo:** Verificar cada uno file/directory referenciado en los archivos de contexto realmente existe.

### Steps

2.1. Extraiga todas las rutas de archivo desde CLAUDE.md (mirar backtick-quoted caminos, bloques de código).
2.2. Extraiga todas las rutas de archivo desde `.claude/rules/*.md`.
2.3. Para cada camino, compruebe si existe en el proyecto:

```
Reference: `src/components/Button.tsx`
Estado: EXISTAS / MISSING / MOVED

Reference: `npm run test:e2e`
Estado: VALID (en package.json scripts) / INVALID
```

2.4. Revisar las referencias de comandos contra package.json scripts.
2.5. Informe de todas las referencias que faltan con correcciones sugeridas.

## Findings Format

```yaml
reference_audit:
  total_references: 45
  valid: 38
  missing: 5
  likely_moved: 2
  missing_details:
    - path: "src/lib/api-client.ts"
      referenced_in: "CLAUDE.md:42"
      suggestion: "El archivo fue renombrado a src/lib/http-client.ts" 
```

---

## Phase 3: Instruction Staleness

** Objetivo:** Detectar instrucciones obsoletas que podrían hacer que Claude hiciera lo incorrecto.

# Indicadores de la estabilidad

Silencio Silencio Silencioso Método de detección
|--------|-----------------|
TEN ANTE Paquete precatado TENSI Check if version in instructions differs from package.json |
TEN Old API patterns TEN Instrucciones mencionan patrones no encontrados en el código actual TEN
← scripts eliminados TENIDO Npm scripts no ya en package.json |
Silencio Antigua estructura de directorios Silencio Instrucciones de referencia caminos que fueron reestructurados Silencio
TEN Version-specific instructions TEN Instrucciones atadas a la versión anterior del marco TEN

### Steps

3.1. Referencia cruzada CLAUDE.md instrucciones con instrucciones actuales package.json:
   - ¿Se siguen instalando dependencias referenciadas?
   - ¿Los números de versión coinciden?
3.2. Compruebe si los patrones de código descritos en CLAUDE.md existen en la base de código:
   - Grep para el patrón en los archivos fuente
   - Si no se encuentra, la instrucción es un escalón
3.3. Comprobación tech-specific - ¿Qué?
   - Reactar los componentes de clase mencionados pero no existen
   - Rutas de importación antiguas referenciadas
   - Métodos de API precatados mencionados

## Findings Format

```yaml
staleness_audit:
  total_instructions_checked: 23
  current: 18
  stale: 4
  uncertain: 1
  stale_details:
    - instruction: "Use getServerSideProps para la búsqueda de datos" 
      location: "CLAUDE.md:78"
      issue: "Proyecto utiliza el router App con componentes del servidor" 
      fix: "Actualización para describir patrones de componentes del servidor" 
```

---

Fase 4: Auditoría de la estructura de las normas

** Objetivo:** Verificar los archivos de reglas coinciden con la estructura actual del proyecto.

### Steps

4.1. Lista de todos `.claude/rules/*.md` Archivos.
4.2. Para cada regla con path-based - ¿Qué?
   - Extraiga el `paths:` patrones
   - Verificar al menos un archivo coincide con el patrón de glob
   - Si no hay archivos coinciden, la regla está huérfana.

4.3. Comprobación de las normas que faltan:
   - ¿Hay directorios importantes sin reglas correspondientes?
   - Comparar la cobertura de reglas contra la estructura del proyecto

4.4. Comprobación de las normas contradictorias:
   - ¿Alguna regla da instrucciones contradictorias para los mismos caminos?

## Findings Format

```yaml
rules_audit:
  total_rules: 6
  active: 4
  orphaned: 1
  missing_coverage: 2
  orphaned_details:
    - file: ".claude/rules/graphql.md"
      paths_pattern: "src/graphql/**"
      issue: "No existe un directorio graphql (removido en la migración v2)" 
  missing_coverage:
    - directory: "src/middleware/"
      suggestion: "Crear middleware.md regla para los patrones de austeridad y validación" 
```

---

## Phase 5: Auto-Memory Audit

** Objetivo:** Revisar los archivos de memoria de agente para las entradas de establo.

### Steps

5.1. Escáner `.claude/agent-memory/` para todos los archivos de memoria.
5.2. Para cada archivo de memoria:
   - Compruebe si los archivos referenciados todavía existen
   - Compruebe si los patrones referenciados siguen siendo válidos
   - Comprobación de contradicciones con la corriente CLAUDE.md
5.3. Check MEMORY.md conteo de líneas (debe ser menor de 200 para auto-loading).
5.4. Identificar las entradas que se session-specific (no debería estar en memoria persistente).

---

## Fase 6: Puntaje de raíz y rehabilitación

** Objetivo:** Calcular la salud general y producir un plan de fijación.

### Rot Score Calculation

```
Puntaje de la raíz = (missing_refs * 3) + (stale_instructions * 5) + (orphaned_rules * 2) +
            (size_penalty) + (memory_issues * 2)

Pena de tamaño:
  Identificar 200 líneas: 0 puntos
  200-500 líneas: 5 puntos
  500+ líneas: 15 puntos

Interpretación de puntaje:
  0-5: Saludable (verde)
  6-15: Caída menor (amarillo) - limpieza de horarios
  16-30: Caída significativa (orange) - limpiar pronto
  31+: Cuadrícula crítica (rojo) - limpiar ahora
```

### Plan de Remediación

6.1. Generar lista de fijación prioritaria:

Silencio Silencio Silencio Silencio Silencio Silencio Silencio Silencio Silencio
|----------|-----|--------|--------|
Silencio P0 Silencio Eliminar referencias a archivos borrados Silencio Bajo Silencio
Silencio P1 Silencio Actualizar instrucciones de establo Silencio Medium Silencio
Silencio P2 Silencio Retirar las reglas orfanatos Silencio Bajo Silencio Silencio
Silencio P3 Silencio Extract large CLAUDE.md secciones a reglas TEN ANTE Medium TEN MEDIO ANTE
Silencio P4 Silencio Inscribir en memoria de establo limpio Silencio Bajo Silencio

6.2. Si `fix_automatically` es cierto, aplicar P0 se fija automáticamente.
6.3. Generar un informe resumido.

---

## Formato de salida

```yaml
context_rot_audit_result:
  rot_score: 12
  severity: "yellow"
  summary:
    total_checks: 89
    passed: 76
    warnings: 8
    failures: 5
  phases:
    size_audit:
      lines: 234
      status: "growing"
    reference_validation:
      total: 45
      missing: 3
    instruction_staleness:
      total: 23
      stale: 2
    rules_structure:
      total: 6
      orphaned: 1
    auto_memory:
      total: 3
      stale_entries: 1
  remediation:
    auto_fixed: 0
    manual_fixes_needed: 7
    priority_list: [...]
  overall_status: "NEEDS_ATTENCIÓN" 
```

---

## Condiciones de veto

Silencio Silencio Silencio Silencio Silencio Silencio
|-----------|--------|
Silencio No CLAUDE.md y no .claude/ directorio TEN-N- nada para auditar 
Silencio Proyecto no tiene historia de git (no puede determinar la estabilidad) TEN WARN -- cheques de estabilidad de patrón TEN
← La puntuación de Rot supera 50 Silencio HALT - crítico pudri, necesita atención humana inmediata TEN
TEN Auto-fix modificaría más de 10 archivos TEN HALT - demasiados cambios, requieren revisión manual TEN
| CLAUDE.md tiene secciones administradas por AIOS TEN WARN - no modifique las secciones administradas
