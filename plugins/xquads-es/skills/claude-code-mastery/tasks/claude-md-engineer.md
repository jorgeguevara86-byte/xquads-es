# Task: Engineer Optimal CLAUDE.md

** ID de la lista:** claude-md-engineer
**Version:** 1.0
**Purpose:** high-quality, conciso CLAUDE.md archivo optimizado para la carga y carga de contexto de Claude Code auto-memory
**Orquestador:**project-integrator (Conduit)
**Modelo:** Interactivo (elicito: verdadero)
**Estandar de calidad:** Bajo 200 líneas, todas las secciones pueden actuar, sin contenido de relleno, pasa self-review

---

## Overview

CLAUDE.md es el archivo más importante para la productividad del Código de Claude. well-engineered CLAUDE.md enseña a Claude cómo trabajar en el proyecto con fichas mínimas. Esta tarea crea una desde cero o reescribe una existente utilizando principios de ingeniería contextual.

```
INPUT (project_root + [existing_claude_md])
    |
[FAPACIDAD 1: ANÁLISIS PROYECTO]
    -Edificio de la pila técnica Analyze y estructura de proyecto
    - &quot; Determinar patrones y convenciones fundamentales &quot;
    - Determinar lo que Claude necesita saber
    |
[PHASE 2: CODE STANDARDS SECTION]
    - Extracto estilo de codificación del código existente
    - &quot; Definer las convenciones sobre nombres de nombres &quot;
    - Establecer patrones de importación y exportación
    |
[FAPACIDAD 3: RESPECTO DE LOS NECESIDADES]
    - Identifique el marco y patrones de prueba
    - comandos de Define
    - Establecer expectativas de cobertura
    |
[FAPACIDAD 4: TÍTULO Y CONVENCIONES PRÓXIMAS]
    - Extracto formato de mensaje de la historia
    - &quot; Instrumentos de designación de documentos &quot;
    - Obligaciones de relaciones públicas
    |
[FAPÍTULO 5: PROYECTO-SPECIFIC GUIDANCE]
    - Documento clave de la arquitectura decisiones
    - Lista de archivos críticos y sus propósitos
    - No. tool-specific Orientación
    |
[FAPÍTULO 6: OPTIMIZACIÓN]
    - título de menos de 200 líneas
    - excluido el contenido redundante
    -Verificar cada línea es factible
    |
[PHASE 7: GESTIÓN DE LAS SECCIONES]
    - agregar marcadores de sección gestionados para auto-updates
    - Separar contenido estable de contenido dinámico
    - Estrategia de actualización de documentos
    |
[FAPÉFONO 8: VALIDACIÓN]
    - Comprobación de cuenta de línea
    - Examen de contenido para la viabilidad de la acción
    - Test con la muestra de interacción Claude
    |
OUTPUT: Optimizado CLAUDE.md archivo
```

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
| project_root Silencio Silencio Silencio Auto-detect Silencio sí Silencio Valid directorio de proyecto Silencio
| existing_claude_md Silencio Silencio Silencio Auto-detect Silencio no Silencioso Sendero para existente CLAUDE.md si está presente .
| project_name Silencio Silencio Silencio Usuario o auto Silencio no Silencio Nombre del proyecto legible por humanos Silencio
| team_notes Silencio Silencio Silencio Silencio Usuario Silencio no Silencio Cualquier convención de equipo que no se capte en el código Silencio
Silencioso estilo Silencio enum Silencio Usuario Silencio no TENIDO minimal / standard / comprehensive (default: standard) TEN

---

## Preconditions

1. El directorio del proyecto existe con código fuente
2. Comprensión de lo que necesita el Código de Claude CLAUDE.md
3. Acceso al código existente del proyecto para la extracción de patrones

---

## Phase 1: Project Analysis

** Objetivo:** Determinar lo que Claude debe saber para ser productivo en este proyecto.

## Información Jerarquía (principalmente importante)

1. **Qué ejecutar** -- Construir, probar, comandos lint
2. **Cómo escribir código** - Patrones, convenciones, estilo
3. **Donde están las cosas** - Directores clave, puntos de entrada
4. **Qué no hacer** - Antipatterns, operaciones prohibidas
5. **Cómo integrar** - Corriente de trabajo de Git, proceso de PR

### Steps

1.1. Detectar la pila de tecnología (package.json, tsconfig.json, etc.).
1.2. Identificar los patrones más importantes analizando:
   - Patrones usados más frecuentemente en archivos
   - Patrones que son project-specific (no defectos marco)
   - Patrones que Claude se equivoca.
1.3. Listar lo que Claude necesita saber frente a lo que ya sabe:
   - Claude ya sabe React, TipoScript, marcos comunes
   - Claude NO conoce los patrones personalizados de su proyecto, alias, convenciones

---

## Fase 2: Sección de Normas de Código

** Objetivo:** Defina cómo debe escribirse el código en este proyecto.

### Steps

2.1 Analizar los archivos de fuente representativos de 5 a 10.
2.2. Documentar únicamente patrones que se desvían de los defectos:

```markdown
## Code Standards
- Use named exports (not default exports)
- Import with @ alias: `import { Button } from '@/components/Button'`
- Error handling: always use custom AppError class
- State: Zustand stores in src/stores/, one file per domain
```

2.3. Mantenga esta sección bajo 20 líneas.
2.4. Si las normas son complejas, cree `.claude/rules/code-standards.md` y lo referencia.

---

## Fase 3: Requisitos de prueba

** Objetivo:** Dile a Claude exactamente cómo probar en este proyecto.

### Steps

3.1. Extraer configuración de prueba de archivos de proyecto.
3.2. Documentar los comandos de prueba esenciales:

```markdown
## Testing
- Run all tests: `npm test`
- Run specific: `npm test -- --testPathPattern=auth`
- Coverage: `npm test -- --coverage`
- Watch mode: `npm test -- --watch`
- E2E: `npx playwright test`
```

3.3. Patrones de ensayo de documentos:
   - Donde viven los archivos de prueba (co-located vs directorio separado)
   - Convención de Naming (*.test.ts vs *.spec.ts)
   - Patrones de mock específicos para este proyecto

3.4. Mantenga esta sección bajo 15 líneas.

---

## Fase 4: Convenios sobre la Git y la PR

** Objetivo:** Enseñar el flujo de trabajo git del proyecto.

### Steps

4.1 Analizar mensajes recientes de confirmación para formato:

```bash
git log --oneline -20
```

4.2. Documentar las convenciones:

```markdown
## Git Conventions
- Commits: `type(scope): description` (conventional commits)
- Branch naming: `feature/`, `fix/`, `chore/`
- PR: squash merge, reference issue number
```

4.3. Mantenga esta sección bajo 10 líneas.

---

## Fase 5: Guía del Proyecto Específico

** Objetivo:** Documentar lo que hace que este proyecto sea único.

### Steps

5.1. Determinar las decisiones clave de la arquitectura:

```markdown
## Architecture
- Monorepo with packages/ directory
- API routes in src/app/api/ (Next.js App Router)
- Database: Supabase with RLS policies
- Auth: Supabase Auth with JWT
```

5.2. Listar archivos críticos que Claude debe saber sobre:

```markdown
## Key Files
- `src/lib/supabase.ts` -- Supabase client singleton
- `src/middleware.ts` -- Auth middleware for all routes
- `src/types/database.ts` -- Auto-generated DB types
```

5.3. Add tool-specific orientación si se utiliza non-standard herramientas.
5.4. Mantenga la sección combinada en 30 líneas.

---

## Fase 6: Optimización

** Objetivo:** Trim to maximum impact per token.

#### Optimization Rules

1. ** Cada línea debe ser accionable** - eliminar "este proyecto utiliza..." a favor de "utilizar..."
2. **No tutoriales** -- Claude sabe cómo funciona React, no lo expliques
3. **No relleno** - quitar "por favor, asegúrese", "asegúrese de", sólo decir la regla
4. **Recomendaciones sobre descripciones** `npm test` sobre "correr la suite de pruebas con npm"
5. **Cuantías sobre los párrafos** - datos estructurados es más rápido para parse
6. ** Diferencia a las reglas** - mover patrones detallados a `.claude/rules/` archivos

### Steps

6.1. Revisar cada línea y preguntar: "¿Podría quitarle a Claude esta causa para cometer un error?"
   - Si no, retíralo.
   - Si, si, quédatelo.
6.2. Convertir párrafos en puntos o tablas de bala.
6.3. Mueva cualquier sección más de 30 líneas a un archivo de reglas.
6.4. Longitud final de la meta:
   - Estilo mínimo: 50-80 líneas
   - Estilo estándar: 100-150 líneas
   - Estilo completo: 150-200 líneas

---

## Fase 7: Gestionado secciones

** Objetivo:** auto-updating de contenido dinámico.

### Patrón de Sección Gestionado

```markdown
<!-- MANAGED-START: tech-stack -->
## Tech Stack
- Next.js 14, React 18, TypeScript 5
- Tailwind CSS, shadcn/ui
- Supabase (auth + database)
<!-- MANAGED-END: tech-stack -->
```

### Steps

7.1. Identificar secciones que cambian frecuentemente (versiónes de pila de tecnología, comandos).
7.2. Envolverlos en marcadores de sección gestionados.
7.3. Determinar secciones estables (arquitectura, convenios).
7.4. Dejar las secciones estables como marcador plano.

---

## Phase 8: Validation

**El objetivo:** Verificar CLAUDE.md es eficaz.

### Validation Checklist

- Total de la línea cuenta con menos de 200
Cada sección tiene al menos una instrucción práctica
- [ ] Ninguna sección excede 30 líneas
- [ ] Todas las rutas de archivo referencia existen
- [ ] Todos los comandos referenciados existen en package.json
- [ ] No hay información duplicada en secciones
- No. tutorial-style explicaciones
- [ ] Administrar secciones correctamente formateado

### Steps

8.1. Ejecute la lista de verificación de validación.
8.2. Prueba con una muestra de interacción Claude:
   - Pide a Claude que cree un nuevo componente - ¿sigue los patrones?
   - Pide a Claude que agregue una prueba - ¿Usa el marco adecuado?
   - Pide a Claude que se comprometa... ¿Usa el formato correcto?
8.3. Si falla alguna prueba, identifique la instrucción que falta y añádala.

---

## Formato de salida

```yaml
claude_md_engineer_result:
  file: "CLAUDE.md"
  total_lines: 142
  style: "standard"
  sections:
    - name: "Panorama general de los proyectos" 
      lines: 5
    - name: "Normas de código" 
      lines: 18
    - name: "Testing"
      lines: 12
    - name: "Convenios de Git" 
      lines: 8
    - name: "Architecture"
      lines: 15
    - name: "Archivos clave" 
      lines: 10
    - name: "Commands"
      lines: 8
  managed_sections: 2
  rules_extracted_to:
    - ".claude/rules/code-standards.md"
    - ".claude/rules/architecture.md"
  validation:
    line_count: "pass"
    actionability: "pass"
    references: "pass"
    sample_test: "pass"
  overall_status: "PASS"
```

---

## Condiciones de veto

Silencio Silencio Silencio Silencio Silencio Silencio
|-----------|--------|
| CLAUDE.md supera 200 líneas después de la optimización TEN- continuar recortando o extrayendo a reglas TEN
Silencio No hay código fuente en el proyecto (nada para analizar) Silencio HALT - no patrones para documentar Silencio
TENIDO ANTERIOR CLAUDE.md ha gestionado secciones personalizadas de otra herramienta TEN WARN -- preservar los marcadores existentes TEN
TENCIÓN DEL PROYECTO language/framework sin convenciones detectadas Silenciosa WARN - generar mínimo CLAUDE.md |
TEN Todas las líneas eliminadas en optimización fueron marcadas como sea necesario TEN WARN -- proyecto puede realmente necesitar 200+ líneas, utilizar archivos de reglas TEN
