# Task: Audit Claude Code Settings

** ID de la lista:** CCM-CONFIG-002
**Version:** 1.0.0
**Command:** `*audit-settings`
**Orquestador: ** Sigil (config-engineer)
**Purpose:** Auditoría de todas las capas activas de configuración del Código Claude para conflictos, redundancias, brechas de seguridad y oportunidades de optimización mediante la lectura de archivos de configuración gestionados, de proyecto, locales y de usuarios.

---

## Overview

```
  +------------------+     +------------------+     +------------------+
  Silencio 1. Lea todo Silencio -- confiar Silencio 2. Check for ← Silencio 3. Validar Silencio
  Silencio Archivos pretensiones Silenciosos Silenciosos Silencio Silencio Silencio Deny Rules 
  +------------------+     +------------------+     +------------------+
       |                                                    |
       v
  +------------------+     +------------------+     +------------------+
  Silencio 4. Check ← -- confiar Silencio 5. Verify MCP ❌ -- Confeder TEN 6. Generate TENED
  Silencioso Permiso Silencioso Silencioso Silencioso Silencioso informe de auditoría Silencio
  |    Mode          |     |                  |     |                  |
  +------------------+     +------------------+     +------------------+
```

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
| project_root Silencio cadena Silencioso Directorio de trabajo Silencio Silencio Debe contener .claude/o ser una raíz de proyecto Silencio
| check_managed Silencio booleano Silencio Parameter de usuario Silencio No Silencio Ya sea para comprobar managed-settings.json (default: true) Silencio

---

## Preconditions

- Lea el acceso a todas las ubicaciones de archivos de la configuración
- Código Claude instalado en el sistema
- Al menos un archivo de configuración debe existir (.claude/settings.json mínimo)

---

## Fases de Ejecución

### Fase 1: Leer todos los archivos de configuración

Localizar y leer cada capa de configuración en orden de precedencia:

← Layer Silencio Prioridad Silencio Silencio Silencio
|-------|----------|------|-------|
Silencio 1 (Suspira) Silencio Managed Silencio Plataforma específica managed-settings.json Silencio, organización
Silencio 2 Silencio CLI args Silencio (solamente en tiempo – no se puede auditar de los archivos) Silencio Sesión Silencio
| 3 | Local | .claude/settings.local.json | Personal/project |
| 4 | Shared | .claude/settings.json | Team/project |
Silencio 5 (Lo más bajo) Silencio Usuario Silencio ~/.claude/settings.json | Personal/global |

**Ubicaciones de configuración administradas:**
- macOS: `/Library/Application Support/ClaudeCode/managed-settings.json`
- Linux/WSL: `/etc/claude-code/managed-settings.json`
- Windows: `C:\Program Files\ClaudeCode\managed-settings.json`

Para cada archivo encontrado:
1. Parse JSON y estructura validada
2. Extraer reglas de permiso (de acuerdo, preguntar, permitir arrays)
3. Extraer configuraciones de servidores MCP
4. Configuraciones de ganchos de extracción
5. Ajustes de caja de arena
6. Grabación de archivos tiempos de modificación

### Fase 2: Consulta por conflictos entre siguas

1. ** Conflictos de reglas**: El mismo patrón de herramienta (especificador) aparece en diferentes tipos de reglas a través de capas
   - Ejemplo: `Bash(npm run *)` en locales permitir pero compartido negar
   - Resolución: Negar siempre gana (comportamiento de fusión + desprecio)
   - Bandera como ATENCIÓN si el usuario probablemente lo desea
2. **Controversias de movimiento**: Diferente defaultMode entre capas
   - Gana una capa superior de precedencia
   - Bandera si se supera el espacio compartido (puede confuso equipo)
3. **Análisis de fusión de rayos**: Los arrays de permisos se fusionan entre los alcances
   - Identificar reglas duplicadas (samo patrón en múltiples capas)
   - Identificar contradicciones (pattern en tanto permiten y niegan)
4. **Conversaciones de gancho**: Mismo evento con diferentes configuraciones a través de capas
   - Los ganchos manejados no pueden ser sobresechados

### Fase 3: Validar las reglas deniega Cubre los caminos sensibles

Compruebe que los archivos sensibles críticos están protegidos:

**Requiere reglas denegar (plano si falta):**

TENIDO Pattern TENCIÓN PROTECCIÓN ANTERIENTE SEverity if Missing TEN
|---------|----------|---------------------|
| `Read(./.env)` Silencioso variables en el medio ambiente Silencio CRITICAL TEN
| `Read(./.env.*)` Silencios en el medio ambiente TEN CRITICAL TEN
| `Read(./secrets/**)` Silencioso directorio Secretos Silencio
| `Read(./**/*.pem)` | SSL/TLS certificados TENIDO ALTO TENIDO
| `Read(./**/*.key)` Silencio Privadas claves Silencio
| `Bash(rm -rf *)` Silencioso destructivo Silencio Silencio Silencio Silencio Silencio 
| `Bash(curl * \| bash)` TEN-to-shell atentados TENIDO ANTERIOR ANTERIOR

**Las reglas de la negación específicas de la AIOS (si .aios-core/ existe):**

TENIDO Pattern TENCIÓN PROTECCIÓN ANTERIENTE SEverity if Missing TEN
|---------|----------|---------------------|
| `Edit(.aios-core/core/**)` Silencio L1 Marco básico Silencioso
| `Edit(.aios-core/constitution.md)` Silencioso , Constitución ,
| `Edit(bin/aios.js)` Silencioso punto de entrada CLI Silencio

### Fase 4: Modo de Permisión de Verificación

1. Determinar el modo de permiso eficaz (ganancias de capa de precedencia más alta)
2. Evaluar la idoneidad del proyecto:
   - `bypassPermissions` en un proyecto de equipo - aviso CRITICAL
   - `autoApprove` sin reglas de negar - ES HIGH warning
   - `askAlways` con reglas de permiso extensa - título INFO (podría actualizar para aceptarEdits)
   - `acceptEdits` con reglas de negación adecuada - título Good (recomendado configuración)
3. Comprobar la cierre de la empresa:
   - `disableBypassPermissionsMode` en configuraciones gestionadas
   - `allowManagedPermissionRulesOnly` flag

## Fase 5: Verificar las configuraciones de servidor MCP

1. Recopilar configuraciones MCP de todas las capas
2. Para cada servidor:
   - Verificar command/URL se especifica
   - Compruebe que las variables de entorno referencia env vars (no valores codificados)
   - Verificar el servidor tiene una regla de permiso MCP (allow or ask) que coincide
3. Comprobar las restricciones de la empresa:
   - `allowManagedMcpServersOnly` flag
   - `allowedMcpServers` / `deniedMcpServers` lists
4. Bandera cualquier servidor MCP que no esté en la lista de permisos

## Fase 6: Generar informe de auditoría

Compilar todas las conclusiones en un informe estructurado.

---

## Formato de salida

```markdown
## Settings Audit Report

**Project:** {project-name}
**Date:** {YYYY-MM-DD}
**Layers Found:** {count}/5

### Layer Summary

| Layer | File | Exists | Rules | Mode |
|-------|------|--------|-------|------|
| Managed | {path} | {Yes/No} | {N deny, N allow} | {mode or --} |
| Local | .claude/settings.local.json | {Yes/No} | {N deny, N allow} | {mode or --} |
| Shared | .claude/settings.json | {Yes/No} | {N deny, N allow} | {mode or --} |
| User | ~/.claude/settings.json | {Yes/No} | {N deny, N allow} | {mode or --} |

### Effective Configuration

- **Permission mode:** {effective mode} (from {layer})
- **Total deny rules:** {N} (after merge + dedup)
- **Total allow rules:** {N} (after merge + dedup)
- **MCP servers:** {N}
- **Hooks:** {N} events configured

### Findings

| # | Severity | Finding | Layer(s) | Recommendation |
|---|----------|---------|----------|----------------|
| 1 | {CRITICAL/HIGH/MEDIUM/LOW/INFO} | {description} | {layer} | {fix} |

### Security Gaps

{List of missing deny rules that should be present}

### Conflicts

{List of rule conflicts between layers}

### Optimization Opportunities

{List of redundancies and improvements}
```

---

## Condiciones de veto

- ** NUNCA** modificar cualquier configuración de archivos durante la auditoría. read-only diagnóstico.
- ** NUNCA** muestra los valores reales de las teclas de API, fichas o secretos encontrados en la configuración.
- **Nunca** reportar una auditoría limpia si faltan reglas críticas de negar (para .env, secretos). Siempre marca estas.
- ############################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################### `bypassPermissions` modo como solución para cualquier problema.
- ############################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################### managed-settings.json check in enterprise environments -- it is the highest authority layer.

---

## Criterios de finalización

- [ ] Todas las capas de configuración accesibles leen y se analizan
- Conflictos entre capas identificadas y documentadas
- [ ] Camino sensible niega reglas validadas (reglas de la pérdida insignia)
- [ ] Modo de autorización evaluado para su idoneidad
- [ ] Configuraciones de servidor MCP verificadas
- [ ] Informe de auditoría generado con severity-ranked Conclusiones
