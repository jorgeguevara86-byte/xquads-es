# Task: Configuration de la empresa

** ID de la lista:** CCM-CONFIG-007
**Version:** 1.0.0
**Command:** `*enterprise-config`
**Orquestador: ** Sigil (config-engineer)
**Fuente:** Generar e implementar enterprise-grade Configuración del Código de Claude managed-settings.json para la aplicación de políticas institucionales, la integración de MDM, las normas de cumplimiento y el despliegue normalizado de servidores MCP en equipos.

---

## Overview

```
  +------------------+     +------------------+     +------------------+
  Silencio 1. Establecer Silencio -- confiar Silencio 2. Configure ❌ -- Confesar Silencio 3. Establecer 
  TENED- TEN- TEN ANTE    MDM/OS-Level  Silencio Silencio administrado- Silencio
  |    settings.json |     |    Policies      |     |    mcp.json      |
  +------------------+     +------------------+     +------------------+
       |                                                    |
       v
  +------------------+     +------------------+
  Silencio 4. Configure ¦ -- confiar Silencio 5. Deploy 
  Silencio Silencio Silencio Silencio Silencio Silencio
  Silencio , Silencio , , , , , , . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
  +------------------+     +------------------+
```

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
| org_name Silencio Silencio Silencio Silencio Silencio Silencio Silencio Identificador de la Organización Silencio
tención permanente TENIDO array TENIDO Parámetro de usuario TEN No TENIDO Marcos de cumplimiento: `soc2`, `hipaa`, `gdpr`, `pci`, `iso27001` |
| platform_targets Silencio Silencio Silencioso para el usuario Silencio No Silencio `macos`, `linux`, `windows`, `wsl2` (por defecto: todos) Silencio
| team_count Silencio número Silencio para el usuario Silencio No Silencio Número de developers/teams usando el Código Claude TEN

---

## Preconditions

- Acceso administrativo para desplegar archivos de configuración gestionada
- Comprensión de las políticas de seguridad institucional
- Acceso al sistema MDM (para la lista de macOS o el despliegue del registro de Windows)
- Conocimiento de herramientas aprobadas y servidores MCP para la organización

---

## Fases de Ejecución

### Fase 1: Configuración managed-settings.json

Cree el archivo de configuración gestionado que no puede ser sobreimulado por el usuario o configuración del proyecto:

** Localizaciones de despliegue (una por plataforma):**

Silencio , Plataforma Silencio ,
|----------|------|
| macOS | `/Library/Application Support/ClaudeCode/managed-settings.json` |
| Linux/WSL | `/etc/claude-code/managed-settings.json` |
| Windows | `C:\Program Files\ClaudeCode\managed-settings.json` |

**Plantilla de base:**

```json
{
  "permissions": {
    "deny": [
      "Read(./.env)",
      "Read(./.env.*)",
      "Read(./secrets/**)",
      "Read(./**/*.pem)",
      "Read(./**/*.key)",
      "Bash(rm -rf /)",
      "Bash(curl * | bash)",
      "Bash(wget * | bash)"
    ],
    "defaultMode": "acceptEdits"
  },
  "disableBypassPermissionsMode": "disable",
  "allowManagedPermissionRulesOnly": false,
  "env": {
    "CLAUDE_CODE_EFFORT_LEVEL": "high",
    "CLAUDE_AUTOCOMPACT_PCT_OVERRIDE": "80"
  },
  "companyAnnouncements": [
    "{org_name}: Use Claude Code responsibly. Report issues to #ai-tools."
  ]
}
```

**Managed-only policy keys:**

Silencio Key Silencio Tipo Silencio Finalidad Silencioso
|-----|------|---------|----------------|
| `disableBypassPermissionsMode` | `"disable"` Silencio Prevenir a los usuarios de bypassing permissions ← Siempre establecido en la empresa ←
| `allowManagedPermissionRulesOnly` Silencioso booleano Silencio Sólo gestionado deny/allow reglas aplicables Silencio `true` para entornos regulados TEN
| `allowManagedHooksOnly` ← booleano Silencio Sólo los ganchos gestionados pueden ejecutar Silencio `true` para high-security |
| `allowManagedMcpServersOnly` ← boolean TENED Sólo los servidores MCP gestionados permitieron TEN `true` para el cumplimiento 
| `companyAnnouncements` TENEDAJE[] TEN Mensajes mostrados a todos los usuarios TENIDOS Uso para políticas y recordatorios TENIDO

### Phase 2: Configure MDM/OS-Level Políticas

Para las organizaciones que utilizan la gestión de dispositivos móviles:

**macOS (plist):**
```xml
<!-- com.anthropic.claudecode.plist -->
<dict>
  <key>disableBypassPermissionsMode</key>
  <string>disable</string>
  <key>permissions</key>
  <dict>
    <key>defaultMode</key>
    <string>acceptEdits</string>
    <key>deny</key>
    <array>
      <string>Read(./.env)</string>
      <string>Read(./.env.*)</string>
      <string>Read(./secrets/**)</string>
    </array>
  </dict>
</dict>
```

**Endos (Registrión):**
```
HKLM\SOFTWARE\Polices\ClaudeCode\
  disableBypassPermissionsMode = "disable" (REG_SZ)
  permisos\defaultMode = "acceptEdits" (REG_SZ)
```

**Linux (file-based):**
Despliegue `/etc/claude-code/managed-settings.json` a través de la gestión de configuración (Ansible, Chef, Puppet).

Proveed platform-specific scripts de implementación o fragmentos de configuración.

### Fase 3: Configurar managed-mcp.json

Crear la configuración MCP gestionada para herramientas organizativas estándar:

** Lugares de despliegue**

Silencio , Plataforma Silencio ,
|----------|------|
| macOS | `/Library/Application Support/ClaudeCode/managed-mcp.json` |
| Linux/WSL | `/etc/claude-code/managed-mcp.json` |
| Windows | `C:\Program Files\ClaudeCode\managed-mcp.json` |

**Template:**

```json
{
  "mcpServers": {
    "context7": {
      "command": "npx",
      "args": ["-y", "@context7/mcp-server"],
      "env": {}
    }
  },
  "allowedMcpServers": [
    { "serverName": "context7" },
    { "serverName": "playwright" }
  ],
  "deniedMcpServers": [
    { "serverName": "filesystem" }
  ]
}
```

**Server allowlisting strategy:**

Silencio Silencio Silencio Silencio Silencio Silencio Silencio
|----------|---------|----------|
Silencio Abierto (por defecto) Silencio No hay restricciones Silencio Equipos confiados, experimental TEN
Silencio `allowedMcpServers` array Ø equipos estándar, control moderado tención
Silencio Managed-only Silencio `allowManagedMcpServersOnly: true` Silencio ambientes regulados TEN
Silencioso Blocklist Silencio `deniedMcpServers` array Ø Ø Bloquear específico known-risky servidores Ø

### Phase 4: Configure Compliance Rules

Para cada marco de cumplimiento, añádase reglas específicas:

**SOC2:**
```json
{
  "permissions": {
    "deny": [
      "Read(./**/*.pem)", "Read(./**/*.key)",
      "Bash(curl * | bash)", "Bash(wget * | bash)"
    ]
  },
  "disableBypassPermissionsMode": "disable",
  "sandbox": {
    "network": { "allowManagedDomainsOnly": true }
  }
}
```

**HIPAA (datos de atención de salud):**
```json
{
  "permissions": {
    "deny": [
      "Read(./patient-data/**)", "Read(./phi/**)",
      "WebFetch"
    ],
    "defaultMode": "askAlways"
  },
  "allowManagedPermissionRulesOnly": true,
  "allowManagedMcpServersOnly": true
}
```

**GDPR (datos personales):**
```json
{
  "permissions": {
    "deny": [
      "Read(./user-data/**)", "Read(./pii/**)",
      "Read(./**/personal/**)"
    ]
  },
  "companyAnnouncements": [
    "GDPR: Do not paste personal data into Claude Code prompts."
  ]
}
```

**PCI-DSS (fecha de pago):**
```json
{
  "permissions": {
    "deny": [
      "Read(./payment/**)", "Read(./**/*card*)",
      "Read(./**/*billing*)"
    ],
    "defaultMode": "askAlways"
  },
  "disableBypassPermissionsMode": "disable"
}
```

Intensificar las normas de cumplimiento de la base managed-settings.json.

## Fase 5: Despliegue en toda la organización

1. Generar artefactos de despliegue:
   - `managed-settings.json` para cada plataforma
   - `managed-mcp.json` para cada plataforma
   - Perfiles MDM (lista para macOS, registro para Windows)
   - Gestionado CLAUDE.md (opcional, para org-wide instrucciones)
2. Crear documentación de despliegue:
   - Instrucciones de instalación por plataforma
   - Comandos de verificación para confirmar el despliegue
   - Procedimiento de reversión
3. Proporcione lista de verificación:

```bash
# Verify managed settings are loaded (run as user)
# Claude Code will show managed policy indicators in the UI

# Check managed file exists
# macOS:
ls -la "/Library/Application Support/ClaudeCode/managed-settings.json"
# Linux:
ls -la /etc/claude-code/managed-settings.json
# Windows:
dir "C:\Program Files\ClaudeCode\managed-settings.json"
```

---

## Formato de salida

```markdown
## Enterprise Configuration Package

**Organization:** {org_name}
**Compliance:** {frameworks}
**Platforms:** {targets}
**Teams:** {team_count}

### Generated Files

| File | Platform | Purpose | Deploy To |
|------|----------|---------|-----------|
| managed-settings.json | {platform} | Policy enforcement | {path} |
| managed-mcp.json | {platform} | Standard MCP servers | {path} |
| CLAUDE.md | All | Org-wide instructions | {path} |
| {mcp-profile} | macOS | MDM deployment | Jamf/Intune |

### Policy Summary

| Policy | Setting | Effect |
|--------|---------|--------|
| Bypass disabled | disableBypassPermissionsMode: disable | Users cannot skip permissions |
| Managed rules only | allowManagedPermissionRulesOnly: {val} | {effect} |
| Managed MCP only | allowManagedMcpServersOnly: {val} | {effect} |
| Network restriction | allowManagedDomainsOnly: {val} | {effect} |

### Deny Rules ({count} total)

{Numbered list of all deny rules with categories}

### Approved MCP Servers

| Server | Purpose | Status |
|--------|---------|--------|
| {name} | {purpose} | Allowed/Managed |

### Deployment Instructions

{Platform-specific deployment steps}

### Verification

{Commands to verify deployment on each platform}

### Rollback

{Steps to remove managed settings if needed}
```

---

## Condiciones de veto

* ** NUNCA** genera configuración empresarial sin `disableBypassPermissionsMode: "disable"`. Este es el control de seguridad empresarial fundamental.
- **NO** incluye claves de API reales, fichas o credenciales en archivos de configuración gestionados. Utilice referencias variables de entorno.
- ############################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################### `allowManagedPermissionRulesOnly: true` sin incluir reglas de negación integral, lo que dejaría el sistema sin protección.
- ############################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################### managed-settings.json sin proporcionar un procedimiento de devolución. Los errores de configuración a nivel gestionado afectan a todos los usuarios.
- ############################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################### compliance-specific normas cuando se especifica un marco de cumplimiento. El cumplimiento parcial es peor que documentado non-compliance.

---

## Criterios de finalización

- [ ] managed-settings.json generados con deny-first normas y claves de política empresarial
- [ ] MDM/OS-level método de despliegue documentado para las plataformas de destino
- [ ] managed-mcp.json generado con lista de servidores aprobada
- [ ] Normas de cumplimiento integradas para todos los marcos especificados
[ ] Instrucciones de despliegue creadas por plataforma
- [ ] Comandos de verificación proporcionados
- [ ] Procedimiento de reversión documentado
