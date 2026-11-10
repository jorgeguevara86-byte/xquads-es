# Task: Brownfield Project Claude Code Setup

** ID de la lista:** brownfield-setup
**Version:** 1.0
**Purpose:** Establecer el Código de Claude en un proyecto existente de campo marrón, respetando las convenciones establecidas y protegiendo las vías críticas
**Orquestador:**project-integrator (Conduit)
**Modelo:** Interactivo (elicito: verdadero)
**Estandar de calidad:** No se ha interrumpido el flujo de trabajo, se niegan las normas que protegen las vías críticas, las convenciones documentadas

---

## Overview

Esta tarea difiere de integrate-project en que se centra en **discovering y respetando las convenciones existentes** en lugar de establecer nuevas.El enfoque de brownfield prioriza la seguridad: protege lo que existe, enseña a Claude las reglas del proyecto e integre sin perturbar los flujos de trabajo establecidos.

```
INPUT (project_root + critical_paths)
    |
[FAPACIDAD 1: CODEBASE SCANNING]
    - # Descubre marcos, patrones, convenciones de nominación
    - No identificar estilo de codificación del código existente
    - Estructura y arquitectura de proyectos de mapa
    |
[FAPACIDAD 2: EXISTENCIA DE LA DETECCIÓN DE TOOLING]
    - Detectar datos CI/CD oleoductos
    - Detectar forro, formato, configuración de pruebas
    - &quot; Determinar los flujos de trabajo de despliegue &quot;
    |
[FAPACIDAD 3: CONVENCIÓN-RESPECTO CLAUDE.MD]
    - Generate CLAUDE.md que enseña a Claude las formas del proyecto
    - patrón de codificación de documentos encontrado en el código existente
    - Incluido project-specific terminología
    |
[FAPACIDAD 4: PATTERN RULES]
    - Crear reglas que codifican project-specific patrones
    - Entrenamiento Claude sobre decisiones arquitectónicas
    - Documento anti-patterns para evitar
    |
[FILSO 5: DENY RULES FOR CRITICAL PATHS]
    - Identifique files/directories que no debe ser modificado
    - Confeccionar reglas deny en settings.json
    - Establecer permisos para operaciones específicas
    |
[FAPÍTULO 6: INTEGRACIÓN DE LA FRONUCACIÓN]
    - Configurar ganchos para ya existentes CI/CD
    - Configuración pre-commit alineación con los revestimientos existentes
    - Garantizar que Claude siga el flujo de trabajo de la empresa
    |
OUTPUT: Brownfield integration config + caminos protegidos + documentos de convenciones
```

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
| project_root Silencio Silencio Silencio Auto-detect Silencio sí Silencio Proyecto existente con código fuente TEN
| critical_paths TENCIÓN TERRITORIO TENIDO NO TENIDO Senderos que nunca deben ser modificados por AI TEN
| team_conventions_doc TENED TENIDO TENIDO Usuario TENIDO NO TENIDO Send to existing coding standards doc TEN
| deployment_branch TENEDA TENIDO Usuario TENIDO NO ANTERIOR SUPERVISIÓN UTILIZADA PARA EL DISPONIBLE (por defecto: principal) TEN
| legacy_areas TENTER TERRI TEN SON TEN NO TENÍA A LOS Directores con código hereditario para tener cuidado con TEN

---

## Preconditions

1. El proyecto existe con base de código establecida (no verde)
2. El proyecto tiene historia de compromiso existente (para analizar convenciones)
3. El usuario puede identificar caminos críticos que necesitan protección
4. Git es inicializado y funcional

---

## Phase 1: Codebase Scanning

** Objetivo:** Comprender los patrones establecidos del proyecto sin cambiar nada.

### Steps

1.1. Escaneo estructura de directorios y construcción de un árbol fuente:

```
src/
  componentes/ - Confeccionar componentes (función, funciones de flecha)
  servicios/ - capa de servicio API de confianza (class-based)
  utiles/ - Confecciones de utilidad (funciones puras)
  ganchos/ - Confeccionar ganchos personalizados (utilización* noming)
  tipos/ - Nombres TipoScript tipo definiciones
```

1.2 Analizar patrones de codificación de archivos existentes:
   - Estilo de importación (nombre vs predeterminado, absoluto vs relativo)
   - Patrones de componentes (clase funcional vs, uso de ganchos)
   - Patrones de manipulación de errores (try/catch vs errores límites)
   - Convenciones de natación (camelCase, PascalCase, kebab-case para archivos)
   - Comentarios estilo y densidad

1.3. Detectar patrones arquitectónicos:
   - Enfoque de gestión del Estado
   - Patrones de integración de API
   - Estructura de rutina
   - Flujo de autenticación

1.4. Elaborar un inventario de patrones:

```yaml
patterns:
  imports: "absoluto con @ alias" 
  components: "funcional con funciones de flecha" 
  state: "Tiendas de Zustand en src/stores/" 
  api: "axios casos en src/services/" 
  naming:
    files: "kebab-case"
    components: "PascalCase"
    functions: "camelCase"
    constants: "UPPER_SNAKE_CASE" 
```

---

## Fase 2: Detección de Herramientas existentes

** Objetivo:** Mapa de todas las herramientas de desarrollo y flujos de trabajo existentes.

### Steps

2.1. Comprobación CI/CD:
   - `.github/workflows/*.yml` (GitHub Actions)
   - `.gitlab-ci.yml` (GitLab CI)
   - `Jenkinsfile` (Jenkins)
   - `.circleci/` (CircleCI)
   - `vercel.json` (Vercel)
   - `netlify.toml` (Netlify)

2.2. Comprobar herramientas de calidad de código:
   - `.eslintrc*` / `eslint.config.*` (ESLint)
   - `.prettierrc*` (Prettier)
   - `.stylelintrc*` (Stylelint)
   - `.editorconfig` (EditorConfig)
   - `commitlint.config.*` (Forro de mensaje de envío)

2.3. Comprobación para la prueba:
   - `jest.config.*` (Jest)
   - `vitest.config.*` (Vitest)
   - `cypress.config.*` (Cypress)
   - `playwright.config.*` (Playwright)

2.4. Document existing scripts from package.json:

```yaml
scripts:
  dev: "siguiente dev" 
  build: "siguiente construcción" 
  test: "Jest - recuperación" 
  lint: "eslint src/" 
  format: "más bonito -write src/" 
```

---

## Phase 3: Convention-Respecting CLAUDE.md

** Objetivo:** Crear CLAUDE.md que enseña a Claude a escribir código que parece la base de código existente.

### Steps

3.1. Escribir CLAUDE.md con énfasis en las pautas existentes:

```markdown
# {Project Name}

## Code Standards (from existing codebase)
- Import style: {detected pattern}
- Component pattern: {detected pattern}
- File naming: {detected pattern}
- Error handling: {detected pattern}

## Commands
- `{npm run dev}` -- Start development server
- `{npm test}` -- Run tests
- `{npm run lint}` -- Run linter

## Architecture
{Brief description of project structure}

## Critical Rules
- NEVER modify files in {critical_paths}
- ALWAYS follow existing patterns in neighboring files
- When in doubt, check how similar code is written in the codebase
```

3.2. Si existe un documento de convenios de equipo, incorpore sus normas.
3.3. Mantenga bajo 200 líneas. Mueva detalles a los archivos de reglas.

---

Fase 4: Reglas de Patrón

** Objetivo:** Crear reglas que codifican project-specific conocimiento.

### Steps

4.1. Crear `.claude/rules/` con los archivos de patrón:

Silencio Silencio Silencio Silencio Silencio Silencio Silencio
|------|---------|
| `code-style.md` TENIDO Convenciones de nombres, patrones de importación, estructura de archivos TENIDO
| `architecture.md` ← Límites de capa, flujo de datos, reglas de dependencia TENIDO
| `anti-patterns.md` Silencio cosas que nunca se pueden hacer en esta base de códigos
| `legacy-areas.md` tención Manejo especial para secciones de códigos legados TEN

4.2. Uso path-based activación para context-specific reglas:

```markdown
---
paths:
  - "src/legacy/**"
---
# Legacy Code Rules
- Do NOT refactor unless explicitly asked
- Maintain existing patterns even if suboptimal
- Add tests before making any changes
```

---

## Fase 5: Negar reglas para caminos críticos

** Objetivo:** Proteger archivos y directorios que AI no debe modificar.

### Senderos Críticos Comunes

Silencio Silencio Silencio Silencio Silencio
|-------------|--------|
| `.env*` Silencio Secretos y credenciales Silencio
| `**/migrations/**` Silencios de las migraciones de bases de datos (correr, no editar) Silencio
| `docker-compose.prod.yml` Silencio Infraestructura de producción tóxica
| `*.lock` tención archivos de bloqueo ( gestionados por gestores de paquetes) Silencio
| `.github/workflows/**` | CI/CD pipelines |
| `infrastructure/**` | Infrastructure-as-code |

### Steps

5.1. Recopilar rutas críticas del usuario y auto-detection.
5.2. Configurar reglas de denegación `.claude/settings.json`:

```json
{
  "permissions": {
    "deny": [
      "Edit(.env*)",
      "Write(.env*)",
      "Edit(**/migrations/**)",
      "Edit(docker-compose.prod.yml)",
      "Edit(.github/workflows/**)"
    ],
    "allow": [
      "Read(**)"
    ]
  }
}
```

5.3 Verificar las normas de denegación no obstaculizan la labor legítima de desarrollo.

---

## Fase 6: Integración del flujo de trabajo

** Objetivo:** Hacer que el Código de Claude funcione dentro de los flujos de trabajo existentes del proyecto.

### Steps

6.1. Configure pre-tool-use ganchos para alinearse con los revestimientos existentes:
   - Después de escribir código, sugiera que ejecute el comando lint del proyecto
   - Después de modificar las pruebas, sugiera ejecutar el comando de prueba del proyecto

6.2. Manejo de git alineado con las convenciones de equipo:
   - Detectar el formato de mensaje de la historia (composiciones convencionales, etc.)
   - Instrumentos de designación de documentos
   - Observe cualquier plantilla de PR o requisitos de revisión

6.3. Establecer ganchos de notificación para operaciones críticas:
   - Alerta al modificar archivos de configuración compartidos
   - Alerta cuando añada nuevas dependencias

---

## Formato de salida

```yaml
brownfield_setup_result:
  project_analysis:
    language: "TypeScript"
    framework: "Next.js 14"
    patterns_detected: 12
    tooling_detected: ["ESLint", "Prettier", "Jest", "GitHub Actions" ]
  files_created:
    - "CLAUDE.md"
    - ".claude/settings.json"
    - ".claude/rules/code-style.md"
    - ".claude/rules/architecture.md"
    - ".claude/rules/anti-patterns.md"
  critical_paths_protected: 5
  deny_rules_configured: 5
  existing_workflows_integrated: true
  disruption_risk: "none"
  overall_status: "PASS"
```

---

## Condiciones de veto

Silencio Silencio Silencio Silencio Silencio Silencio
|-----------|--------|
tención Project no tiene código fuente existente TEN HALT - uso integrate-project para Greenfield TEN
| CLAUDE.md existe y se mantiene manualmente TEN WARN - preguntar antes sobre la escritura TEN
← No puede detectar ningún patrón de codificación (empty repo) TEN HALT - nada que aprender de TEN
TEN La lista de rutas críticas está vacía y el proyecto es grande TEN WARN -- recomienda encarecidamente identificar caminos críticos TEN
TENIDO ANTERIOR .claude/settings.json ha negado reglas TEN TERMINADOR TENGE - añadir a las reglas existentes, no reemplazar 
