# Task: Integrar el Código de Claude en el Proyecto Existente

** ID de la lista:** integrate-project
**Version:** 1.0
**Purpose:** Establecer infraestructura de Código de Claude en un proyecto existente con configuración adaptada
**Orquestador:**project-integrator (Conduit)
**Modelo:** Interactivo (elicito: verdadero)
**Calidad Estándar:** Integración pasa prueba de humo, todos los archivos de configuración válidos, CLAUDE.md de 200 líneas

---

## Overview

Esta tarea integra Claude Code en un proyecto existente detectando la pila tecnológica del proyecto, generando la configuración adecuada, estableciendo reglas, ganchos y servidores MCP. Sigue la filosofía Unix: hacer una cosa bien, componer herramientas pequeñas.

```
INPUT (project_root)
    |
[FAPACIDAD 1: PROYECTO DETECCIÓN]
    - Escáner para package.json, requisitos.txt, go.mod, etc.
    - &quot; Identifique marcos, idiomas y patrones &quot;
    - Detectar datos existentes CI/CD, forro, configuración de pruebas
    |
[FAPACIDAD 2: CLAUDE.MD GENERATION]
    - Generate CLAUDE.md adaptado al proyecto
    - e) Incluir normas de código, pruebas, convenciones de git
    - Mantener bajo 200 líneas
    |
[FAPOS 3: SETTINGS CONFIGURATION]
    -> Create .claude/settings.json
    - Confeccionar deny/allow reglas para caminos críticos
    - Establecer permisos apropiados para proyectar
    |
[FAPEL 4: RULES SETUP]
    - Crear .claude/rules/ directorio
    - Escribe path-based reglas contextuales
    - Confeccionar auto-loading comportamiento
    |
[FAPOS 5: HOOKS CONFIGURATION]
    - identificar puntos de integración de flujo de trabajo de proyecto
    - Configuración pre-tool-use guardias si es necesario
    - ganchos de notificación Configurar
    |
[PHASE 6: MCP SETUP]
    - Nombrar servidores MCP útiles para la pila
    - Confeccionar project-specific MCPs
    - disponibilidad de herramientas de validación
    |
[PHASE 7: AGENTS SETUP]
    - Crear project-specific subagent definitions
    - Configurar agentes para el dominio del proyecto
    - Ejecución de un agente de pruebas
    |
[FILO 8: SMOKE TEST]
    - Información Verificar todos los archivos de configuración parse correctamente
    - Test Claude Code puede leer y entender el proyecto
    - normas Validate cargan en contextos correctos
    |
OUTPUT: Integración completa del Código de Claude + resultados de prueba de humo
```

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
| project_root Silencio Silencio Silencio Auto-detect Silencio sí Silencio Valid directorio with source code ←
| project_name Silencio Silencio Silencio Auto o usuario Silencio no Silencio Nombre del proyecto legible por humanos Silencio
| primary_language Silencio Silencio Silencio Auto-detect Silencio no Silencio Principal lenguaje de programación Silencio
| team_size Silencio Silencio Silencio Silencioso Silencioso solo / pequeño / medio / grande 
| existing_ci Silencio booleano Silencio Auto-detect Silencio no Silencio CI/CD ya está configurado Silencio

---

## Preconditions

1. El directorio del proyecto existe con código fuente
2. Código CLI de Claude
3. El usuario ha escrito acceso al directorio de proyectos
4. Git se inicializa en el proyecto (o será)

---

## Fase 1: Detección de proyectos

** Objetivo:** Entender la pila tecnológica y las convenciones del proyecto.

### Detection Signals


|------|-----------|
| `package.json` | Node.js proyecto -- scripts de verificación, dependencias 
| `tsconfig.json` TENCIÓN DE TipoScript TENIDO
| `next.config.*` | Next.js framework |
| `requirements.txt` / `pyproject.toml` Silencio Proyecto Python Silencio
| `go.mod` Silencio, proyecto, vida
| `Cargo.toml` Silencio proyecto Rust Silencio
| `.eslintrc*` / `eslint.config.*` TEN ESLint configurado TEN
| `.prettierrc*` TENCIÓN Prettier configurado TEN
| `jest.config.*` / `vitest.config.*` Silencioso marco de examen
| `Dockerfile` / `docker-compose.yml` | Containerized |
| `.github/workflows/` Silencioso GitHub Actions CI/CD |
| `supabase/` 

### Steps

1.1. Raíz del proyecto de análisis para todas las señales de detección anteriores.
1.2. Read. `package.json` (si existe) para scripts y dependencias.
1.3. Identificar el patrón de estructura del proyecto (monorepo, single-app, biblioteca).
1.4. Detectar normas de formato y forro de código existentes.
1.5. Conclusiones de los documentos:

```yaml
detection:
  language: "TypeScript"
  framework: "Next.js 14"
  package_manager: "npm"
  test_framework: "Jest"
  linter: "ESLint"
  formatter: "Prettier"
  ci: "GitHub Actions" 
  database: "Supabase"
  structure: "single-app"
```

---

## Phase 2: CLAUDE.md Generación

** Objetivo:** Crear un conciso, eficaz CLAUDE.md archivo.

### Guidelines

- Mantenga debajo de 200 líneas (auto-memory compatibilidad)
- Enfóquese en lo que Claude necesita saber, no en la documentación general
- Incluir: normas de código, comandos de pruebas, convenciones de git, decisiones clave de arquitectura
- Usar secciones administradas (`<!-- AIOS-MANAGED-START -->`) para auto-updatable contenido

### Steps

2.1. Generar CLAUDE.md con estas secciones:
   - Resumen del proyecto (2 a 3 oraciones)
   - Resumen de la pila técnica (tabla)
   - Normas de código (de detección) linter/formatter config)
   - Comandos de prueba (de package.json scripts)
   - Convenciones de Git (de la historia de la comisión existente)
   - Directores clave y sus propósitos
   - Referencias comunes de comandos

2.2. El recuento de la línea de verificación es inferior a 200.
2.3. Si superan los 200, mueva secciones detalladas a `.claude/rules/` Archivos.

---

## Fase 3: Configuración

** Objetivo:** Crear `.claude/settings.json` con reglas apropiadas.

### Steps

3.1. Crear `.claude/settings.json` con:

```json
{
  "permissions": {
    "allow": [],
    "deny": []
  }
}
```

3.2. Agregue reglas de denegación para caminos sensibles:
   - `.env*` archivos (secretos)
   - `credentials*` files
   - `**/node_modules/**`
   - Archivos de configuración de producción

3.3. Añádase que se establezcan normas para las operaciones comunes de desarrollo:
   - Construir comandos
   - Comandos de prueba
   - Lint/format commands

---

Fase 4: Configuración de reglas

** Objetivo:** Crear reglas contextuales que se cargan en función de las rutas de archivos.

### Steps

4.1. Crear `.claude/rules/` directorio.
4.2. Crear reglas basadas en la estructura del proyecto:

Silencio Archivo de la regla Silencio Activa Cuando Silencio Content Silencio
|-----------|----------------|---------|
| `frontend.md` TENEDO Editar `src/components/**` TENCIÓN Patrones de componentes, convenciones de estilo
| `api.md` TENEDO Editar `src/api/**` o `pages/api/**` Ø Patrones de API, manejo de errores 
| `testing.md` TENEDO Editar `**/*.test.*` ← Testing conventions, mock patterns ←
| `database.md` TENEDO Editar `supabase/**` o `prisma/**` Silencio patrones de migración, reglas de esquema

4.3. Cada archivo de reglas debe usar la primera herramienta para especificar las rutas de activación:

```markdown
---
paths:
  - "src/components/**"
---
# Component Rules
...
```

---

## Fase 5: Configuración de ganchos

** Objetivo:** Integrar el Código Claude se engancha con el flujo de trabajo del proyecto.

### Steps

5.1. Evaluar qué ganchos beneficiarían al proyecto:
   - `PreToolUse` - protegerse contra la modificación de archivos protegidos
   - `PostToolUse` - uso de instrumentos de registro para la auditoría
   - `Notification` -- alerta sobre acontecimientos específicos
5.2. Crear ganchos en `.claude/hooks/` si el proyecto necesita comportamiento personalizado.
5.3. Inscribir ganchos en `.claude/settings.json`.

---

## Phase 6: MCP Setup

** Objetivo:** Configurar servidores MCP relevantes para el proyecto.

### Steps

6.1. Basado en la pila de tecnología detectada, recomiende servidores MCP.
6.2. Delegado mcp-workflow tarea para la configuración completa.
6.3. Documento configurado de MCPs en CLAUDE.md.

---

## Phase 7: Agents Setup

** Objetivo:** Crear project-specific definiciones subagentes.

### Steps

7.1. Basándose en la complejidad de los proyectos, crear agentes:
   - Para proyectos simples: no se necesitan agentes personalizados
   - Para proyectos medianos: 1-2 agentes especializados (por ejemplo, code-reviewer, test-writer)
   - Para grandes proyectos: equipo de agente completo con topología

7.2. Crear archivos de agente en `.claude/agents/`.
7.3. Delegado create-agent-definition tarea para cada agente.

---

## Phase 8: Smoke Test

** Objetivo:** Verificar las obras de integración end-to-end.

### Steps

8.1. Verificar todos los archivos de configuración son válidos JSON/YAML.
8.2. Verificar CLAUDE.md está debajo de 200 líneas y contiene secciones clave.
8.3. Prueba que las reglas se cargan al editar los archivos pertinentes.
8.4. Prueba que los servidores MCP se conectan (si se configuran).
8.5. Ejecute un simple comando de Código de Claude para verificar todo funciona:
   - Pide a Claude que lea un archivo fuente y explíquelo
   - Verificar que sigue las convenciones CLAUDE.md

---

## Formato de salida

```yaml
integration_result:
  project_type: "Next.js TypeScript"
  files_created:
    - "CLAUDE.md"
    - ".claude/settings.json"
    - ".claude/rules/frontend.md"
    - ".claude/rules/testing.md"
  mcp_configured: ["context7"]
  agents_created: []
  smoke_test:
    config_valid: true
    rules_load: true
    mcp_connected: true
    claude_responds: true
  overall_status: "PASS"
```

---

## Condiciones de veto

Silencio Silencio Silencio Silencio Silencio Silencio
|-----------|--------|
TENER EN LA EJECUCIÓN DEL Proyecto no tiene ningún código fuente TEN HALT - nada que integrar con TEN
| CLAUDE.md ya existe y ha gestionado secciones TEN WARN - fusionarse en lugar de sobreescribir TEN
| .claude/settings.json existe con reglas personalizadas ¦ WARN -- fusionarse, no sobreescribir 
Silencio No escriba acceso al directorio de proyectos TEN HALT -- no puede crear archivos de configuración TEN
Silencio Project utiliza lenguaje no compatible (sin señales de detección) Silencio WARN -- generar genérico CLAUDE.md |
