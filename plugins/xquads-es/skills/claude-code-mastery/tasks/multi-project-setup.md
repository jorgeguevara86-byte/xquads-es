# Task: Multi-Project Claude Code Setup

** ID de la lista:** CCM-PI-004
**Version:** 1.0.0
**Command:** `*multi-project-setup`
**Agente:**Conduit (project-integrator)
**Fuente:** Configurar Código Claude para múltiples proyectos relacionados, configurando configuraciones de usuario compartidas, project-specific anula, servidores compartidos de MCP, y cross-project reglas.

---

## Overview

```
  Proyectos múltiples
       |
       v
  +-----------------------+
  Silencio 1. Proyecto de análisis
  |    Relationships      |
  +-----------------------+
       |
       v
  +-----------------------+
  Silencio 2. Configure Shared TENED
  TENCIÓN DE LOS UTILIZADOS TENIDO
  +-----------------------+
       |
       v
  +-----------------------+
  Silencio 3. Crear Per-Project Silencio
  |    Settings           |
  +-----------------------+
       |
       v
  +-----------------------+
  Silencio 4. Establecer compartido Silencio
  TENCIÓN MCP Servers TENIDO
  +-----------------------+
       |
       v
  +-----------------------+
  Silencio 5. Configure Shared TENED
  |    Rules              |
  +-----------------------+
       |
       v
  +-----------------------+
  Silencio 6. Verificar Cross- Silencio
  Silencio del proyecto
  +-----------------------+
```

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
tención proyectos confidencialidad objetos[] Silencio Usuario Silencio Sí Silencio Array de {pata, nombre, tipo} para cada proyecto Silencio
Silencio Silencio Silencio Silencio Silencio Silencio Silencio Silencio `monorepo`, `polyrepo-shared-stack`, `polyrepo-independent`, `workspace` |
| shared_tools TENEDAJE[] TENIDO Usuario TENIDO No TENCIÓN Herramientas utilizadas en todos los proyectos (por ejemplo, "eslint", "jest", "docker") TEN

---

## Preconditions

- Todos los directorios de proyectos incluidos en la lista existen y son accesibles
- El usuario tiene acceso a la escritura `~/.claude/` (user-level config)
- Cada proyecto se ha inicializado con git

---

## Fases de Ejecución

### Fase 1: Analizar las relaciones del proyecto

Para cada proyecto, determinar:

1. **Idioma y marco**: detección de package.json, Cargo.toml, pyproject.toml, etc.
2. **Cuentas compartidas**: qué paquetes aparecen en los proyectos
3. **Pautas compartidas**: convenciones de nombres, similitudes de la estructura de directorios
4. ** Patrones de comunicación**: hacer proyectos importados entre sí (monorepo), compartir API (microservicios) o operar independientemente
5. ** Topología de la propiedad**: un solo repo con múltiples paquetes vs repositorios separados

Construir un mapa de relación:
```
Proyecto A (Proyecto A)Next.js frontend) --imports-- shared-lib
Proyecto B (Proyecto B)Node.js API) --imports-- shared-lib
Proyecto C (Python ML) -independiente--
shared-lib (TipoScript) --consumed-by-- título A, B
```

### Fase 2: Configurar Configuración de Usuarios Compartidos

Crear o actualizar `~/.claude/settings.json`:

1. **Permisos globales**: comandos safe across all projects
   - `git status`, `git diff`, `git log`
   - Linteres y formateadores de lenguaje-agnóstico
2. **Global niega**: comandos peligrosos independientemente del proyecto
   - `rm -rf /`, `sudo`, `DROP DATABASE`, `git push --force`
3. ** Preferencias globales**: ajustes que se aplican en todas partes
   - Preferencias de formato de salida
   - Configuración de modelo predeterminada

Crear o actualizar `~/.claude/CLAUDE.md` (user-level):
- Identidad y preferencias de desarrolladores
- Convenciones de proyectos cruzados (estilo de compromiso, formato PR)
- Mantengase bajo 50 líneas... project-specific contenido va en proyecto CLAUDE.md

### Fase 3: Crear configuración de un producto

Para cada proyecto, generar `.claude/settings.json`:

1. ** El objeto específico permite**: build/test/lint comandos para esa pila
   - Frontend: `npm run dev`, `npm run build`, `npx next`
   - Backend: `npm run start:dev`, `npm run migrate`
   - Python: `python -m pytest`, `pip install`
2. **El proyecto niega**: proteger las trayectorias críticas de ese proyecto
3. **additionalDirectories**: si los proyectos se hacen referencia entre sí
   ```json
   {
     "additionalDirectories": ["../shared-lib"]
   }
   ```
4. **Proyecto CLAUDE.md**: project-specific context, construir comandos, estructura

No se garanticen conflictos entre user-level y project-level Ajustes.

### Fase 4: Configurar servidores MCP compartidos

Configurar servidores MCP que sirven múltiples proyectos:

1. **Identificar las necesidades comunes**: que benefician a los MCP a todos los proyectos
   - Context7: búsqueda de documentación (universal)
   - EXA: búsqueda web (universal)
   - Base de datos: compartido si los proyectos utilizan el mismo DB
2. **Configurar a nivel de usuario**: añadir MCPs compartidos a `~/.claude/settings.json`
3. **Configuración project-specific MCPs**: en la configuración de cada proyecto
4. **Evitar la duplicación**: el mismo PCM no debe configurarse en ambos niveles

## Fase 5: Configurar reglas compartidas

Crear reglas que se apliquen en los proyectos:

1. **Reglas de nivel de usuario** (en inglés)`~/.claude/rules/`): convenios de equipo
   - Presentar formato de mensaje
   - Lista de verificación de revisión del código
   - Normas de documentación
2. **Reglas de nivel de los proyectos** (artículos 2 y 5 del párrafo 1 del artículo 5 del Reglamento)`.claude/rules/`): project-specific
   - Normas de codificación para eso language/framework
   - Requisitos de prueba para ese proyecto
   - Limitaciones de arquitectura
3. **Tamaños de reglas compartidos**: para la coherencia en los nuevos proyectos

## Fase 6: Verificar la coherencia de los proyectos cruzados

Ejecutar la verificación en todos los proyectos:

1. **No hay conflictos**: user-level y project-level configuración no contradice
2. **Cobertura completa**: cada proyecto tiene CLAUDE.md + settings.json
3. **Congruencia del PCM**: acceso compartido de todos los proyectos a los PCM
4. **Congruencia absoluta**: no existen normas contradictorias en los proyectos
5. **Precisión del pago**: las direcciones adicionales apuntan a caminos válidos

---

## Formato de salida

```markdown
## Multi-Project Setup Report

**Projects:** {N} projects configured
**Relationship:** {relationship}
**Date:** {YYYY-MM-DD}

### Project Map

| Project | Type | Stack | MCP Servers | Rules |
|---------|------|-------|-------------|-------|
| {name} | {type} | {stack} | {N} | {N} |

### Shared Configuration

- User settings: ~/.claude/settings.json ({N} allows, {N} denies)
- User CLAUDE.md: ~/.claude/CLAUDE.md ({N} lines)
- Shared MCPs: {list}
- Shared rules: {list}

### Per-Project Configuration

**{project_name}:**
- .claude/CLAUDE.md: {N} lines
- .claude/settings.json: {N} allows, {N} denies
- .claude/rules/: {N} files
- additionalDirectories: {list or "none"}

### Cross-Project Verification

| Check | Status |
|-------|--------|
| No setting conflicts | PASS/FAIL |
| All projects configured | PASS/FAIL |
| MCP consistency | PASS/FAIL |
| Rule consistency | PASS/FAIL |
| Path accuracy | PASS/FAIL |
```

---

## Condiciones de veto

- *Nunca* *sobreescribir ya existente user-level Ajustes sin confirmación
- ** NUNCA** añadir caminos de proyecto a directorios adicionales sin verificar que existan
- **NO** configure servidores MCP que requieran credenciales sin el usuario que les proporcione
- ** NUNCA** modificar los ajustes de los proyectos no incluidos en la entrada

---

## Criterios de finalización

- [ ] Relaciones de proyecto analizadas y mapeadas
- [ ] Configuración de usuario compartida configurada en ~/.claude/
- [ ] Ajustes por proyecto creados para cada proyecto
- [ ] Servidores MCP compartidos configurados sin duplicación
- [ ] Reglas de proyecto cruzado establecidas
- [ ] Verificación de la coherencia aprobada
- [ ] Informe de configuración entregado
