# Task: Optimize Context Window Usage

** ID de la lista:** CCM-CONFIG-004
**Version:** 1.0.0
**Command:** `*optimize-context`
**Orquestador: ** Sigil (config-engineer)
**Purpose:** Optimize context window use by analyzing CLAUDE.md tamaño, moviendo instrucciones detalladas a condicional `.claude/rules/`, configuración auto-compaction, y revisión auto-memory archivos para la eficiencia.

---

## Overview

```
  +------------------+     +------------------+     +------------------+
  Silencio 1. Analyze Silencio -- confiar Silencio 2. Mover detallado ← ← 3. Configure Silencio
  |    CLAUDE.md     Silencio Silencio Silencio Silencio Silencio Silencio
  Silencio Silencio Silencio Silencio para las reglas / Silencio Silencio
  +------------------+     +------------------+     +------------------+
       |                                                    |
       v
  +------------------+     +------------------+     +------------------+
  Silencio 4. Revisión Auto- ← -- confiar Silencio 5. Configure ❌ -- Confértese Silencio
  Silenciosos archivos de memoria Silencio Silencioso compaction Silencio
  +------------------+     +------------------+     +------------------+
```

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
| project_root Silencio Silencio Silencio Directorio de trabajo Silencio Silencio Debe contener CLAUDE.md o .claude/CLAUDE.md |
| target_lines Silencio número Silencio para el usuario Silencio No Silencio Objetivo max lineas para el usuario CLAUDE.md (por defecto: 200) Silencio
| dry_run Silencio booleano Silencio Parametro de usuario Silencio No Silencio Si es verdad, sólo reporte sin hacer cambios ←

---

## Preconditions

- Al menos uno CLAUDE.md archivo existe (proyecto root o .claude/)
- Lea el acceso a .claude/rules/ directorio
- Lea el acceso a auto-memory directorio (~/.claude/projects/)

---

## Fases de Ejecución

### Phase 1: Analyze CLAUDE.md Tamaño

1. Localizar todos CLAUDE.md archivos:
   - `./CLAUDE.md` (proyecto root)
   - `./.claude/CLAUDE.md` (Directorio de la carta)
   - `./CLAUDE.local.md` (sobresellas locales)
   - `~/.claude/CLAUDE.md` (user-level)
2. Para cada archivo, medida:
   - Conteo total de la línea
   - Conteo de secciones (por cabezas de marcado)
   - Conteo estimado de fichas (líneas x ~4 fichas promedio)
   - @import count y lo que se refieren
3. Categorizar secciones de contenido por propósito:
   - **Instrucciones del contrato** (debe quedarse): Vista general del proyecto, comandos clave, sistema de agentes
   ** Contenidos convencionales** (pueden pasar a reglas/): Marco específico, path-scoped
   - ** Material de referencia** (debería utilizar @imports): Docs de arquitectura, especificaciones de API
   ** Contenido de redundante** (puede eliminar): Duplicado en archivos, obsoleto
4. Generar el cuadro de análisis:

Silencioso Sección Silencioso Líneas Silencioso Categoría Silencioso Recomendación Silencio
|---------|-------|----------|----------------|
| {header} | {N} | {core/conditional/reference/redundant} | {keep/move/import/remove} |

### Fase 2: Mover Instrucciones detalladas a .claude/rules/

Para cada sección categorizada como "condicional":

1. Identificar las rutas de archivo que esta sección aplica a:
   - Instrucciones de API - confiar `src/api/**`, `server/**`
   - Patrones de componentes - `src/components/**/*.tsx`
   - Convenciones de prueba - título `tests/**`, `**/*.test.*`
   - Reglas de base de datos - título `migrations/**`, `supabase/**`
2. Crear un nuevo `.claude/rules/{section-name}.md` archivo:
   - Añadir `paths:` YAML frontmatter con patrones de glob adecuados
   - Mueva el contenido de la sección en el archivo de reglas
   - Formato preserve y ejemplos de código
3. Retirar la sección movida de CLAUDE.md
4. Añádase un breve comentario de referencia en el que se indicaba la sección:
   ```markdown
   <!-- API conventions: see .claude/rules/api-conventions.md -->
   ```

### Fase 3: Configure condicional Loading

1. Verificar todos los archivos de reglas nuevos tienen la primera opción:
   ```yaml
   ---
   paths:
     - "src/api/**/*.ts"
   ---
   ```
2. Prueba patrones de glob coinciden con archivos de proyecto reales
3. Organizar reglas en subdirectorios si existen muchas reglas:
   ```
   .claude/rules/
     frontend/
       component-patterns.md
       styling-rules.md
     backend/
       api-conventions.md
       database-rules.md
     testing/
       test-patterns.md
   ```
4. Retirar cualquier existente always-on reglas que deben ser condicionales

### Fase 4: Revisar archivos de memoria automática

1. Revisar el auto-memory directorio:
   - `~/.claude/projects/{project-hash}/memory/`
2. Si auto-memory Existen archivos:
   - Listar todos los archivos de memoria y sus tamaños
   - Comprobación de recuerdos obsoletos o irrelevantes
   - Recuerdos de bandera que duplican CLAUDE.md contenido
   - Sugerir limpieza de recuerdos de escalones
3. Si auto-memory no es activo:
   - Informar al usuario sobre auto-memory (Claude lo crea automáticamente)
   - No se necesitan medidas

## Fase 5: Configurar la compactación

1. Evaluar la configuración de compactación actual:
   - ¿Qué? `CLAUDE_AUTOCOMPACT_PCT_OVERRIDE` variable env
   - El gatillo predeterminado es ~95% de capacidad de contexto
2. Recomendar umbral de compactación basado en el tamaño del proyecto:

Silencio Proyecto Tamaño Silencio CLAUDE.md Líneas ← Recomendado PCT Silencio Rationale Silencio
|-------------|----------------|-----------------|-----------|
tención Small (Seguido 100 archivos) Нены невены невани неный Predeterminado (95%) TENRIOR TENIDO TERRITOR TENIDO TERRITOR TERRITOR TENIDO TERRITOR SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON SON
Silencio Medium (100-500 archivos) Silencio 100-200 Silencio 80% Silencio Algunos auriculares necesarios Silencio
TENIDO Grande (500+ archivos) TENIDO 200+ TEN 50-60% TENIDO compactación frecuente necesaria TENIDO

3. Comprobar el gancho PreCompact:
   - Si falta: recomiendo añadir uno para la preservación del contexto
   - Si está presente: verifique que tiene un tiempo razonable (5-10 segundos)
4. Check `CLAUDE_CODE_MAX_OUTPUT_TOKENS` ajuste:
   - Predeterminado: 32000, Máximo: 64000
   - Los valores más altos reducen la ventana contextual disponible
   - Recomendar por defecto a menos que el usuario necesite salidas largas

---

## Formato de salida

```markdown
## Context Optimization Report

**Project:** {project-name}
**Date:** {YYYY-MM-DD}
**Mode:** {dry-run | applied}

### CLAUDE.md Analysis

| Metric | Before | After | Change |
|--------|--------|-------|--------|
| Total lines | {N} | {N} | {-N (-X%)} |
| Sections | {N} | {N} | {-N} |
| Est. tokens | {N} | {N} | {-N (-X%)} |
| @imports | {N} | {N} | {+N} |

### Content Redistribution

| Section | Lines | Action | Destination |
|---------|-------|--------|-------------|
| {section} | {N} | {moved/imported/removed/kept} | {.claude/rules/X.md | @import | --} |

### Context Budget

| Component | Lines | Tokens (est.) | Loading |
|-----------|-------|---------------|---------|
| CLAUDE.md | {N} | {N} | Always |
| .claude/rules/ (total) | {N} | {N} | Conditional |
| Auto-memory | {N} | {N} | Always |
| **Total always-loaded** | {N} | {N} | -- |

### Compaction Settings

- **Current trigger:** {N}% (default | override)
- **Recommended trigger:** {N}%
- **PreCompact hook:** {configured | missing}
- **Max output tokens:** {N}

### Savings Summary

- **Context saved per interaction:** ~{N} tokens ({X}% reduction)
- **Conditional content:** {N} lines loaded only when relevant
- **Files optimized:** {N}
```

---

## Condiciones de veto

- ** NUNCA** borrar contenido de CLAUDE.md sin moverlo a .claude/rules/ o confirmando con el usuario que es redundante.
- ** NUNCA** set CLAUDE_AUTOCOMPACT_PCT_OVERRIDE abajo 30. Los valores demasiado bajos causan compactación excesiva que degrada la calidad de sesión.
- ############################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################### always-on reglas para el contenido que es path-specific. Siempre use caminos: de primera para carga condicional.
- ############################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################### auto-memory Los archivos son gestionados por el Código Claude automáticamente.
- ############################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################### CLAUDE.md abajo un mínimo funcional. Las instrucciones básicas (respecto general del proyecto, comandos clave, convenciones esenciales) deben permanecer.

---

## Criterios de finalización

- [Todos] CLAUDE.md archivos analizados con recuentos de línea y categorización de secciones
- [ ] Contenido condicional identificado y trasladado a .claude/rules/
- [ ] Patrones de brillo validados contra la estructura del proyecto
- [ ] Archivos de memoria automática revisados para la estabilidad
- [ ] umbral de compactación recomendado con racionalidad
- [ ] Before/after comparación generada muestra ahorros de token
