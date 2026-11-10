# Task: Claude Code CI/CD Pipeline Setup

** ID de la lista:** ci-cd-setup
**Version:** 1.0
**Purpose:** Configurar el Código Claude para la ejecución sin cabeza en CI/CD oleoductos (revisión de RPR, generación de códigos, pruebas)
**Orquestador:**project-integrator (Conduit)
**Modelo:** Interactivo (elicito: verdadero)
**Calidad Standard:** La tubería funciona correctamente en modo sin cabeza, límites de seguridad configurados, costos controlados

---

## Overview

Esta tarea establece el Código de Claude para ejecutarse CI/CD tuberías utilizando el modo sin cabeza (`claude -p`). Cubre la integración de GitHub Actions, gestión clave de API, configuración de formato de salida y límites de seguridad para evitar costos de escape.

```
INPUT (INPUT)ci_platform + integration_pattern + presupuesto)
    |
[FAPACIDAD 1: SELECCIÓN DE PATTERN INTEGRACIÓN]
    - Español Elige lo que Claude hace en CI (revisión, generación, prueba)
    - Confeccione los eventos de desencadenante (PR open, push, comment)
    - Establecer el alcance y las limitaciones
    |
[FILIA 2: HEADLESS MODE CONFIGURATION]
    - Confeccionar claude -p para non-interactive uso
    - Set de...output-format para machine-readable Producto
    - Confía en...max-turns para el control de costos
    |
[FAPACIDAD 3: GITHUB ACTIONS WORKFLOW]
    -> Create .github/workflows/claude-*.yml
    - Configurar los eventos de desencadenantes
    - Establecer pasos de trabajo
    |
[FAPACIDAD 4: API KEY AND ENVIRONMENT]
    - Establecer ANTHROPIC_API_KEY como secreto
    - Configurar variables de entorno
    - Establecer caché para el Código CLI de Claude
    |
[FAPOS 5: FORMATO DE LOS REBAJOS Y PARQUE]
    -> Configure --output-format stream-json
    - Resultado parse para comentarios de PR
    - salida de error de manole
    |
[PHASE 6: SAFETY LIMITS]
    - Set de...max-turns to cap execution
    - Configurar presupuesto por gastos por ejecución
    - Establecer alerta para anomalías
    |
Fuera. CI/CD archivos de flujo de trabajo + secretos docs + seguridad config
```

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
| ci_platform Silencio en el futuro Usuario Silencio sí Silencio github-actions / gitlab-ci / other TEN
| integration_pattern Silencio en el futuro Usuario Silencio sí Silencio pr-review / code-gen / prueba / costumbre TEN
| max_cost_per_run Silencio Silencio Silencioso usuario Silencio no Silencioso gorra de presupuesto (por defecto: $1.00) Silencio
| trigger_events TENRITER TENIDO Usuario TEN NO TENIDO Cuándo ejecutar (por defecto: pull_request) |
| claude_version TENCIÓN TENIDO Usuario TENIDO NO TENIDO Pin a versión específica o "latest" TEN

---

## Preconditions

1. Repositorio GitHub con Acciones habilitadas (o plataforma equivalente de CI)
2. Antropopic API clave disponible
3. El depósito ya ha CI/CD (recomendado, no necesario)
4. Entendimiento de qué tareas debería automatizar Claude

---

## Fase 1: Selección de Patrones de Integración

** Objetivo:** Elige el patrón de integración de CI adecuado.

### Patrones disponibles

Silencio Pattern Silencioso Trigger Silencio Qué Claude Hace Silencio Típico Costo Silencio
|---------|---------|-----------------|--------------|
Silencioso **Revisión de la revisión** `pull_request` Silencio Reseñas cambios de código, comentarios de publicaciones Silencio $0.10-0.50/PR |
Silencio ** Generación del proyecto** `workflow_dispatch` o comentario ¦ Genera el código desde spec/issue | $0.50-2.00/run |
Silencio **La generación más alta** `pull_request` TEN Genera pruebas para el nuevo código TEN $0.20-1.00/PR |
Silencio **Documentación** , `push` Silencio , actualizaciones de documentos para cambio de código Silencio $0.10-0.30/push |
Silencioso **Issue Triage** `issues.opened` TENIDO Categoriza y etiqueta temas TENED $0.05-0.10/issue |

### Steps

1.1. Seleccione uno o más patrones basados en las necesidades del equipo.
1.2. Definir el impulso específico para cada patrón.
1.3. Establecer el formato de salida esperado (comment, file, label).

---

## Fase 2: Configuración del modo sin cabeza

** Objetivo:** Configurar el Código Claude non-interactive ejecución.

## Modo sin cabeza Básicos

```bash
# Basic headless execution
claude -p "Review the changes in this PR for bugs and security issues"

# With output format
claude -p "..." --output-format stream-json

# With turn limit
claude -p "..." --max-turns 10

# With specific model
claude -p "..." --model sonnet

# With system prompt from file
claude -p "..." --system-prompt "$(cat .claude/ci-system-prompt.md)"
```

### Key Flags

Silencio Silencio Silencio Silencio Silencio
|------|---------|-------------|
| `-p` Silencio Modo no interactivo (leer desde el argumento) Silencio Siempre uso en CI Silencio
| `--output-format stream-json` TEN Máquina de salida JSON TEN para el procesamiento automatizado TEN
| `--output-format text` Ø Salida de texto Silencio Para simple registro Silencio
| `--max-turns` TENCIÓN Límite de llamadas herramienta TEN siempre establecido (por defecto: 10) 
| `--model` TENIDO Seleccionar modelo TENIDO sonnet para el costo, opus para la calidad TEN
| `--no-telemetry` ← Telemetría incapaz Silenciosa recomendada para CI Silencio

### Steps

2.1. Componga el comando sin cabeza para cada patrón de integración.
2.2. Crear un archivo de sistema de impulso para el contexto CI (`.claude/ci-system-prompt.md`).
2.3. Prueba el comando localmente antes de añadir a la CI.

---

## Fase 3: GitHub Actions Workflow

** Objetivo:** Crear el archivo de flujo de trabajo de CI.

### GitHub Actions Template

```yaml
name: "Claude Code Review" 
on:
  pull_request:
    types: [opened, synchronize]

permissions:
  contents: read
  pull-requests: write

jobs:
  claude-review:
    runs-on: ubuntu-latest
    timeout-minutes: 10
    steps:
      - name: Checkout
        uses: actions/checkout@v4
        with:
          fetch-depth: 0

      - name: "Instala el Código de Claude" 
        run: "npm instalar -g @anthropic-ai/claude-code@latest" 

      - name: "Run Claude Review" 
        env:
          ANTHROPIC_API_KEY: ${{ secrets.ANTHROPIC_API_KEY }}
        run: "DIFF=$(git diff origin/main...HEAD)\nclaude -p \"Revise estos cambios para fallos, problemas de seguridad y calidad de código. Sea conciso. Cambios: $DIFF\" \\\n  --output-format texto \\\n  --max-turns 10 \\\n  --model sonnet \\\n  > review-output.txt"
      - name: "Comentario de la publicación" 
        uses: actions/github-script@v7
        with:
          script: "const fs = require('fs');\nconst review = fs.readFileSync('review-output.txt, 'utf8');\nawait github.rest.issues.createComment({\n  propietario: context.repo.owner,\n  repo: context.repo.repo,\n  issue_number: context.issue.number,\n  cuerpo: `## Claude Code Review\\n\\n${review}`\n});"
```

### Steps

3.1. Crear `.github/workflows/claude-review.yml` (o equivalente).
3.2. Configurar los eventos de desencadenante.
3.3. Establece apropiado `timeout-minutes` (10 para los exámenes, 30 para la generación).
3.4. Add `permissions` bloque para los alcances de token GitHub requeridos.

---

## Phase 4: API Key and Environment

** Objetivo:** Configurar el acceso de API de forma segura.

### Steps

4.1. Add `ANTHROPIC_API_KEY` como un secreto de repositorio:
   - Ir a Ajustes √≥ Secrets and variables √≠a Acciones
   - Añadir `ANTHROPIC_API_KEY` con el valor clave API

4.2. Configurar variables ambientales adicionales si es necesario:

```yaml
env:
  ANTHROPIC_API_KEY: ${{ secrets.ANTHROPIC_API_KEY }}
  CLAUDE_MODEL: "sonnet"
  CLAUDE_MAX_TURNS: "10"
```

4.3. Consideraciones de seguridad:
   - NUNCA log la clave de API
   - Nunca pasar la llave como argumento de comando (use env var)
   - Usa secretos de repositorio, no variables de entorno en archivos de flujo de trabajo
   - Considere usar OIDC para autenticación sin clave si está disponible

---

## Fase 5: Formato de salida y pareado

** Objetivo:** Configurar la salida para el consumo de la máquina.

## Stream JSON Format

Cuando se utiliza `--output-format stream-json`, la salida es newline-delimited JSON:

```json
{"type": "assistant", "content": "Here is my analysis..."}
{"type": "tool_use", "tool": "Read", "input": {"file_path": "..."}}
{"type": "tool_result", "content": "..."}
{"type": "assistant", "content": "Based on reading the file..."}
```

### Steps

5.1. Elija el formato de salida basado en el patrón de integración:
   - Revisión de la política de relaciones públicas - título `text` (para publicar como comentario)
   - Generación de códigos - titulado `stream-json` (para analizar los cambios de archivo)
   - Pruebas - título `text` (para el resumen de resultados de la prueba)

5.2. Crear un script de lectura si utiliza `stream-json`:

```bash
# Extract final assistant message
claude -p "..." --output-format stream-json | \
  jq -s '[.[] | select(.type == "assistant")] | last | .content'
```

5.3. Casos de error de manutención:
   - Salida vacía - &gt; Claude no podía procesar
   - Tiempo de salida - aumentar el tiempo de salida o reducir el alcance
   - Límite de tarifas - agregar lógica de retry con backoff

---

## Fase 6: Limites de seguridad

** Objetivo:** Prevenir los costos de fuga y comportamiento involuntario.

### Configuración de seguridad

Silencio Silencio Silencio Silencio Silencio Silencio Silencio
|-------|-------|---------|
| `--max-turns` Silencio 10 (revisión), 25 (generación) Silencio Cap herramienta llamada iteraciones ←
| `timeout-minutes` Silencio 10 (revisión), 30 (generación) Silencio GitHub Acciones trabajo timeout Silencio
Silencio Max diff size TENENCIA 5000 líneas ANTERIOR Saltar muy grandes PRs TENIDO
TENEDO Costo por ejecución TEN $1.00 por defecto TENIDO Alerta si es excedido 
Silencio Corres por día Silencio 50 Silencio Prevenir el abuso high-activity repos ←

### Steps

6.1. Conjunto `--max-turns` por cada `claude -p` invocación.
6.2. Agregue un cheque de tamaño de diff antes de ejecutar Claude:

```bash
DIFF_LINES=$(git diff origin/main...HEAD | wc -l)
if [ "$DIFF_LINES" -gt 5000 ]; then
  echo "PR too large for automated review ($DIFF_LINES lines)"
  exit 0
fi
```

6.3. Configure job concurrency to prevent parallel runs:

```yaml
concurrency:
  group: claude-review-${{ github.event.pull_request.number }}
  cancel-in-progress: true
```

6.4. Establecer el control de costos (ver el panel de control de uso antropográfico).

---

## Formato de salida

```yaml
ci_cd_setup_result:
  platform: "github-actions"
  integration_pattern: "pr-review"
  files_created:
    - ".github/workflows/claude-review.yml"
    - ".claude/ci-system-prompt.md"
  secrets_required:
    - "ANTHROPIC_API_KEY" 
  safety_limits:
    max_turns: 10
    timeout_minutes: 10
    max_diff_lines: 5000
  estimated_cost_per_run: "$0.10-0.50"
  tested: true
  overall_status: "PASS"
```

---

## Condiciones de veto

Silencio Silencio Silencio Silencio Silencio Silencio
|-----------|--------|
TEN No acceso a la plataforma CI (no puede crear flujos de trabajo) TEN-necesita acceso a los administradores TEN
Ø API clave no disponible TEN HALT -- no puede configurar sin clave 
TEN Repository es público y la clave estaría expuesta TEN HALT - asegurar que los secretos estén correctamente configurados TEN
tención Cost budget es cero TEN HALT - modo sin cabeza incurre en costos API TEN
TEN CI plataforma no compatible (no GitHub Actions, no GitLab CI) TEN HALT - manual setup required TEN
