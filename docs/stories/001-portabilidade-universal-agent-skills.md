# Story 001 — Portabilidade universal do Xquads via Agent Skills

**Epoto:** Distribución de Xquads
**Estatus:** Hecho
** Creado en:** 2026-09-25
** Agente creador: ** @master

---

# Descripción #

Hoy Xquads sólo está instalado en el Código Claude. README envía copiando los equipos a
`~/.claude/commands/`, directorio no otra herramienta de agencia lee, y la routing
do Xquads Chief usa a sintaxe `/squad:agents:agente`, que é namespacing exclusivo do
Código Claude. Usuarios de Codex, Gemini CLI, Cursor, Copilot y similares no pueden instalar
O usar cualquier cosa.

El contenido mismo (371 archivos de personas, tareas, flujos de trabajo, listas de verificación y catálogos) es
Marcado y YAML puro, por lo tanto ya portátil. La cerradura es exclusivamente embalaje
y distribución.

La solución es adoptar el estándar abierto ** Habilidades de la Agencia** (agentskills.io), publicado por
Antrópico en dez/2025 y adoptado por 40+ clientes de agencia, incluyendo Codex, Gemini CLI,
Cursor, GitHub Copilot, Código VS, OpenCode, Goose, Amp, Factory e Kiro. Cada escuadrón vira uma
habilidad: carpeta con `SKILL.md` en root (frontmatter) `name` + `description`más directorios
Auxiliar que ya existen.

# Valor de negocio

Multiplica el público instalado de Xquads. Hoy el producto está restringido a los usuarios de un
sólo herramienta; con el cambio comienza a funcionar en cualquier cliente compatible con el Agente
Habilidades, sin contenido de reescritura. También elimina la fricción manual de instalación a través de `cp -r`,
reemplazado por un solo comando.

# Criterios de aceptación

-**AC1** - Cada uno de los 15 escuadrones tiene uno `SKILL.md` válido en root con frontmatter
  que contiene `name` (kebab-case, igual al nombre de carpeta, max. 64 chars) y `description`
  (máx. 1024 chars, describiendo lo que haces y cuándo utilizar).
- ¿Qué? `SKILL.md` de cada quad instruye la activación de la forma de herramienta agnóstica:
  lee los archivos por **caminho relacionado con la raíz de la habilidad** (por ejemplo: `agents/copy-chief.md`),
  nunca por path absoluto `~/.claude/...` nem por slash command `/squad:agents:x`.
- ****AC3* `SKILL.md` del quad `xquads` (jefe general) router para otros equipos sin
  dependiendo de comandos de slash, degradando con advertencia cuando no se instala un equipo.
- Hay un `install.sh` en la raíz del repo: detecta qué clientes agentes
  están presentes en la máquina, se instala en `~/.agents/skills/` como fuente de verdad,
  y conecta los otros destinos (`~/.claude/skills/`, `~/.codex/skills/`, `~/.gemini/skills/`,
  `~/.cursor/skills/`Por simlink.
**AC5** — El instalador acepta la instalación selectiva (`install.sh copy-squad brand-squad`)
  e instalación por proyecto (`--project`, grabación en `.agents/skills/`).
**AC6** - La instalación heredada del Código de Claude a través de `~/.claude/commands/` Vamos.
  Funciona, sin descomponer a quien ya lo ha instalado.
- Hay un `AGENTS.md` en la raíz del repo, para clientes que leen este archivo.
- ¿Qué? `README.md` documento instalación universal, lista de herramientas
  compatible y reemplaza las viejas instrucciones de `cp -r`.
-**Cálculo* `SKILL.md` transmisor generado en validación automatizada de las reglas
  frontmatter da spec (nombre kebab-case sin hifeno inicial/final o doble, coincide con el nombre
  carpeta; descripción no vacía y dentro del límite).

## Escopo

### IN
- Generación de los 15 archivos `SKILL.md` (uno por equipo)
- `install.sh` universal con detección de clientes
- `AGENTS.md` na raiz
- Reescribir `README.md` principal
- Corrección de la ruta absoluta y referencias a comandos de corte en los archivos equipos
  `xquads` (`command-entry.md`, `agents/xquads-chief.md`, `tasks/route.md`,
  `tasks/diagnose.md`, `data/routing-catalog.yaml`, `squad.yaml`)
- Script de validación del `SKILL.md`

### OUT
- Reescribir el contenido de las personas, tareas y flujos de trabajo de las equipos (ya es agnóstico)
- Cambiar el equipo `claude-code-mastery` sobre el fondo del contenido (se trata de Claude Code por
  a)
- Alterar o dashboard Next.js em `~/Desktop/Projetos/xquads` (o ZIP de descarga é regerado
  em story separadas)
- Publicar em registries de skills de terceiros
- `git push` ou desplegable

# Dependencias

Es sólo hasta la espectro de la Agente Skills, ya estable y pública.

## Complexidade

**M** — alto volumen de archivos, pero la transformación es mecánica y manejable por script.
Trabajo de prueba se centra en 6 archivos equipos `xquads` y `install.sh`.

## Riscos


|---|---|---|
 `~/.claude/commands/` intacto y aditivo; el instalador sólo añade
 `description` Do `squad.yaml` (dominio + palabras clave), que ya ha sido curado
 `~/xquads-squads` y `~/Desktop/Projetos/xquads/squads` `~/xquads-squads`) y sincronizar para la historia separada
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
 `$HOME` no estándar rompe el instalador `set -euo pipefail` |

# Los criterios de Done

- [x] Los 15 `SKILL.md` existen y pasan en el validador
- [x] `install.sh` rueda limpia en macOS con zsh y es idempotente (rodar 2x no duplica)
- [x] Instalación selectiva y `--project` trabajo
- [x] `AGENTS.md` y `README.md` actualizada
- [x] Cero camino `~/.claude/` codificado por foros do pelotón `claude-code-mastery`
- [x] Cero referencia a `/squad:agents:` en las instrucciones de activación agnóstica
- Planta de Legacy en `~/.claude/commands/` comprobado como intacto
- [x] Nada cometido sin revisión; ningún empuje sin autorización explícita del propietario

# Lista de archivos

### Criados
- `install.sh` — instalador universal con detección de clientes
- `AGENTS.md` - instrucciones de sustitución de agentes
- `scripts/gerar-skills.py` - generador de SKILL.md de los manifiestos
- `scripts/validar-skills.py` - Validador contra la piel del agente de la especie
- `scripts/testar.sh` — suite de 33 pruebas de embalaje
- `docs/stories/001-portabilidade-universal-agent-skills.md` —Esta historia
- `.gitignore` - Construcción y desechos de sistemas
- `advisory-board/SKILL.md`
- `brand-squad/SKILL.md`
- `c-level-squad/SKILL.md`
- `claude-code-mastery/SKILL.md`
- `copy-master/SKILL.md`
- `copy-squad/SKILL.md`
- `cybersecurity/SKILL.md`
- `data-squad/SKILL.md`
- `design-squad/SKILL.md`
- `hormozi-squad/SKILL.md`
- `marketing-squad/SKILL.md`
- `movement/SKILL.md`
- `storytelling/SKILL.md`
- `traffic-masters/SKILL.md`
- `xquads/SKILL.md`

### Modificados
- `README.md` — instalación universal, escala corregida (183 agentes)
- `xquads/squad.yaml` — `command` -> `legacy_command` en rutas internas
- `xquads/data/routing-catalog.yaml` — Ídem, nota de activación más agnóstica
- `xquads/agents/xquads-chief.md` — protocolo de activación sin comando de barras
- `xquads/tasks/route.md` — activando mesa por habilidad
- `xquads/tasks/diagnose.md` —dijo un comando de diagnóstico sem slash
- `xquads/command-entry.md` - marcado como formato legado

No modificado intencionalmente
- archivos de 183 persona en `*/agents/` - ya agnóstico
- Como tareas, flujos de trabajo e listas de verificación dos escuadrones de demais — ja eram agnosticas
- El contenido de `claude-code-mastery/` - habla del Código de Claude por tema

# Found out of scope

- `copy-master/data/persuasion-psychology.yaml` No y válido YAML (línea 177:
  `sugarman_30_triggers` Mezcla de mapping y secuencia). **Pre-existing**, entró en la
  commit dcb32f3. Registrado como tarea separada, no corregido aquí por ser
  fuera del ámbito declarado de esta historia.

##QA Loop — iteration 1 (2026-09-27)

**Carta:**Comprobar la documentación oficial de cada cliente después de la publicación.

### Defeito

El instalador creado `~/.codex/skills/` Y entonces él daría vueltas a las equipos allí.
directorio.** La documentación de OpenAI sólo lista `.agents/skills` (proyecto y repo),
`$HOME/.agents/skills` (personal) y `/etc/codex/skills` (admin)

Severidad: Bajo. No se rompió nada — el centro `~/.agents/skills` Era el camino correcto y
Codex encontró las habilidades allí. El efecto era una carpeta de huérfanos que ningún cliente abre y
un mensaje de éxito engañoso ( " Codex" sugirió que el simlink era lo que hizo que funcionara).

Mismo imprecisión, menor, en Gemini CLI y Cursor: ambos leen el hub **e** el directorio adecuado,
con el hub que tiene precedencia, entonces el simlink fue redundante.

Corrección

- Cuadro `DESTINOS` ha ganado la columna "lee el centro". Cualquiera que lea no recibe su propio directorio;
  la salida continúa diciendo `Codex — lê o hub direto`Eso es lo que pasa.
- `DESTINOS_OBSOLETOS` Holds `~/.codex/skills`, `~/.gemini/skills` y `~/.cursor/skills` Ed
  Desinstalación rutinaria, para limpiar el residuo del que instaló la versión anterior.
- README comenzó a explicar la diferencia entre leer el centro y recibir el enlace, y documenta la
  invocación en Codex (Invocación en Codex)`/skills`, `$copy-squad`).

### Testes

Suite era de 33 a 40 afirmaciones. Las nuevas cubiertas: ausencia de carpetas inútiles, presencia
de las habilidades en el centro, el texto de salida y la limpieza del residuo de la versión antigua.

Un falso negativo apareció y fue corregido en la prueba misma: `grep -q` tubo en
Primer partido y SIGPIPE estaba derribando el `install.sh` de los países `pipefail`La prueba ahora captura el
el mismo patrón ya me había engañado una vez con `head`.

### Verdict

**PASS** — 40/40.

Resultados de QA

**Gate:** PASS
* Agente: * @calidad
**Data:** 2026-09-25

## 7 controles de calidad


|---|---|---|
 `install.sh` y los dos scripts Python. `shellcheck` y `ruff` no se instalan en esta máquina, por lo que el forro automatizado **não** fue ejecutado.
 33/33 Ed `scripts/testar.sh`, corriendo en casa desechable en el bajo macOS 3.2.
3 . Criterios de aceptación . OK - AC1 a AC9 comprobó uno por uno . . .
`xquads-chief.md`Cero tareas cambiaron fuera de la equipo. `xquads`. El formato legado del Código de Claude instala y desinstala. .
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . `SKILL.md` debajo de 500 líneas (máx. 128).
 `set -euo pipefail`; todos `rm -rf` con `${var:?}`; expansión cero sin comillas; no `eval`, sin pipe-to-shell, ningún secreto codificado; directorio temporal eliminado en la trampa EXIT; guarda que preserva habilidades de terceros con el nombre de coincidencia.
 AGENTS.md y la historia actualizada; `command-entry.md` marcado como legado.

### Issues

```yaml
issues:
  - severity: low
    category: tests
    description: "descomposición y desvío que falta en la máquina - el recubrimiento estático no gira" 
    recommendation: "Instalar shellcheck y ruff y añadir ambos a scripts/testar.sh" 
  - severity: low
    category: code
    description: "Instalación remota depende de git; no hay retroceso para tarball" 
    recommendation: "Adicionar caída de la vía curl do tarball do GitHub quando git faltar" 
  - severity: low
    category: performance
    description: "15 equipos añadir ~2.4k fichas de metadatos permanentes en contexto" 
    recommendation: "Mezclado por documentación. La instalación selectiva ya está soportada." 
```

## Bloqueadores para publicación (require commit y push, no autorizado)

1. **`marketing-squad/` nunca se ha cometido.** No se ha rastreado en el sitio y no está
   `origin/main`Consecuencia directa: instalación remota (instalación remota)`curl | bash`, que clona
   repositorio) entrega **14 equipos, no 15**, y ruta `marketing-squad` del Jefe de la Generalidad
   no está disponible para todos los que instalan desde fuera de esta máquina.
2. **`.next/` está comprometido con el repositorio público** — un proyecto de construcción de artefactos
   Next.js que no pertenecen a un reposo de habilidades. Añadido `.gitignore` y retirado de
   índice; la eliminación sólo va después de la confirmación.

Tampoco fue presentado por esta historia, pero la primera invalida AC4 en la práctica
para usuarios remotos. La historia permanece Done as to code; a **publicação** Depende de
autorização do dono para comprometer e push.

Fuera del alcance de esta historia

- `copy-master/data/persuasion-psychology.yaml` no es válido YAML. **Pre-existing**
  (commit dcb32f3), no ingresado aquí. Registrado como tarea separada.
  las pruebas actuales no validan YAML de `data/` — la tarea separada también lo abarca.

# La autorización pendiente del propietario

Nada ha sido cometido, nada ha sido enviado, la instalación.*não** fue ejecutado en el medio ambiente
  usuario real — todas las pruebas se realizaron en INIC descartable.

# Change Log


|---|---|---|
Silencio 2026-09-25 Silencio @mestre Silencio Historia criada (Draft) Silencio
 10/10 - GO. Proyecto de Estado - Confeccionado

Silencio 2026-09-25 Silencio @qualidade Silencio QA gate PASS (Página de inicio)7/7, 3 números bajos). Estado InReview - Propiedad Done Silencio
 origin/main (b4610d0) con el permiso del propietario
.codex/skills) |

40/40) |
