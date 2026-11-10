# Task: Audit Existing Claude Code Integration

** ID de la lista:** CCM-PI-002
**Version:** 1.0.0
**Command:** `*audit-integration`
**Agente:**Conduit (project-integrator)
**Purpose:** Auditoría de una integración existente en el Código de Claude en un proyecto, verificación de la integridad, coherencia, salud y generación de una puntuación factible con recomendaciones.

---

## Overview

```
  Proyecto de objetivos
       |
       v
  +--------------------+
  . . . check .claude/ . .
  |    Completeness     |
  +--------------------+
       |
       v
  +--------------------+
  TEN 2. Validar configuración infligida
  |    Consistency      |
  +--------------------+
       |
       v
  +--------------------+
  Silencio 3. Check Rule Silencio
  |    Coverage         |
  +--------------------+
       |
       v
  +--------------------+
  Silencio 4. Verificar el gancho Silencioso
  |    Health           |
  +--------------------+
       |
       v
  +--------------------+
  
  |    Connectivity     |
  +--------------------+
       |
       v
  +--------------------+
  Silencio 6. Generar Puntaje Silencio
  |    & Recommendations|
  +--------------------+
```

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
| project_path Silencio Silencio Silencio Silencio Usuario o cwd Silencio Sí Silencio Debe contener .claude/ directorio Silencio
| deep_scan TENBOLEA TENIDO TENIDO Usuario TENIDO No TENIDO Falso predeterminado; verdaderos escanea todos los archivos fuente para la consistencia TENIDO

---

## Preconditions

- `.claude/` directorio existe en el proyecto objetivo
- Lea el acceso a todos los archivos del proyecto

---

## Fases de Ejecución

## Fase 1: Check .claude/ Completeness

Escanear el `.claude/` directorio y chequeo para componentes esperados:

Silencio Silencio Silencio Requerido Silencio Silencio Silencio
|-----------|----------|------|--------|
| CLAUDE.md | Yes | `.claude/CLAUDE.md` | 25 |
| settings.json | Yes | `.claude/settings.json` | 20 |
Ajustes confidencialidad.local.json Silencio recomendado `.claude/settings.local.json` | 5 |
Silencio reglas/ directorio Silencio recomendado Silencio `.claude/rules/` | 15 |
Silencio Al menos 1 archivo de reglas Silencio `.claude/rules/*.md` | 10 |
Silencio comandos/ directorio Silencio Opcional Silencio `.claude/commands/` | 5 |
TENCIÓN DE LA HABITACIÓN TENIDO TERRITORIO TENIDO ANTERIOR ANTERIOR TERRITORIO TERRITORIO TENIBILIDADES `.claude/skills/` | 5 |

Para cada componente, conste: present/missing, tamaño de archivo, última fecha modificada.

### Fase 2: Validar configuración de consistencia

Parse `.claude/settings.json` y comprobar:

1. **JSON validez**: parseable without errors
2. **Congruencia de la misión**: no hay contradicciones entre permitir y negar las reglas
3. **Apreciación del par**: todos los caminos referenciados en deny/allow en realidad existen
4. **Desfavorables graves**: no se denegó explícitamente la existencia de órdenes peligrosas comunes
   - `rm -rf /`, `git push --force`, `DROP TABLE`, `sudo`
5. **Oprofundamente permisivo**: `bash("*")` o comodín permite
6. **Compatibilidad de los AIOS**: si el proyecto AIOS verifica L1/L2 normas de protección

Marca cada hallazgo como: PASS, WARN, FAIL.

### Fase 3: Check Rule Coverage

Para cada archivo de reglas en `.claude/rules/`:

1. Validar el formato de frontmatter (patas: array presente si contextual)
2. Comprobar el contenido de reglas non-empty y actuar
3. Verificar los globs de ruta en la primera combinación de archivos de proyecto reales
4. Determinar las deficiencias en la cobertura:
   - Código fuente editado pero no coding-standards Regla
   - Pruebas presentes pero sin reglas de prueba
   - CI/CD archivos presentes pero no regla de flujo de trabajo
   - Los archivos de bases de datos presentan pero no existen reglas de base de datos

### Fase 4: Verificar la salud de los ganchos

Comprobar configuración y salud de ganchos:

1. **Registración**: Son ganchos registrados en settings.json o ~/.claude/settings.json?
2. **Existen archivos**: ¿Existen scripts de ganchos referenciados?
3. **Sintaxis**: ¿Pueden los scripts de gancho ser analizados sin errores?
4. **Permisiones**: ¿Son ejecutables scripts de gancho?
5. ** Riesgo de tiempo**: ¿Tienen los ganchos operaciones que podrían colgar (llamadas de red sin tiempo de salida)?

Para cada gancho, clasificar como: SALUD, DEGRADADO, BROKEN, MISSING.

## Fase 5: Test MCP Connectivity

Si los servidores MCP están configurados:

1. Listar todos los servidores MCP configurados desde la configuración
2. Para cada servidor, compruebe:
   - La configuración está completa (comandante, args, presente env)
   - Binary/command existe en la PATH
   - No hay problemas creíbles obvios (vars vacíos env)
3. Categorizar: CONNECTED, CONFIGURED, MISCONFIGURED, MISSING

Si no se configura ningún MCP, note como N/A con recomendación.

### Fase 6: Generar puntuación y recomendaciones

Calcular la puntuación de salud de integración (0-100):

```
Puntuación = suma(component_weight * component_score) / max_possible_score * 100

Where component_score:
  PASS = 1.0
  WARN = 0.5
  FAIL = 0.0
  N/A  = excluido del cálculo
```

**Puntos de grado:**

|-------|-------|-------|
Silencio 90-100 Silencio Un Silencio Excelente integración Silencio
TEN-VIS 75-89 TENIDO B ANTERIOR Good, minor improvements possible TEN
Silencio 60-74 Silencio C Silencio Funcional, notables lagunas Silencio
Silencio 40-59 Silencio D Silencio Problemas importantes, recomiendo la rehabilitación Silencio
Silencio 0-39 Silencio F Silencio Critical gaps, integration not effective 

---

## Formato de salida

```markdown
## Claude Code Integration Audit

**Project:** {project_path}
**Date:** {YYYY-MM-DD}
**Score:** {score}/100 (Grade: {grade})

### Component Status

| Component | Status | Details |
|-----------|--------|---------|
| CLAUDE.md | PASS/WARN/FAIL | {detail} |
| settings.json | PASS/WARN/FAIL | {detail} |
| Rules | PASS/WARN/FAIL | {N} files, {coverage}% coverage |
| Hooks | PASS/WARN/FAIL/N/A | {N} healthy, {N} broken |
| MCP | PASS/WARN/FAIL/N/A | {N} connected |

### Findings

#### Critical (Must Fix)
1. {finding} -- {recommendation}

#### Warnings (Should Fix)
1. {finding} -- {recommendation}

#### Info (Nice to Have)
1. {finding} -- {recommendation}

### Quick Fixes

{Numbered list of commands or actions to fix top issues}
```

---

## Condiciones de veto

* ** NUNCA** modificar cualquier archivo de proyecto durante la auditoría. read-only análisis
- **Nunca** ejecutar scripts de gancho para probarlos - sólo análisis estático
- ** NUNCA** intentar conexiones MCP que podrían desencadenar efectos secundarios
- ** NUNCA** reporte credenciales o secretos encontrados en los archivos de configuración

---

## Criterios de finalización

- [ ] Las 6 fases ejecutadas
- [ ] Puntuación calculada con componentes ponderados
- [ ] Grado asignado de la tabla del umbral
[ ] Conclusiones críticas enumeradas con recomendaciones específicas
- [ ] Resoluciones rápidas proporcionadas para los principales problemas
- [ ] Informe de auditoría presentado en formato estándar
