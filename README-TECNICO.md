# Escuadrones Xquads

**Las mentes más brillantes trabajando para ti.**

15 escuadrones de agentes de IA especializados (**183 agentes**) con flujos de trabajo, tareas y
Listas de verificación listas para usar.

Distribuidos en el estándar abierto **[Agent Skills](https://agentskills.io)**, para que funcionen
en el agente que ya utiliza: Claude Code, Codex, Gemini CLI, Cursor, GitHub Copilot, VS Code,
OpenCode, Goose, Amp, Factory, Kiro, Roo Code y más de 30 clientes compatibles.

## Instalación

Un comando, en cualquier máquina:

```bash
bash <(curl -sL https://raw.githubusercontent.com/jorgeguevara86-byte/xquads-es/main/install.sh)
```

El instalador detecta qué agentes ha instalado y hace que los equipos estén disponibles en todos
ellos a la vez. Reinicia el agente y pregunta en lenguaje natural:

> "usa xquads para configurar la campaña de lanzamiento"

### Otras formas

```bash
bash install.sh --list                     # ver os squads disponíveis
bash install.sh copy-squad traffic-masters # instalar só o que interessa
bash install.sh --project                  # instalar neste projeto (.agents/skills)
bash install.sh --copy                     # copiar em vez de criar symlink
bash install.sh --uninstall                # remover
```

La instalación global utiliza `~/.agents/skills/` como fuente de verdad: el directorio neutral que
se ha definido el estándar de Habilidades del Agente. **Codex, Gemini CLI y Cursor leen este directorio directamente**, sin
sin configuración. Los clientes que sólo miran la carpeta ellos mismos reciben un enlace simbólico que apunta
por ahí. En ambos casos, actualizar una vez los actualiza a todos.

En el Codex, después de instalar: `/skills` enumera, `$copy-squad` invoca, o simplemente describe el
problema que elige por descripción.

> **Acerca del costo del contexto.** Cada agente lleva el nombre y la descripción de cada habilidad
> instalado al inicio de la sesión. Los 15 escuadrones suman alrededor de 2.400 fichas permanentes. no lo es
> muchas, pero si solo usas dos o tres, instálalas solo; el gerente general te avisa cuando una
> la ruta no está instalada y sugiere la alternativa más cercana. El cuerpo completo de un escuadrón.
> (personas, tareas, flujos de trabajo) solo ingresa al contexto cuando realmente está activado.

Instalación por proyecto escribe en `.agents/skills/`. Confirma esta carpeta y todo el equipo.
hereda los equipos junto con el repositorio.

### ¿Has utilizado los comandos de barra diagonal de Claude Code?

Sigue funcionando, no se ha roto nada. Para reinstalar también en este formato:

```bash
bash install.sh --claude-commands
```

## Empieza aquí: el Jefe General

No necesitas saber a qué plantilla convocar. **Xquads Chief (Xander 🎯)** es la puerta de entrada
único: describe el problema en lenguaje natural, identifica la actividad, elige la
escuadrón
y activa a su jefe con una sesión informativa lista.

```
Describes el problema.
        │
        ▼
  DIAGNÓSTICO.......clasifica el dominio y calcula la confianza
        │
        ├── confianza < 50% ── ► Una pregunta de desambiguación
        │
        ▼
  BRIEFA ........... transferencia estructurada (máximo 500 tokens)
        │
        ▼
  ACTIVA ............. el líder del escuadrón se hace cargo de la conversación
```

Nunca hace el trabajo, simplemente identifica y delega. Cuando la demanda cruza dominios,
ensambla una cadena multi-squad y activa un eslabón a la vez.

Detalles en [`xquads/README.md`](xquads/README.md).

## Plantillas disponibles

| Plantilla | Agentes | Enfoque |
|-------|---------|------|
| Consejo Asesor | 11 | Asesores estratégicos (Ray Dalio, Charlie Munger, Naval Ravikant...) |
| Equipo de marca | 15 | Branding y posicionamiento (David Aaker, Marty Neumeier, Al Ries...) |
| Equipo de nivel C | 6 | Liderazgo ejecutivo (CEO, CTO, CMO, COO, CIO, CAIO) |
| Dominio del código Claude | 8 | Configuración del agente: ganchos, MCP, subagentes, contexto |
| Copiar maestro | 33 | Redacción publicitaria 2.0: persuasión, presentación, negociación, SaaS |
| Copiar equipo | 23 | Redacción publicitaria (Gary Halbert, Eugene Schwartz, David Ogilvy...) |
| Ciberseguridad | 15 | Seguridad ofensiva y defensiva |
| Equipo de datos | 7 | Análisis, crecimiento y comunidad (Sean Ellis, Avinash Kaushik...) |
| Equipo de diseño | 8 | UX/UI y sistemas de diseño (Brad Frost, Dan Mall...) |
| Equipo Hormozi | 16 | Negocios y escala (marcos Alex Hormozi) |
| Equipo de marketing | 5 | Campaña integrada: lo mejor de cada disciplina |
| Movimiento | 7 | Construyendo movimientos y comunidades |
| Narración | 12 | Narrativa y storytelling (Joseph Campbell, Oren Klaff...) |
| Maestros del tráfico | 16 | Tráfico pago y medios (Pedro Sobral, Kasim Aslam...) |
| Jefe de Xquads | 1 | Gateway: diagnósticos y rutas hacia el equipo adecuado |

## Estructura de cada plantilla

```
squad-name/
├── SKILL.md # Punto de entrada (valor predeterminado de Habilidades del agente)
├── squad.yaml # Manifiesto: agentes, tareas, flujos de trabajo
├── agentes/ # Personas autónomas
├── tareas/ # Tareas ejecutables con inputs/outputs
├── flujos de trabajo/# Flujos de trabajo multi-agente
├── listas de verificación/ # Listas de verificación de calidad
├── config/ # Niveles, iconos y metadatos
└── datos/# Marcos y catálogos de referencia
```

## Desenvolvimento

Los `SKILL.md` son **gerados**, no editados a mano:

```bash
python3 scripts/gerar-skills.py     # regera os 15 SKILL.md
python3 scripts/validar-skills.py   # valida contra a spec Agent Skills
```

Las convenciones para contribuyentes se encuentran en [`AGENTS.md`](AGENTS.md).

## Dashboard

Ver todos los agentes, biografías y especialidades en
[xquads.vercel.app/xquads](https://xquads.vercel.app/xquads).

---

**Xquads de Synkra** · MIT
