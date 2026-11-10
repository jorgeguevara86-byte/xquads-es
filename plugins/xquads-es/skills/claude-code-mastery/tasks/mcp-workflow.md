# Task: MCP Server Management Workflow

** ID de la lista:** mcp-workflow
**Version:** 1.0
**Purpose:** Descubra, evalúe, configure y valide servidores MCP para la pila de tecnología de un proyecto
**Orquestador:**mcp-integrator (Piper)
**Modelo:** Interactivo (elicito: verdadero)
**Estandar de calidad:** Integración completa de los PCM con el presupuesto de contexto documentado

---

## Overview

Esta tarea guía el ciclo de vida completo de la gestión del servidor MCP: desde descubrir qué servidores benefician al proyecto, mediante la evaluación de su impacto presupuestario contextual, para configurarlos y probarlos en el Código Claude.

```
INPUT (project_tech_stack + current_mcps)
    |
[FAPÍTULO 1: DISCOVERY]
    - Proyecto de escaneo para marcos, idiomas, servicios
    - Match contra el catálogo de servidor conocido MCP
    - No hay lagunas en la herramienta actual
    |
[FAPACIDAD 2: EVALUACIÓN DE PRESUPUESTO CONTEXTO]
    - ratio costo de token por servidor MCP
    - Compara el presupuesto total contra los límites modelo
    - Recomendar add/remove decisiones
    |
[FAPACIDAD 3: CONFIGURACIÓN]
    - Escoge la ubicación de los config (proyecto vs global)
    - Seleccione el transporte (stdio vs HTTP Streamable)
    - Escribe entradas MCP a ajustes
    |
[FAPACIDAD 4: SELECCIÓN DE TRANSPORTE]
    - Valorar los requisitos locales vs remotos
    - Configurar parámetros de transporte
    - Establecer variables y secretos de entorno
    |
[FAPOS 5: TOOL VALIDATION]
    - Testear la disponibilidad de herramientas de cada servidor MCP
    -Verificar respuestas de herramientas con llamadas de muestra
    - Documento disponible herramientas por servidor
    |
[FAPACIDAD 6: DOCUMENTACIÓN]
    - Actualización de datos CLAUDE.md con reglas de uso del MCP
    - Crear tabla de prioridades de selección de herramientas
    - título CLI-first vs MCP decision tree
    |
OUTPUT: servidores MCP configurados + informe de presupuesto contextual + CLAUDE.md actualizaciones
```

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
| project_root Silencio Silencio Silencio Auto-detect Silencio sí Silencio Valid directorio con package.json o equivalente TENIDO
| tech_stack TENCIÓN TERRITOR ANTERITO EScan o usuario TENIDO sí ANTERIOR Lista de frameworks/languages en uso TEN
| current_mcps Silencioso objeto Silencio .claude/settings.json TEN NO TENIDO Configuración MCP existente TENIDO
| context_budget_limit TENN NÚMERO TENIDO Usuario o predeterminado TEN NO TENIDO Max fichas para MCP overhead (por defecto: 10000) TEN

---

## Preconditions

1. El Código de Claude se instala y se aplica en el proyecto
2. `.claude/settings.json` o `~/.claude.json` existe (o se creará)
3. El usuario tiene acceso a los binarios del servidor MCP (npm, pip, docker)
4. Acceso a la red para servidores remotos de PCM (si procede)

---

## Phase 1: Discovery

** Objetivo:** Identificar qué servidores MCP beneficiarían este proyecto.

### Steps

1.1. Escanear la raíz del proyecto para los indicadores de pila de tecnología:
   - `package.json` -> Node.js ecosistema (mirar para React, Next.js, Express, etc.)
   - `requirements.txt` / `pyproject.toml` - ecosistema de Python
   - `docker-compose.yml` - Servicios basados en contenedores
   - `.env` / `supabase/` -> Supabase/database usage
   - `playwright.config.*` - Pruebas de exploradores

1.2. Apilación detectada de referencia cruzada contra el catálogo del servidor MCP:

Silencio Tech Stack Signal Silencio recomendado MCP Silencio
|-------------------|----------------|---------|
← Proyecto Supabase Silencioso Silencioso Silencioso Operaciones de base de datos, migraciones Silencio
Silencio Cualquier proyecto web Silencio playwright/browser TENCIÓN DE LA UI, capturas de pantalla TEN
← Investigación-Audición Silencio exa Silencio Búsqueda en la web, investigación de la empresa
Silencio Cualquier marco Silencio context7 Silencio Documentación de la biblioteca buscar
Silencio Docker servicios Silencio desktop-commander Silencio Silencio Silencio , .
Silencio GitHub repo Silencio github-cli (native) Silencio PR/issue , gestión y gestión

1.3. Listar los servidores MCP actuales de los config e identificar las lagunas.

---

## Phase 2: Context Budget Evaluation

** Objetivo:** Cuantifique el costo de ficha de cada servidor MCP.

#### Context Budget Math

Cada servidor MCP añade al sistema:
- **Registro de servidor:** ~200 fichas (nombre, descripción, información de conexión)
- **Definiciones de la herramienta:** ~100-400 fichas por herramienta (nombre, descripción, parámetros, esquema)
- ** Servidor típico: * 600-2000 fichas total

### Calculación presupuestaria

```
Costo total del PCM = SUM(server_tool_count * avg_tokens_per_tool + 200)

Example:
  playwright (15 herramientas) = 15 * 150 + 200 = 2.450 fichas
  context7 (2 herramientas) = 2 * 150 + 200 = 500 fichas
  exa (1 herramienta) = 1 * 150 + 200 = 350 fichas
  supabase (5 herramientas) = 5 * 150 + 200 = 950 fichas
  ---
  TOTAL = 4.250 fichas (~2% del contexto 200K)
```

### Decision Framework

Silencio Total MCP Budget Silencioso
|-----------------|---------------|
TENIDO QUINTO 5,000 fichas ANTERIOR Green - añadir libremente ANTERIOR
Ø 5,000-10,000 fichas Silencio Amarillo - evaluar cada adición 
Ø Ø 10.000 fichas ANTERIOR Rojo - eliminar low-value servidores Ø

2.1. Calcular el costo de fichas para cada servidor MCP propuesto.
2.2. Total de la suma y comparación con el límite presupuestario.
2.3. Si supera el presupuesto, los servidores de rango value-per-token y recomendar absorciones.

---

## Fase 3: Configuración

** Objetivo:** Escriba la configuración del servidor MCP a la ubicación adecuada.

#### Config Location Decision

Silencioso Silencioso archivo Silencioso Cuándo usar Silencio
|-------|------|-------------|
TEN-SÓLO PROPUESTO TENIDO `.claude/settings.json` TEN es MCP project-specific (por ejemplo, supabase for this DB) Silencio
← Global (todos los proyectos) Silencio `~/.claude.json` TEN es universalmente útil (por ejemplo, contexto7, exa) TEN

### Steps

3.1. Determinar el alcance de cada servidor MCP.
3.2. Lea el archivo de configuración existente.
3.3. Agregue entradas de servidor MCP con la estructura adecuada:

```json
{
  "mcpServers": {
    "server-name": {
      "command": "npx",
      "args": ["-y", "@package/mcp-server"],
      "env": {
        "API_KEY": "..."
      }
    }
  }
}
```

3.4. Validar la estructura JSON después de escribir.

---

## Fase 4: Selección de transporte

** Objetivo:** Elija el protocolo de transporte adecuado para cada servidor MCP.

### Transport Comparison

Silencio transporte Silencioso Protocolo Silencioso Caso Silencioso Silencioso Silencioso
|-----------|----------|----------|---------|-------|
| **stdio** (por defecto) Silencio stdin/stdout ← Herramientas locales CLI, la mayoría de los servidores TENIDO Bajo TENIDO Simple TEN
Silencio **HTTP Streamable** TEN HTTP + SSE TENIDO Servidores remotos, compartidos infra TEN Medium TENER URL + auth ANTE

### Decision Tree

```
¿El servidor MCP funciona localmente?
  Sí - Usar stdio (por defecto)
    ¿Es un binario CLI? - comando título + args
    ¿Es un contenedor Docker? - comando de ejecución de docker
  NO - Usar HTTP Streamable
    ¿Necesita austeridad? - Conf Añadir encabezado Autorización
    ¿Está detrás de un proxy? - Confeccionar URL proxy
```

4.1. Para cada servidor MCP, determinar si local o remoto.
4.2. Configure el transporte en consecuencia.
4.3. Establecer variables de entorno para las claves de API (nunca código duro en el configuración).

---

## Fase 5: Validación de la herramienta

** Objetivo:** Verificar cada servidor MCP está funcionando y sus herramientas son accesibles.

### Steps

5.1. Iniciar el Código Claude con la nueva configuración.
5.2. Para cada servidor MCP configurado, verifique la disponibilidad de herramientas:
   - Revisar que las herramientas aparecen en la lista de herramientas
   - Ejecute una llamada mínima de prueba (por ejemplo, contexto7) resolve-library-id con "reacto")
5.3. Documentar cualquier servidor que no se conecte.
5.4. Si un servidor falla, compruebe:
   - ¿Bloque instalado?
   - ¿Tecla de API válida? (env vars set)
   - ¿El puerto está disponible?
   - ¿Se puede acceder a la red? (para servidores remotos)

---

## Fase 6: Documentación

** Objetivo:** Actualizar la documentación del proyecto con las reglas de uso del MCP.

## CLI-First vs MCP Decision Tree

```
¿Necesitas realizar una tarea?
  |
  ¿Puede una herramienta de Código de Claude nativa hacerlo?
  (Lee, Escribe, Edita, Bash, Grep, Glob)
    Sí - Usar herramienta nativa (ALWAYS prefiere)
    NO - ¿Hay una herramienta MCP para ello?
      YES - Usar herramienta MCP
      NO - Usar Bash para install/run herramienta externa
```

### Steps

6.1. Añada o actualice la sección de MCP en CLAUDE.md con:
   - Lista de servidores configurados y sus propósitos
   - Prioridad de selección de herramientas (native √ MCP √ Bash)
   - Reglas de uso específicas para servidores
6.2. Crear `.claude/rules/mcp-usage.md` si no existe, con path-based activación.
6.3. Documentar cualquier server-specific gotchas (auth, limites de tarifas, etc.).

---

## Formato de salida

```yaml
mcp_workflow_result:
  servers_configured:
    - name: "context7"
      transport: "stdio"
      tools: 2
      token_cost: 500
      status: "verified"
    - name: "playwright"
      transport: "stdio"
      tools: 15
      token_cost: 2450
      status: "verified"
  total_token_cost: 2950
  budget_status: "green"
  files_modified:
    - ".claude/settings.json"
    - "CLAUDE.md"
  documentation_updated: true
```

---

## Condiciones de veto

Silencio Silencio Silencio Silencio Silencio Silencio
|-----------|--------|
TEN MCP token budget exceeds 15,000 tokens TEN- debe eliminar servidores antes de proceder TEN
TEN API clave requerida pero no proporcionada TEN SKIP servidor -- documento como pendiente 
TEN MCP servidor binario no instalado TEN SKIP servidor -- sugiere alternativa TEN
Silencio Config file write fails Silencio HALT -- check file permissions Silencio
← Todos los servidores MCP fallan la validación TEN HALT - probable problema del medio ambiente, depurar primero TEN
