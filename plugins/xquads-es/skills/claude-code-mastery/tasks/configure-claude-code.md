# Task: Configure Claude Code Settings

** ID de la lista de documentos** CCM-CONFIG-001
**Version:** 1.0.0
**Command:** `*configure`
**Orquestador: ** Sigil (config-engineer)
**Purpose:** Configurar la configuración del Código Claude para un proyecto analizando las necesidades del proyecto y generando una configuración `.claude/settings.json` con permisos apropiados, denegar reglas y configuración del servidor MCP.

---

## Overview

```
  +------------------+     +------------------+     +------------------+
  Silencio 1. Analyze ← -- confiar Silencio 2. Generate ← ← 3. Establecer la Permiso
  Silenciosidad de las necesidades del proyecto    settings.json Silencio , Modo Silencioso
  +------------------+     +------------------+     +------------------+
       |                                                    |
       v
  +------------------+     +------------------+     +------------------+
  . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
  TENIDO MCP Servers TENIDO ANTERIEND Variables Env TENIDO TENIDO &gt; OUTPUT TEN
  +------------------+     +------------------+     +------------------+
```

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
| project_root TENTER TEN TERN Directorio de trabajo TEN ANTE Sí ANTERIENTE Directorio válido con archivos de proyecto TEN
| security_level Silencio Silencio Silencio Silencio Silencio Silencio Silencio Silencio `standard` (por defecto), `strict`, `enterprise` |
| existing_settings Silencioso objeto Silencio .claude/settings.json Silencio No TENIDO Config existente para fusionarse con TEN

---

## Preconditions

- Escriba acceso al directorio .claude/
- Comprensión de la pila tecnológica del proyecto (detectado o user-provided)
- Si existe settings.json: el usuario confirma la fusión o la estrategia de sobreescritura

---

## Fases de Ejecución

### Fase 1: Analizar las necesidades del proyecto

1. Escanear el proyecto para marcadores tecnológicos:
   - Administrador de paquetes: npm, hilo, pnpm, bun (ver archivos de bloqueo)
   - Marco: Next.js, Vite, Express, Fastify, Django, etc.
   - Pruebas: Jest, Vitest, Playwright, Cypress
   - Base de datos: Supabase, Prisma, Drizzle migrations
   - AIOS: ¡Mira!aios-core/ Directorio
2. Identificar patrones de archivos sensibles:
   - `.env`, `.env.*`, `.env.local`
   - `secrets/`, `credentials/`, `private/`
   - `*.pem`, `*.key`, `*.p12`
3. Determinar las operaciones de desarrollo seguro:
   - Los scripts de paquetes de package.json
   - Git read-only operaciones
   - Corredores de pruebas, linteres, formateadores
4. Resultados de documentos para el usuario

### Phase 2: Generate settings.json

Construir el archivo de configuración después deny-first metodología:

```json
{
  "permissions": {
    "deny": [
      "Read(./.env)",
      "Read(./.env.*)",
      "Read(./secrets/**)",
      "Read(./**/*.pem)",
      "Read(./**/*.key)",
      "Bash(rm -rf *)",
      "Bash(curl * | bash)",
      "Bash(wget * | bash)"
    ],
    "allow": [],
    "defaultMode": "acceptEdits"
  }
}
```

Populate `allow` basado en las necesidades de proyectos detectadas:
- **Always:** `Bash(git status)`, `Bash(git diff *)`, `Bash(git log *)`
- **Node.js:** `Bash(npm run *)`, `Bash(npx *)`, `Bash(node *)`
- **Python:** `Bash(python *)`, `Bash(pip *)`, `Bash(pytest *)`
- ¿Qué? `Bash({test-runner} *)` basado en un marco detectado
- **Edificio:** Permitir que se detecten comandos de construcción
- **Pintura:** Permitir detectar lint/format comandos

## Fase 3: Establecer el modo de transmisión

Seleccione el modo de permiso adecuado:

Silencioso nivel de seguridad Silencioso Modo predeterminado Silencioso
|---------------|--------------|-----------|
Silencio estándar Silencio aceptaEditar Silencio Auto-aproba la edición de archivos, avisos para bash/network |
TENTER TERRE TENIDO ANTERIENTES PUEBLOS PARA TODO LAS ACTIVIDADES DE TODO TENIENTES
Silencio , empresa Silencioso managed-settings.json restricciones Silencio

Presente el modo seleccionado con explicación. Permita que el usuario se anule.

**Configuración de la referencia de la Jerarquía (para la conciencia del usuario):**

```
managed-settings.json  (más alto -- no puede ser sobresulado)
  > Discusiones CLI (session-only)
  > Ajustes √.local.json (personal, gitignorado)
  > settings.json       (compartido, comprometido)
  > ~/.claude/settings.json (user-level, lowest)
```

### Fase 4: Configure MCP Servers

1. Preguntar qué servidores MCP necesita el proyecto
2. Para cada servidor seleccionado, añadir settings.json o .claude/mcp.json:
   ```json
   {
     "mcpServers": {
       "context7": {
         "command": "npx",
         "args": ["-y", "@context7/mcp-server"]
       }
     }
   }
   ```
3. Configuraciones de servidor comunes:
   - **context7**: Consulta de documentación de la biblioteca (no se necesita ninguna clave de la API)
   - **playwright**: Automatización del navegador (no se necesita ninguna clave de API)
   - **exa**: Búsqueda en la Web (requiere EXA_API_KEY)
   - **supabase**: Base de datos (requiere SUPABASE_ACCESS_TOKEN)
4. Para servidores que requieren claves API: añadir marcador de lugar con comentario, nunca código duro claves reales
5. Añádase reglas específicas de permiso para el PCM:
   - `MCP({server-name})` para permitir la lista de servidores aprobados
   - `MCP(filesystem)` negar la lista si no es necesario

## Fase 5: Establecer variables ambientales

1. Documento variables ambientales recomendadas para la configuración:
   - `ANTHROPIC_MODEL`: Sobresueldo modelo si es necesario
   - `CLAUDE_CODE_EFFORT_LEVEL`: high/medium/low
   - `CLAUDE_AUTOCOMPACT_PCT_OVERRIDE`: Gestión de contextos
   - `BASH_DEFAULT_TIMEOUT_MS`: Hora de salida del comando
2. Si la empresa: añadir los env organizativos para gestionar el config
3. Crear un bloque de comentarios de referencia en la parte superior de settings.json:
   ```json
   // Environment variables can be set in .env or shell profile:
   // CLAUDE_CODE_EFFORT_LEVEL=high
   // CLAUDE_AUTOCOMPACT_PCT_OVERRIDE=50
   ```
   (Nota: JSON no apoya los comentarios -- proporcionar como documentación separada)

---

## Formato de salida

```markdown
## Configuration Complete

**Security Level:** {standard | strict | enterprise}
**Permission Mode:** {defaultMode}

### Generated: .claude/settings.json

| Section | Count | Details |
|---------|-------|---------|
| deny rules | {N} | Blocks: {summary} |
| allow rules | {N} | Permits: {summary} |
| MCP servers | {N} | {server names} |

### Permission Rules

**Deny (evaluated first):**
{numbered list of deny rules with explanations}

**Allow:**
{numbered list of allow rules with explanations}

### Environment Variables

| Variable | Recommended Value | Purpose |
|----------|-------------------|---------|
| {name} | {value} | {purpose} |

### Verification

Run `*audit-settings` to validate the configuration.
```

---

## Condiciones de veto

- ############################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################### settings.json Cada configuración debe bloquear archivos sensibles al mínimo.
- ** NUNCA** claves de API de código duro, fichas o credenciales en archivos de configuración. Utilice variables de entorno o marcadores de posición.
- ############################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################### `bypassPermissions` como modo predeterminado a menos que el usuario lo solicite explícitamente y reconozca las implicaciones de seguridad.
- ############################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################### `Bash(rm -rf *)` u otras operaciones destructivas en la lista de permisos.
- ** NUNCA** fusionar la configuración sin mostrar al usuario el diff entre la configuración antigua y nueva.

---

## Criterios de finalización

- [ ] Necesidades de proyecto analizadas (tecnología, archivos sensibles, operaciones seguras)
- [ ] settings.json generados con deny-first reglas de permiso
- [ ] Modo de permiso seleccionado y justificado
- [ ] servidores MCP configurados con credenciales de marcador de posición
[ ] Recomendaciones ambientales variables documentadas
- [ ] Resumen de configuración mostrado al usuario
