# Task: Configure Sandbox Environment

** ID de la lista:** CCM-CONFIG-006
**Version:** 1.0.0
**Command:** `*sandbox-setup`
**Orquestador: ** Sigil (config-engineer)
**Fuente:** Configurar el entorno de caja de arena del Código Claude para el aislamiento de sistemas de archivos, restricciones de red y límites de proceso para garantizar la ejecución segura de comandos con mínima fricción.

---

## Overview

```
  +------------------+     +------------------+     +------------------+
  Silencio 1. Evaluar  -- confiar Silencio 2. Configure ❌ -- instrucciones ← 3. Establecer Silencio
  Silencio Silencio Silencio Silencio Silencio Silencio Silencio Silencio Silencio Silencio 
  ← Necesidades Silenciosas en las opciones Silenciosas Silenciosas
  +------------------+     +------------------+     +------------------+
       |                                                    |
       v
  +------------------+     +------------------+
  Silencio 4. Configurar ¦ -- confiar  durable 5. Test Sandbox Silencio
  Silencio Silencio Silencio Silencio Silencio Silencio
  |    Boundaries    |     |                  |
  +------------------+     +------------------+
```

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
| project_root Silencio cadena Silencioso Directorio de trabajo Silencio Silencio Valid directorio de proyectos Silencio
Silencioso plataforma Silencio Silencio autodetectado Silencio No Silencio `macos`, `linux`, `wsl2`, `windows` |
| isolation_level Silencio Silencio Silencio Silencio Silencio Silencio Silencio Silencio `standard` (por defecto), `strict`, `airgapped` |

---

## Preconditions

- Código de Claude instalado y operativo
- Comprensión de las necesidades de acceso a los sistemas de archivos y de la red del proyecto
- Plataforma soporta sandboxing (macOS, Linux, WSL2 -- Windows tiene soporte limitado)

---

## Fases de Ejecución

### Fase 1: Evaluar las necesidades de aislamiento

1. Determinar la plataforma y las características disponibles de la caja de arena:

Silencio Silencio Silencio Silencio Silencio Silencio Silencio Silencio Silencio Silencio 
|----------|--------------------|------------|---------|--------|
← macOS Silencio Apple Sandbox (Seatbelt) Silencio Apoyo completo Silencio Produccion Silencio
Silencio Linux ← Landlock + Seccomp ← Apoyo completo ← Apoyo completo Silencio Producción Silencio
Silencio WSL2 Silencio Linux sandbox en WSL Silencio Soporte completo Silencio Produccion Silencio
Silencio Windows (native) Silencio Limited Silencio Parcial Silencio Limited Silencio Limited Silencio

2. Requisitos de los proyectos de estudio:
   - ¿Qué directorios necesitan acceso por escrito? (src/, tests/, docs/, node_modules/)
   - ¿Qué directorios deberían ser? read-only? (.aios-core/, archivos de configuración)
   - ¿Qué directorios deben ser invisibles? (secretos/, archivos .env)
   - ¿Qué acceso externo a la red es necesario? (npm registro, servidores API, CDN)
   - ¿Hay algún sistema que necesite fuera de la caja de arena?

3. Elija el nivel de aislamiento:

Silencio Silencio Silencio Silencio Silencio Silencio Silencio Silencio Silencio 
|-------|-----------|---------|----------|
TEN estandar Silencio Escribir para proyecto, leer casa TENIDO Permitir dominios conocidos TEN desarrollo general TEN
Silencio estricto Silencio Escribir para src/ only Silencio Permitir sólo esencial Silencio Proyectos sensibles Silencio
Silencio aéreo Silencio Escribir para src/ only Silencio No hay red externa TENIDO Regulated/offline |

### Fase 2: Configurar el modo Sandbox en los ajustes

Generar la configuración de la caja de arena settings.json:

```json
{
  "sandbox": {
    "enabled": true,
    "autoAllowBashIfSandboxed": true,
    "excludedCommands": ["git", "docker"],
    "allowUnsandboxedCommands": false
  }
}
```

**Configuración clave explicada:**

Silencio Silencio Silencio Silencio Silencio Silencio Silencio 
|---------|---------|----------------|
| `enabled` TENCIÓN Sandbox para comandos bash TEN `true` para todos los proyectos compartidos Silencio
| `autoAllowBashIfSandboxed` TEN Saltar permisos de los clientes para sandboxed bash TEN `true` -- sandbox proporciona seguridad Silencio
| `excludedCommands` TENCIÓN Mandos que pasan sandbox TENIDO Sólo git, docker si es necesario TEN
| `allowUnsandboxedCommands` . Permitir `dangerouslyDisableSandbox` | `false` a menos que sea necesario explícitamente

### Fase 3: Establecer restricciones de red

Configurar el acceso de la red usando `network` sección:

```json
{
  "sandbox": {
    "network": {
      "allowedDomains": [
        "registry.npmjs.org",
        "api.github.com",
        "raw.githubusercontent.com"
      ],
      "allowUnixSockets": [],
      "allowAllUnixSockets": false,
      "allowLocalBinding": false,
      "httpProxyPort": 0,
      "socksProxyPort": 0
    }
  }
}
```

**Permisores de dominio común por tipo de proyecto:**

Silencio Proyecto Tipo Silencioso Dominios para Permitir 
|-------------|-----------------|
| Node.js Silencios.npmjs.org, nodejs.org Silencio

TENCIÓN Frontend TENEDKKKS, cdn.jsdelivr.net, fonts.googleapis.com TEN

TENCIÓN GitHub TENER Api.github.com, raw.githubusercontent.com TEN
TENIDO DOcker TENIDO registro.docker.io, auth.docker.io TEN
TENISTERIO DE API general TEN (project-specific Dominios API) Silencio

** Niveles de aislamiento**
- **standard**: Permitir registros de paquetes + API de proyecto
- **strict**: Permitir sólo registros de paquetes
- **airgapped**: Empty allowedDomains (no red externa)

### Fase 4: Configure File System Boundaries

Establecer controles de acceso a los sistemas de archivos:

```json
{
  "sandbox": {
    "filesystem": {
      "allowWrite": [
        "/src",
        "/tests",
        "/docs",
        "//tmp"
      ],
      "denyWrite": [
        "/.aios-core/core",
        "/node_modules",
        "/.git"
      ],
      "denyRead": [
        "/.env",
        "/.env.*",
        "/secrets"
      ]
    }
  }
}
```

**Path prefijo reference:**

Silencio Silencio Silencio Silencio Silencio
|--------|---------|---------|
| `//` Silencio Silencio , sistema de archivos , `//tmp/build` |
| `~/` TENIDO directorio SON TEN  `~/.ssh`, `~/.kube` |
| `/` Silencio Relativo a la configuración directorio de archivos Silencio `/src`, `/tests` |
| `./` TENIDO Sendero relativo resuelto por tiempo fijo `./output` |

**Standard escribe acceso:**

Silencio Silencio Silencio Escribir Permitido Silencio Escribir
|-------|---------------|--------------|
TENISTERIO TENIS Src/, tests/, docs/, tmp/ TEN node_modules/, .git/, .aios-core/core/ |
TEN TERRITO TENIDO Src/ only TENIDO Todo lo demás TENIDO
Silencio respirado Silencioso src/ con revisión Silencio Todo lo demás Silencio

**Leer restricciones (siempre niegan):**
- `.env`, `.env.*` - variables ambientales
- `secrets/`, `private/` - directorios secretos
- `~/.ssh/` - Llaves de SSH
- `~/.aws/` -- credenciales de AWS
- `~/.kube/` - Kubernetes configs

## Fase 5: prueba de aislamiento de la caja de arena

1. Verificar la caja de arena es activa:
   - Ejecutar un comando bash y comprobar los indicadores de caja de arena
   - Intento leer un camino negado (debería fracasar con gracia)
   - Intento escribir a un camino negado (debería fracasar con gracia)

2. Restricciones de la red de pruebas:
   - Intento de buscar un dominio permitido (debería tener éxito)
   - Intento deshacerse de un non-allowed dominio (debería ser bloqueado)

3. Probando límites del sistema de archivos:
   - Escribe a un camino permitido (debe tener éxito)
   - Escribe a un camino negado (debe ser bloqueado)
   - Lea desde un camino negado (debe ser bloqueado)

4. Resultados de la prueba de documentos:

Silenciosos exámenes Silenciosos esperados Silencio Actual Silencioso
|------|----------|--------|--------|
Silencio Read .env Silencio {result} | {PASS/FAIL} |
Silencio Escribe a src/ Silencio TODODO {result} | {PASS/FAIL} |
← Registro de la Npm Fetch npm Silencio {result} | {PASS/FAIL} |
← Fetch dominio aleatorio Silencio BLOCKED ← {result} | {PASS/FAIL} |

---

## Formato de salida

```markdown
## Sandbox Configuration

**Platform:** {platform}
**Isolation Level:** {standard | strict | airgapped}

### Settings Applied

```json
{completa sección de caja de arena settings.json}
```

### Filesystem Policy

Silencio Silencio Silencio Read Silencio Escribir Silencio Silencio
|------|------|-------|-----------|
Silencios in English Sí Silencio Silencio Silencio Código fuente desarrollo Silencio
Silencio .env Silencio No Silencio No Silencio variables ambiente sensible ←
| node_modules/ Silencio Sí Silencio No Silencio Dependencias ( gestionadas por npm) Silencio
| ... | ... | ... | ... |

### Network Policy

Silencio Silencio permitido Silencio
|--------|---------|-----------|
Silencio.npmjs.org Silencio Sí Silencio Instalación del paquete Silencio
Silencio *.supabase.co Silencio Sí Silencio Base de datos
Silencio * (todos los demás) Silencio No Silencio Por defecto Silencio

### Resultados de la prueba

{Mesa de la fase 5}

#### Excluidos Comandos

{Lista de comandos que pasan sandbox con justificación}
```

---

## Condiciones de veto

- ** NUNCA** desactivar el arenero sin confirmación explícita del usuario y justificación documentada.
- ############################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################### `allowAllUnixSockets: true` en entornos de producción o equipo - que supera las restricciones de la red.
* ** NUNCA** añadir directorio de inicio (*`~/`) a write-allowed sólo subdirectorios específicos si es necesario.
- ############################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################### `allowUnsandboxedCommands: true` en configuración de empresa o equipo -- permite pasar por alto todas las protecciones de caja de arena.
- ** NUNCA** añadir dominios de Wildcard (`*`) a la lista de permisos. Se específico acerca de qué dominios necesitan acceso.

---

## Criterios de finalización

[ ] Plataforma detectada y soporte de caja de arena verificada
- Nivel de aislamiento seleccionado basado en la evaluación de la seguridad
- [ ] Sandbox habilitado en la configuración con banderas apropiadas
- [ ] Restricciones de red configuradas con dominio específico
- [ ] Los límites del sistema de archivos write/read Controles
- [ ] Sandbox aislamiento probado con resultados documentados
