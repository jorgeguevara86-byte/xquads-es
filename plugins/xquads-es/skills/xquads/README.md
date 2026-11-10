# Xquads Chief — O Chefe Geral

> Un puerto de entrada de Xquads individuales. Usted describe el problema; identifica la actividad, elige el equipo y **ativa el cabeza del quad**.

```
/xquads
```

El Jefe de Xquads (**Xander**, meta-orquestrador — es un nivel sobre los cabezas de la equipo. Él no escribe copia, no dibuja, no analiza y no programa. Él hace tres cosas: **diagnostica → briefa → activo**.

---

# Cómo funciona #

```
Describes el problema.
        │
        ▼
  [1] DIAGNOSE......... extrae la demanda real, clasifica el dominio, calcula la confianza
        │
        . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
        │                                       │
        ▼◄──────────────────────────────────────┘
  [2] HAS DECIDED AS Seguidos ................... multi-squad
        │
        ▼
  [3] RESUMEN ...... despachado estructurado (máximo 500 fichas)
        │
        ▼
  [4] ATIVA.........{squad}:agentes:{chefe} asumir un conversa
        │
        ▼
  [5] Sáquense de CENA... el jefe de la brigada conduce de aquí en adelante
```

---

# Mapa de la ruta


|---|---|---|---|
Silencio, teléfono, teléfono, correo electrónico copy-squad | copy-chief | 23 |
 copy-master | copy-master-chief | 33 |
 traffic-masters | traffic-chief | 16 |
 brand-squad | brand-chief | 15 |
 marketing-squad | marketing-chief | 5 |
 hormozi-squad | hormozi-chief | 16 |
TENRI Narrativa, pitch, apresentação, manifesto TENISTERIO TENIDO story-chief | 12 |
TENCIÓN UX, UI, sistema de diseño TENIDO design-squad | design-chief | 8 |
 data-squad | data-chief | 7 |
TENEDA, AppSec, incidente, auditoria TENED Cybersecurity TENED cyber-chief | 15 |
 c-level-squad | vision-chief | 6 |
 advisory-board | board-chair | 11 |
 movement-chief | 7 |
Silencioso Código de Claude, ganchos, MCP, agentes viv claude-code-mastery | claude-mastery-chief | 8 |
 `/raxos` - CENTRO Obligatorio
 `/squad` - crea un nuevo

---

## Comandos


|---|---|
| `*route` ** Estándar.** Diagnósticos y activa la cabeza de la equipo.
| `*diagnose` 
| `*route-to {squad}` 
| `*chain`  multi-squad |
| `*squads` 
| `*review` 
| `*help` 

---

# Multi-Squad Chains

Cuando la demanda cruza dominios, el jefe monta una cadena y activa **um enlace a la vez** — la salida de cada equipo se convierte en contexto de la siguiente.


|---|---|

TEN TERRITORIO Marca nova TENISTERIO DE LA TERRITORIA →

 c-level → diseño → raxos
Silencio Turnaround de métrica tención datos → tráfico → copy 

> Estudio de campaña? Prefiere el **marketing-squad** (ya integrada) a toda la cadena.

---

Desambiguation

El jefe no acepta la etiqueta que le diste... él revisa el verdadero problema.


|---|---|---|
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
Silencio "Preciso de um nome" Silencio marca ou headline? Silencio marca · copy Silencio
"¿Haré X o Y?" advisory-board · c-level |
← "Meu site tem problema" Silencio, UX ou invasão? Silencioso raxos · diseño · ciberseguridad TENIDO

Si la confianza es inferior al 50%, lo hace **uma** Pregunta — nunca dos.

---

## Limites (por design)

- Nunca realiza el trabajo - no "sólo un borrador"
Nunca escriba código (el código va a `/raxos`, con la SDC obligatoria)
-
Nunca activa dos jefes en paralelo
- Nunca inventa el quad fuera del catálogo
-
-

---

## Instalación

Un comando, en cualquier agente compatible con [Agent Skills](https://agentskills.io) —
Código Claude, Codex, Gemini CLI, Cursor, GitHub Copilot, Código VS, OpenCode y otros:

```bash
bash <(curl -sL https://raw.githubusercontent.com/jorgeguevara86-byte/xquads-es/main/install.sh)
```

Entonces usted sólo pide en lenguaje natural ("utiliza los xquads para montar la campaña") o invocar la
habilidad `xquads` No hay Codex, `/skills` lista e `$xquads` invoca.

El jefe general sólo activa los equipos que se instalan. Instalar todos (el predeterminado de
comando arriba) deja el enrutamiento completo; si usted instaló sólo unos pocos, advierte cuando un
la ruta no está disponible y ofrece la alternativa más cercana.

> **No vuelvas a llamar la carpeta. **Su nombre es el nombre de la habilidad — `xquads` Debes continuar.
> `xquads`.

<details>
==Referencias====Enlaces externos==

Sólo para aquellos que ya usaban Xquads para `~/.claude/commands/` Y quieres seguir ese camino.
necesaria: la instalación anterior ya cubre el Código Claude.

```bash
bash install.sh --claude-commands
```

</details>

## Componentes

- 1 agente** xquads-chief (Tierra - 1, meta-orquestrador)
**3 tareas** — diagnosticar, trazar, revisar
- **1 flujo de trabajo** wf-route-to-squad (6 fases com gates e vetos)
* 1 lista de verificación* output-quality (Puerta de ruta, no disponible)
- **1 archivo de datos** routing-catalog (14 equipos, 8 tie-breakers, 5 cadenas)

## Requisitos

- Un agente compatible con [Esquías de Agente](https://agentskills.io)
- Git, para el instalador.
- Los equipos que desea que se active, instalado
