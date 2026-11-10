# Task: Design Permission Strategy

** ID de la lista:** CCM-CONFIG-005
**Version:** 1.0.0
**Command:** `*permission-strategy`
**Orquestador: ** Sigil (config-engineer)
**Purpose:** Diseñar una estrategia de permiso integral para un proyecto evaluando las necesidades de seguridad, seleccionando el modo de permiso adecuado y la ingeniería precisa allow/ask/deny reglas usando el Código de Claude `Tool(specifier)` sintaxis.

---

## Overview

```
  +------------------+     +------------------+     +------------------+
  Silencio 1. Evaluar  -- confiar Silencio 2. Elija ← ← Silencio 3. Configure Silencio
  Silencio Silencio Silencio Silencio Silencio Silencio Silencio Silencio Silencio Silencio Silencio Silencio 
  Silencio , necesidad Silencio , vida , vida , vida ,
  +------------------+     +------------------+     +------------------+
       |                                                    |
       v
  +------------------+     +------------------+     +------------------+
  Silencio 4. Configurar Silencio -- confiar Silencio 5. Establecer MCP ❌ -- confiar Silencio
  Silencio Silencio Silencio Silencio Silencio Silencio Silencio Silencio Silencio Silencio 
  +------------------+     |    Permissions   |     +------------------+
                            +------------------+
```

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
| project_root Silencio cadena Silencioso Directorio de trabajo Silencio Silencio Valid directorio de proyectos Silencio
| team_size Silencio Silencio Silencio Silencio Silencio Silencio Silencio Silencio `solo`, `small` (2-5), `team` (6+), `enterprise` |
confidencialidad Silencio Silencio Silencio Silencioso para el usuario Silencio `low`, `standard` (por defecto), `high`, `regulated` |

---

## Preconditions

- Comprensión de la pila tecnológica del proyecto
- Conocimiento de la composición de los equipos y patrones de acceso
- Sensibilización de cualquier requisito de cumplimiento (SOC2, HIPAA, etc.)

---

## Fases de Ejecución

### Fase 1: Evaluar las necesidades de seguridad del proyecto

1. Determinar el perfil de sensibilidad:

Silencioso Silencioso Silencioso Silencioso
|--------|--------|------------|
TENIDO PUEDOS PII/PHI datos TEN HIGH TEN TENIDO Compruebe los datos del usuario, registros de salud TEN
Silencio Tiene credenciales de producción TENIDO archivos .env, administradores secretos TEN
← Intección externa de API TEN MEDIUM TENIENDO Servicios de terceros, webhooks TEN
TENIDA Operaciones financieras TENIDO ALTO ANTERIENTE Tratamiento de pagos, facturación ANTE
Silencio Proyecto de fuente abierta TENIDO ANTERIENTE Código público, no secretos TEN
Silencio Herramienta interna Silencio MEDIUM Silencio Datos de la empresa, API interna Silencio

2. Escaneo para patrones de archivos sensibles:
   - `.env`, `.env.*` - variables ambientales
   - `*.pem`, `*.key`, `*.p12` -certificados y llaves
   - `secrets/`, `credentials/`, `private/` - directorios secretos
   - `*.tfvars`, `*.tfstate` - Estado Terraform con secretos
   - `docker-compose.*.yml` - Puede contener credenciales
3. Identificar patrones de operación seguros:
   - Operaciones de sólo lectura (git diff, git log, cat)
   - Build/test operaciones (npm run, pytest)
   - Servidores de desarrollo (npm run dev, siguiente dev)

### Fase 2: Elija el modo de permiso

Seleccione el modo base basado en la evaluación:

Silencioso Modo Silencioso Silencioso Silencioso Nivel de fricción Silencio
|------|----------|----------------|----------------|
TENEDAntes Siempre TENIDO Medios regulados, a bordo, alta sensibilidad TEN High TEN Maximum TEN
confidencialidad ← ← Desarrollo estándar, base de datos de confianza, sensibilidad media tención Medium TEN equilibrio TEN
TENER autoApprove TEN SOLO desarrollador solitario, baja sensibilidad, proyectos personales TENIDO TENIDO Mínimo TENIDO
Silencioso plan tención flujos de trabajo complejos que requieren aprobación directa (sólo gestionado) Silencio Medium TEN High TEN

** Árbol de la decisión:**

```
¿Está regulado (SOC2, HIPAA)?
  Sí - pide siempre + estrictas reglas de denegar
  NO - ¿Es un proyecto de equipo?
    YES - Confía en Editar + completo deny/allow
    NO - ¿Es alta sensibilidad?
      YES - Confía en Editar + reglas de negación estricta
      NO - título autoApprove + reglas básicas de deny (deny secrets)
```

Presente recomendación con racionalidad. Permite anular al usuario.

### Fase 3: Configure Allow Rules

Construir la lista de permisos utilizando `Tool(specifier)` sintaxis:

**Evaluation order reminder:** deny - título pid - título permit (primer partido gana).

**Common permite patrones por herramienta:**

Silencio Silencio Silencio Silencio Silencio Silencio 
|------|---------|---------|
| `Bash(npm run *)` ← Permitir todos los scripts npm ANTERIED Desarrollo workflow TEN
| `Bash(npx *)` Silencio Permitir ejecución npx Silencioso ejecución de herramientas
| `Bash(git status)` 
| `Bash(git diff *)` TENIDO TENIDO TERRITORIO TENIDO TENIDO TENIDO TERMINAR Código revisión TENIDO
| `Bash(git log *)` Silencio Historia de la Git Silencioso control de la versión
| `Bash(git add *)` Silencio Git estanca Silencioso control de la versión
| `Bash(git commit *)` Silencio Git compromete Silencioso control de la versión Silencioso
| `Bash(node *)` | Node.js execution Silencio Silencio
| `Bash(python *)` Silencio Ejecución de Python Silencio
| `Bash(pytest *)` Silencio Python testing Silencio Testing Silencio
| `Read(src/**)` Silencio Read source code Silencio Silencio
| `Read(docs/**)` Silencio Leer documentación Silencio Referencia Silencio
| `Read(tests/**)` ← Leer archivos de prueba Silencio Testing 
| `Edit(src/**)` Silencio Editar código fuente Silencioso
| `Edit(tests/**)` 
| `WebFetch(domain:*.npmjs.org)` Silencio NPM registro Silencio Información del paquete Silencio
| `WebFetch(domain:api.github.com)` ← GitHub API Silencioso Repository info ←
| `MCP(context7)` Silencios de la Biblioteca Silenciosos Documentación Silencio
| `Agent(Explore)` Silenciosos de exploración subagente Silenciosos

Personalizarse según las necesidades de proyectos detectadas.

### Phase 4: Configure Deny Rules

Construir la lista de denegación (evaluada primero, máxima prioridad):

**Mandatory deny rules (siempre incluyen):**

```json
{
  "deny": [
    "Read(./.env)",
    "Read(./.env.*)",
    "Read(./.env.local)",
    "Read(./secrets/**)",
    "Read(./**/*.pem)",
    "Read(./**/*.key)",
    "Read(./**/*.p12)",
    "Bash(rm -rf /)",
    "Bash(rm -rf ~)",
    "Bash(curl * | bash)",
    "Bash(wget * | bash)",
    "Bash(> /dev/sda)"
  ]
}
```

**Proyecto de reglas denegar específicamente:**

Silencio Proyecto Tipo Silencioso Reglas de Deny Adicional 
|-------------|----------------------|
| AIOS | `Edit(.aios-core/core/**)`, `Edit(.aios-core/constitution.md)`, `Edit(bin/aios.js)` |
| Infrastructure | `Bash(terraform apply *)`, `Bash(terraform destroy *)` |
| Database | `Bash(psql * DROP *)`, `Bash(mysql * DROP *)` |
| Docker | `Bash(docker rm -f *)`, `Bash(docker system prune *)` |

**Pregunte reglas (pronto antes de ejecutar):**

```json
{
  "ask": [
    "Bash(git push *)",
    "Bash(git checkout -- *)",
    "Bash(git reset --hard *)",
    "Edit(./package.json)",
    "Edit(./tsconfig.json)",
    "Bash(npm install *)",
    "Bash(npm uninstall *)"
  ]
}
```

## Fase 5: Establecer las Permisos de Herramienta MCP

1. Para cada servidor MCP configurado, agregue reglas de permiso apropiadas:
   - Servidores con confianza: añadir para permitir la lista (por ejemplo, `MCP(context7)`)
   - Confía en el semi: añadir a la lista de preguntas (por ejemplo, `MCP(filesystem)`)
   - Bloqueado: añadir a la lista denegatoria (por ejemplo, `MCP(untrusted-server)`)
2. Si la empresa: cheque `allowedMcpServers` / `deniedMcpServers` listas administradas
3. Para permisos del agente:
   - Permitir a los subagentes seguros conocidos: `Agent(Explore)`, `Agent(Plan)`
   - Agentes personalizados: añadir para permitir si confía, preguntar si es nuevo

---

## Formato de salida

```markdown
## Permission Strategy

**Project:** {project-name}
**Sensitivity:** {level}
**Team:** {size}
**Mode:** {selected-mode}

### Rule Summary

| Category | Count | Examples |
|----------|-------|---------|
| deny | {N} | .env, secrets, destructive commands |
| ask | {N} | git push, package.json changes |
| allow | {N} | npm scripts, git read-only, src/ access |

### Complete Configuration

```json
{
  "permissions": {
    "deny": [ ... ],
    "ask": [ ... ],
    "allow": [ ... ],
    "defaultMode": "{mode}"
  }
}
```

### Ejemplos de evaluación

Mostrar cómo se manejarán las operaciones específicas:

Silencio Silencio Silencio Silencio Silencio Categoría Silencio Silencio Silencio 
|-----------|---------|----------|--------|
| `cat .env` | `Read(./.env)` Silencio Silencio Silencio Silencio Silencio Silencio
| `npm run test` | `Bash(npm run *)` Silencio permitido Silencioso
| `git push origin main` | `Bash(git push *)` Silencioso pedi viv miento
| `edit src/app.ts` | `Edit(src/**)` Silencio permitido Silencioso

## Security Coverage

- [x] Archivos ambientales protegidos
- [x] Directores secretos bloqueados
- [x] Mandos destructivos bloqueados
- Pipe...to-shell ataques bloqueados
- [x] Certificate/key ficheros protegidos
- [ ] {Cualquier brechas marcados aquí]
```

---

## Condiciones de veto

- ** NUNCA** diseñar una estrategia sin negar reglas para .env y secretos. non-negotiable Bases de referencia de seguridad.
- ** NUNCA** añadir comandos bash destructivos (rm -rf, formato, mkfs) a la lista de permisos.
- ############################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################### `bypassPermissions` modo para entornos de equipo o empresa.
- ############################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################### `Bash(curl * | bash)` o `Bash(wget * | bash)` patrones - pipe-to-shell es un vector de ataque conocido.
- **Nunca** puso el mismo patrón en negar y permitir sin explicar que negar siempre gana.

---

## Criterios de finalización

- Evaluación de seguridad completada con perfil de sensibilidad
- [ ] Modo de permiso seleccionado con racional documentado
- [ ] Negar reglas cubren todos los patrones obligatorios sensibles
- Permitir que las reglas permitan flujos de trabajo detectados
- [ ] Pregunte reglas proteger la modificación de los archivos de configuración críticos
- [ ] MCP permisos de herramienta para todos los servidores configurados
- [ ] Ejemplos de evaluación muestran cómo se manejan las operaciones comunes
