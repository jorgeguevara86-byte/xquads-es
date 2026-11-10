# Task: Establecer repositorio con la integración de código Claude

** ID de la lista:** CCM-PI-001
**Version:** 1.0.0
**Command:** `*setup-repository`
**Agente:**Conduit (project-integrator)
**Purpose:** Establecer un nuevo repositorio con la integración completa del Código de Claude desde cero, creando la estructura del directorio .claude/, CLAUDE.md, configuración, reglas y ganchos.

---

## Overview

```
  Project Directory
       |
       v
  +------------------+
  Silencio 1. Iniciar Git Silencio
  Silencio (si es necesario) Silencio
  +------------------+
       |
       v
  +------------------+
  Silencio 2. Crear .claude/
  Silencioso Directorio Árbol Silencio
  +------------------+
       |
       v
  +------------------+
  | 3. Generate       |
  |    CLAUDE.md      |
  +------------------+
       |
       v
  +------------------+
  | 4. Configure      |
  |    settings.json  |
  +------------------+
       |
       v
  +------------------+
  Silencio 5. Establecer reglas para la vida
  |    (.claude/rules)|
  +------------------+
       |
       v
  +------------------+
  Silencio 6. Configure Hooks
  |    (optional)     |
  +------------------+
       |
       v
  +------------------+
  Silencio 7. Verificar Configuración Silencioso
  +------------------+
```

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
| project_path Silencio Silencio Silencio Silencio Silencio Silencio Debe ser válido el directorio Silencio
| project_type Silencio en el futuro Usuario Silencio Silencio `monorepo`, `fullstack`, `frontend`, `backend`, `library`, `mobile` |
| team_size Silencio en el futuro Usuario Silencio No Silencio `solo`, `small` (2-5), `medium` (6-15), `enterprise` (15+) |
| existing_git Silencio booleano Silencio Detección Silencio No Silencio Auto-detectado de .git/ presencia Silencio

---

## Preconditions

- El directorio de objetivos existe y es obligatorio
- Node.js 18+ disponible en PATH
- Git instalado y configurado con el usuario.name y el usuario.email

---

## Fases de Ejecución

### Phase 1: Initialize Git Repository

1. Comprobación si `.git/` directorio existe en el camino de destino
2. Si falta, corre `git init` y crear inicial `.gitignore`
3. Si está presente, observe la rama actual y la historia reciente para el contexto
4. Validate git config tiene usuario.name y user.email set

**Estado de la broca:** Git ya inicializado.

### Fase 2: Crear .claude/Coordinación Directorio

Crear el árbol completo del directorio:

```
.claude/
  CLAUDE.md
  settings.json
  Ajustes.local.json    # Gitignored template
  reglas/ # reglas contextuales
  comandos/ # slash comandos (opcional)
  habilidades/ # definiciones de habilidades (opcional)
  agent-memory/ # memoria persistente (opcional)
```

Para cada directorio:
1. Crear directorio si no está presente
2. Add `.gitkeep` para directorios opcionales vacíos
3. Creación de registros en el registro de salida

### Phase 3: Generate CLAUDE.md

Generar un project-specific CLAUDE.md las mejores prácticas siguientes:

1. **Contexto del proyecto** (1-2 líneas): lo que es el proyecto, primario language/framework
2. **Construir &quot; Comandos de Pruebas**: comandos exactos para `dev`, `build`, `test`, `lint`, `typecheck`
3. ** Normas del código**: nombres de convenciones, estilo de importación, patrón de manejo de errores
4. ** Estructura del archivo**: directorios clave y su propósito (5-10 entradas)
5. ** Archivos protegidos**: archivos que nunca deben ser modificados por AI
6. **Patrones comunes**: 2-3 códigos de francos que muestran convenios de proyectos

**Constraints:**
- Mantenga bajo 150 líneas en total
- Sólo el contenido universalmente aplicable
- El conocimiento específico del dominio se basa en normas/ o habilidades/

### Phase 4: Configure settings.json

Crear `.claude/settings.json` con:

1. **permissions.allow**: operaciones seguras para el tipo de proyecto
   - Construir comandos, comandos de prueba, comandos lint
   - Archivo read/write dentro del ámbito de aplicación del proyecto
2. **permissions.deny**: operaciones peligrosas
   - `rm -rf /`, `git push --force`, acceso a la base de datos de producción
   - Rutas protegidas por el marco si se utiliza AIOS
3. **rules**: path-based configuración de carga de reglas

Adaptar permisos basados en `project_type`:
- `monorepo`: workspace-aware comandos
- `fullstack`: incluyen tanto las herramientas de construcción de frontend como backend
- `library`: publish-related Negar reglas

## Fase 5: Establecer reglas iniciales

Crear archivos de reglas en `.claude/rules/`:

1. **coding-standards.md**: language-specific convenios detectados por proyectos
2. **testing.md**: patrones y requisitos de prueba (framework-specific)
3. **git-workflow.md**: nombramiento de sucursales, compromiso de convenciones, orientación de plantillas de PR

Cada archivo de reglas incluye `paths:` frontmatter para la carga contextual:
```yaml
---
paths:
  - "src/**/*.ts"
  - "src/**/*.tsx"
---
```

### Fase 6: Configure Hooks (Optional)

Si el usuario quiere ganchos de automatización:

1. Detectar la infraestructura de ganchos disponibles (pre-commit, husky, lefthook)
2. Crear `.claude/hooks/` directorio si utilizas ganchos de Código de Claude
3. Sugerir configuraciones de ganchos para:
   - `PreToolUse`: validación de comandos (bloquear patrones peligrosos)
   - `PostToolUse`: logging and métricas
   - `Stop`: sesión de generación de resumen
4. Proporcione plantillas de gancho, no force-install

## Fase 7: Verificar la configuración

Ejecute cheques de verificación:

1. Confirmación `.claude/CLAUDE.md` existe y está bajo 150 líneas
2. Confirmación `.claude/settings.json` es válido JSON
3. Confirmar reglas/ directorio tiene al menos un archivo de regla
4. Prueba que el estado de git reconoce nuevos archivos
5. Generar informe de configuración con pass/fail por componente

---

## Formato de salida

```markdown
## Repository Setup Report

**Project:** {project_path}
**Type:** {project_type}
**Date:** {YYYY-MM-DD}

### Components Created

| Component | Status | Path |
|-----------|--------|------|
| .claude/CLAUDE.md | PASS | .claude/CLAUDE.md |
| settings.json | PASS | .claude/settings.json |
| Rules | PASS | .claude/rules/ (N files) |
| Hooks | SKIP/PASS | .claude/hooks/ |

### CLAUDE.md Summary
- Lines: {N}/150
- Sections: {list}

### Next Steps
1. Review CLAUDE.md and adjust project context
2. Run `claude` to test the integration
3. Consider adding skills with `*create-skill`
```

---

## Condiciones de veto

- ############################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################### CLAUDE.md sin confirmación del usuario
- ** NUNCA** añadir reglas para comandos destructivos (rm -rf, base de datos de caída)
- ** NUNCA** configura ganchos que bloquean el flujo de trabajo sin explícito opt-in
- ** NUNCA** comprometer archivos generados automáticamente - dejar que el usuario revise primero

---

## Criterios de finalización

- [ ] .claude / estructura del directorio creado
- [ ] CLAUDE.md generados bajo 150 líneas con project-specific contenido
- [ ] settings.json configurado con permisos apropiados
Al menos un archivo de reglas creado en .claude/rules/
- [ ] Verificación cheques todos pase
- [ ] Informe de configuración presentado al usuario
