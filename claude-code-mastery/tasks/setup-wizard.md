# Task: Setup Wizard

** ID de usuario** CCM-CHIEF-003
**Version:** 1.0.0
**Command:** `*setup-wizard`
Orión (Orquesta)claude-mastery-chief)
**Purpose:** Asistente interactivo para establecer el Código Claude para un proyecto nuevo o existente, generando todos los archivos de configuración necesarios a medida del tipo de proyecto detectado.

---

## Overview

```
  +------------------+     +------------------+     +------------------+
  Silencio 1. Detectar Silencio -- confiar Silencio 2. Generar Silencio -- confiar Silencio 3. Configure 
  Silencioso Proyecto Tipo Silencio Silencio    CLAUDE.md     |     |    settings.json |
  +------------------+     +------------------+     +------------------+
       |                                                    |
       v
  +------------------+     +------------------+     +------------------+
  Silencio 4. Crear Silencio -- confiar Silencio 5. Configure Ø -- instrucciones  durable 6. Set Up Silencio
  |    .claude/rules Silencio viv vivificados Hooks Silencio Silencioso MCP Servers Silencio
  +------------------+     +------------------+     +------------------+
       |                                                    |
       v
  +------------------+     +------------------+
  Silencio 7. Crear Silencio -- confiar Silencio
  Silenciosos agentes (opt.) Silencio Silenciosos
  +------------------+     +------------------+
```

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
| project_root Silencio Silencio Silencio Directorio de trabajo Silencio Silencio Debe ser un directorio válido Silencio
Silencioso Silencioso Silencio Silencioso para el usuario Silencio No Silencio `guided` (por defecto, interactivo) o `express` (smart defaults) Silencio
Silencio preset Silencio Silencio Silencio para el usuario Silencio No Silencio tipo proyecto (monorepo, fullstack, biblioteca, api, cli) Silencio

---

## Preconditions

- El directorio de trabajo es una raíz de proyecto
- Escriba acceso al directorio del proyecto
- No existe un directorio .claude/ (o el usuario confirma sobreescritura)

---

## Fases de Ejecución

### Fase 1: Detectar Tipo de Proyecto

Analice el proyecto para determinar su tipo:

1. Comprobar los marcadores del proyecto:
   - `package.json` -> Node.js proyecto; comprobación de `workspaces` campo (monorepo)
   - `next.config.*` -> Next.js fullstack
   - `vite.config.*` - Contador Vite
   - `tsconfig.json` - Proyecto TipoScript
   - `pyproject.toml` / `setup.py` - Proyecto de títulos
   - `Cargo.toml` - Proyecto de Rust
   - `go.mod` - Proyecto Go
   - `.aios-core/` - Proyecto gestionado por AIOS
2. Detectar la estructura del proyecto:
   - `src/app/` o `app/` - ## App Router (en inglés)Next.js)
   - `src/pages/` - &gt; Páginas &gt; Router
   - `packages/` o `apps/` - ###############################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################
   - `src/lib/` o `lib/` - Biblioteca
   - `src/api/` o `server/` - API backend
3. Presente el resultado de detección y pida al usuario que confirme o anule

**Matriz tipo de proyecto:**

Silencio Tipo Silenciosos Marcadores Silencioso Modo de Permisión Predeterminada Silencio
|------|---------|------------------------|
TEN monorepo TENIDO espacios de trabajo, paquetes/ TENAceptarEditar TEN
Silencio Silencio fullstack Silencio next.config, app/ + api/ Silencio aceptaEditar Silencio
Silencioso frontend Silencio vite.config, src/components confidencialidad aceptadaEditar Silencio
TENIDO Api TENIDO servidor/, express/fastify dep ¦ aceptaEditar Silencio
Silencioso biblioteca main/module in in ingles package.json Silencioso preguntar Siempre Silencio
TENIDA cli TENIDO bin/campo en package.json Silencioso preguntar Siempre Silencio
Silencio Silencio Silencio Silencio , src/ Silencio aceptanEditar Silencio
Silenciosamente.aios-core/ directorio Н aceptaEditar ←

### Phase 2: Generate CLAUDE.md

1. Crear `.claude/CLAUDE.md` (o `./CLAUDE.md` basado en la preferencia del usuario)
2. Incluir secciones basadas en el tipo de proyecto:
   **Otro resumen del proyecto**: Nombre, descripción, pila de tecnología
   - **Development comandos**: Construir, probar, lint, servidor dev
   ** Normas del proyecto**: Convenciones, patrones, organización de archivos
   **Testing**: Marco de prueba, requisitos de cobertura, cómo ejecutar
   ** Notas de arquitectura**: directorios clave y su propósito
3. Uso de @imports para documentos de referencia grandes
4. Meta: menos de 200 líneas
5. Si el proyecto AIOS: incluye secciones específicas de AIOS (sistema de agentes, flujos de trabajo)

### Phase 3: Configure settings.json

1. Crear `.claude/settings.json` con:
   - **permissions.deny**: Archivos sensibles (.env, secretos/, credenciales)
   - **permissions.allow**: Operaciones de desarrollo seguro basadas en el tipo de proyecto
   - **permissions.defaultMode**: Basado en la matriz de tipo de proyecto
2. Add project-specific reglas:
   - Monorepo: Read/Edit en todos los paquetes
   - Frontend: permite Bash(npm run dev), Bash(npm run build)
   - API: negar llamadas de red externas por defecto
   - Biblioteca: permisos más estrictos (siempre)
3. Si el proyecto AIOS: añadir L1-L4 de protección de límites niega reglas

### Fase 4: Configurar .claude/rules/

1. Crear `.claude/rules/` directorio
2. Generar reglas condicionales basadas en la estructura del proyecto:
   - **api-rules.md**: convenios de la API (si src/api/ o servidor/ existe)
     - `paths: ["src/api/**", "server/**"]`
   - **test-rules.md**: Convenciones de prueba (si existen pruebas/ o __tests______)
     - `paths: ["tests/**", "**/*.test.*", "**/*.spec.*"]`
   - **component-rules.md**: Patrones de componentes (si src/components/ existe)
     - `paths: ["src/components/**", "**/*.tsx"]`
   - **database-rules.md**: Patrones de migración (si existen migraciones/o supabases/)
     - `paths: ["migrations/**", "supabase/**"]`
3. Crear una regla incondicional para project-wide convenios y convenciones

## Fase 5: Configure Hooks

1. Pregunte al usuario sobre sus necesidades de automatización:
   - validación previa al compromiso? (información, formato, tipo de comprobación)
   - ¿Seguridad de mando?
   - ¿Sesiones de registro? (Uso de herramientas de pista)
   - ¿Reserva la compactación? (guarda de contexto antes de auto-compaction)
2. Generar configuración de gancho basado en respuestas:
   ```json
   {
     "hooks": {
       "PreToolUse": [{
         "matcher": "Bash",
         "hooks": [{ "type": "command", "command": "...", "timeout": 10 }]
       }],
       "PreCompact": [{
         "hooks": [{ "type": "command", "command": "...", "timeout": 5 }]
       }]
     }
   }
   ```
3. Para modo expreso: aplicar predeterminados sensibles (PreToolUse bash guard + PreCompact)

## Fase 6: Configurar servidores MCP

1. Pregunte al usuario qué capacidades necesita:
   - Búsqueda en la Web (Exa)
   - Documentación de la biblioteca (Context7)
   - Automatización del navegador (Playwright)
   - Acceso a bases de datos (Base de datos, Postgres)
   - Acceso ampliado al sistema de archivos
2. Generar `.claude/mcp.json` con servidores seleccionados
3. Proporcionar instrucciones de configuración para cada servidor (instalar comandos, teclas API necesarias)
4. Para modo expreso: configure Context7 (más útil universalmente)

## Fase 7: Crear agentes (opcional)

1. Pregunte si el usuario necesita subagents personalizados
2. Si es así, crear `.claude/agents/` directorio con agentes de arranque:
   - **reviewer.md**: Agente de revisión de código con herramientas de lectura
   - **planner.md**: Agente de planificación con alcance limitado
3. Cada agente obtiene la delantera adecuada de YAML:
   ```yaml
   ---
   name: Reviewer
   description: Code review specialist
   tools: [Lee, Grep, Glob]
   ---
   ```
4. Para modo expreso: saltar a menos que el usuario solicite explícitamente

---

## Formato de salida

```markdown
## Setup Complete

**Project:** {project-name}
**Type:** {detected-type}
**Mode:** {guided | express}

### Files Created

| File | Purpose | Lines |
|------|---------|-------|
| .claude/CLAUDE.md | Project instructions | {N} |
| .claude/settings.json | Permissions and config | {N} |
| .claude/rules/{name}.md | Conditional rule | {N} |
| ... | ... | ... |

### Configuration Summary

- **Permission mode:** {defaultMode}
- **Deny rules:** {count} rules protecting sensitive files
- **Allow rules:** {count} rules for development operations
- **Hooks:** {count} hooks configured ({event names})
- **MCP servers:** {count} servers ({names})
- **Custom agents:** {count} agents ({names})

### Next Steps

1. Review .claude/settings.json and adjust permissions
2. Customize CLAUDE.md with project-specific instructions
3. Run `*audit` to verify the setup scores well
4. {Additional steps based on project type}
```

---

## Condiciones de veto

- ** NUNCA** sobreescribir la configuración existente .claude/ sin confirmación explícita del usuario.
- **NO** incluye claves de API reales, fichas o secretos en archivos de configuración generados. Utilice valores de marcador de posición con comentarios.
- ############################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################### `bypassPermissions` como modo predeterminado. `acceptEdits` o `askAlways`.
- ############################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################### CLAUDE.md más de 200 líneas. Se divide en @imports y .claude/rules/ si el contenido excede el límite.
- ** NUNCA** saltar el paso de confirmación de detección del tipo de proyecto, incluso en modo expreso.

---

## Criterios de finalización

- [ ] Tipo de proyecto detectado y confirmado
- [ ] CLAUDE.md generados por 200 líneas
- [ ] settings.json creado con deny-first reglas de permiso
- Al menos uno .claude/rules/ archivo creado con caminos: frontmatter
- [ ] ganchos configurados (al mínimo en modo guiado)
- [ ] Sección de servidores MCP (configurado o explícitamente saltado)
- [ ] Resumen de configuración mostrado con lista de archivos y los siguientes pasos
