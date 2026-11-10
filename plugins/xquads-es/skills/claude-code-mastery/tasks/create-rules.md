# Task: Create Conditional Rules

** ID de la lista:** CCM-CONFIG-003
**Version:** 1.0.0
**Command:** `*create-rules`
**Orquestador: ** Sigil (config-engineer)
**Purpose:** Crear reglas condicionales en `.claude/rules/` con el debido `paths:` YAML frontmatter para context-efficient cargar, garantizando reglas sólo activan cuando se están trabajando los archivos pertinentes.

---

## Overview

```
  +------------------+     +------------------+     +------------------+
  Silencio 1. Identificar Silencio -- confiar Silencio 2. Crear Regla ← Silencio 3. Escribe Regla Silencio
  Silencioso necesita Silencio Silencioso archivo con Silencio Silencio Silencio
  +------------------+     |    Frontmatter   |     +------------------+
                            +------------------+          |
                                                          v
                            +------------------+     +------------------+
                            Silencio 5. Regla de prueba Silenciosa ANTERIEDAD 4 - Validar ANTE
                            Silencioso Activación Silencioso Silencioso Regla Cargando Silencio
                            +------------------+     +------------------+
```

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
| rule_name TENEDA TENCIÓN ANTERIOR DEL PÁRRAFO DE LOS TENIDOS ANTERIENTES Nombre de archivo en caso de Kebab (por ejemplo, `api-conventions`) |
| rule_type Silencio Silencio Silencio Silencio Silencio Silencio Silencio Silencio `conditional` (por defecto) o `always-on` |
| target_paths TEN TERRITOR SON SON SON SON  auto-detected Silencio No Silencio Patrones de la guantera para carga condicional Silencio
Silencioso descripción Silenciosidad Silencioso para el usuario Silencio No Silencio Finalidad de la regla Silencio

---

## Preconditions

- .claude/ directorio existe (o se creará)
- Entendimiento de qué directories/files la norma debe aplicarse a
- No existe ningún fichero de reglas con el mismo nombre (o el usuario confirma sobreescritura)

---

## Fases de Ejecución

### Phase 1: Identifique la necesidad de Regla

Determinar qué tipo de regla crear:

1. Pregunte al usuario qué comportamiento quiere hacer cumplir o qué contexto quiere inyectar
2. Categorizar la regla:

Silencio Categoría Silencio Ejemplo Reglas Silencio Típico Senderos Silencio
|----------|---------------|---------------|
TEN API conventions TENRI Endpoint patterns, error handling, validation  `src/api/**`, `server/**` |
TENCIÓN Patrones de componentes TENIDO Patrones de reacción, estilo, props convenciones TEN `src/components/**/*.tsx` |
← Test conventions ← Patrones de prueba, estrategias de burla, cobertura  `tests/**`, `**/*.test.*` |
← Base de datos reglas vivieron patrones de migración, convenciones de consulta, RLS viv `migrations/**`, `supabase/**` |
TEN Documentación TENIDO Doc formatear, estructura README, changelog TEN `docs/**`, `*.md` |
TEN Seguridad ANTERIOR validación de entradas, patrones de austeridad, OWASP ANTE `src/auth/**`, `src/middleware/**` |
TEN Configuration TEN TEN Config file conventions, env var patterns TEN `*.config.*`, `.env.*` |
TEN siempre en TENIS convenios para todo el proyecto (no caminos: necesarios) TEN (ninguno - cargas siempre) TEN

3. Si el usuario no está seguro: escanear la estructura del proyecto y sugerir reglas basadas en directorios detectados

### Fase 2: Crear archivo de reglas con Frontmatter

1. Determinar la ruta del archivo: `.claude/rules/{rule_name}.md`
2. Para **conditional reglas**, generar el `paths:` YAML frontmatter:

```markdown
---
paths:
  - "src/api/**/*.ts"
  - "src/api/**/*.tsx"
  - "server/**/*.ts"
---
```

**Referencia del patrón de laboratorio:**
- `*` coincide con cualquier segmento de ruta
- `**` partidos cero o más segmentos de ruta (recursivo)
- `*.ts` coincide con los archivos TipoScript en el directorio actual
- `**/*.ts` coincide con los archivos de TipoScript
- `src/{api,server}/**` partidos múltiples directorios
- `**/*.{ts,tsx}` coincide con múltiples extensiones usando expansión de frenos

3. Para **always-on reglas**, omitir la primera carta completamente (no `---` bloques)
4. Crear subdirectorios si se organiza por dominio: `.claude/rules/frontend/`, `.claude/rules/backend/`

### Fase 3: Escribe contenido de Regla

Escribir el órgano de reglas siguiendo estas pautas:

1. **Empieza con un encabezado claro** explicando el propósito de la regla
2. **Utilice instrucciones imperiosas** -- dígale a Claude qué hacer, no qué considerar
3. **Sea específico y verificable** - incluir ejemplos de código cuando proceda
4. **Mantenga reglas concisas** - objetivo 20-60 líneas por archivo de reglas
5. **Utilice puntos de bala** para las reglas individuales

**Plantilla de la regla:**

```markdown
---
paths:
  - "{glob-patterns}"
---
# {Rule Title}

## Conventions

- {Specific, actionable instruction}
- {Another instruction with example}

## Patterns

When creating {X}, follow this pattern:

```{language}
{ ejemplo de código}
```

## Anti-patterns

- No hay nada específico que evitar.
- No hay otra cosa que evitar.
```

### Fase 4: Regla de validación Cargando

1. Verificar la primera yAML es válida:
   - Propio `---` delimitadores (apertura y cierre)
   - `paths:` es un array YAML (cada elemento comienza con `- `)
   - Los patrones de la globa son cadenas citadas
   - No hay caracteres de espacio blanco o de pestañas en la primera
2. Verificar el archivo se guarda en `.claude/rules/` (o un subdirectorio)
3. Compruebe que los patrones de glob coinciden con los archivos reales en el proyecto:
   - Ejecutar una prueba de partido de glob contra la estructura del proyecto
   - Advierta si los patrones coinciden con archivos cero (posiblemente incorrectos)
   - Advierta si los patrones coinciden con muchos archivos (sobre todo amplio)

## Fase 5: Activación de Reglas de Prueba

1. Explicar al usuario cómo verificar las cargas de la regla:
   - Abre un archivo que coincida con uno de los patrones de glob
   - La regla debe aparecer en el contexto de Claude para esa interacción
   - Reglas sin caminos: carga de primera en cada interacción
2. Sugerir un aviso de prueba que desencadenaría las instrucciones de la regla
3. Si la regla entra en conflicto con CLAUDE.md el conflicto:
   - Reglas y reglas CLAUDE.md instrucciones deben complementar, no contradecir
   - Si existe contradicción: recomiende eliminar la instrucción de CLAUDE.md (el archivo de reglas es más específico)

---

## Formato de salida

```markdown
## Rule Created

**File:** .claude/rules/{rule_name}.md
**Type:** {conditional | always-on}
**Lines:** {N}

### Loading Behavior

{For conditional:}
This rule loads when Claude reads files matching:
- `{pattern-1}` -- matches {N} files
- `{pattern-2}` -- matches {N} files

{For always-on:}
This rule loads on every interaction.

### Content Summary

{1-2 sentence summary of what the rule enforces}

### Verification

Open any file matching the paths above and ask Claude to follow the
conventions. The rule will be active in that context.
```

---

## Condiciones de veto

- ** NUNCA** crear una regla que contradice las instrucciones en CLAUDE.md sin marcar el conflicto y recomendar resolución.
- ** NUNCA** crear una regla condicional sin probar que sus patrones de glob coinciden con al menos un archivo existente. Advierta si cero coincide.
- **Nunca** escribir un archivo de reglas sobre 100 líneas. Dividir en múltiples reglas enfocadas en su lugar.
- **NO** incluye secretos, claves de API o credenciales en archivos de reglas (se comprometen a git).
- ############################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################### always-on regla para el contenido que debe ser condicional. Grande always-on regula el presupuesto de contexto de desechos en cada interacción.

---

## Criterios de finalización

- [ ] Necesidad de la regla identificada y categorizada
- [ ] Archivo creado en .claude/rules/ con el camino correcto
- [ ] Frontmatter YAML validado (por reglas condicionales)
- [ ] El contenido de reglas sigue la plantilla con instrucciones específicas y factibles
- [ ] Patrones de langosta probados contra la estructura del proyecto
- No hay conflictos con los existentes CLAUDE.md instrucciones
