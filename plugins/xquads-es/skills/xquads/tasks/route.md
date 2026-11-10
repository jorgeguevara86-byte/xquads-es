# Task: Route (Diagnose + Activar)

**Agente:** xquads-chief
**Comandante:** `*route` (por defecto) · `*route-to {squad}` (salta el diagnóstico)
**Consejo:** jefe de la equipo Activado con información estructurada
** Duración:**

---

## Objetivo

Tome la demanda al jefe equipo derecho y **transferir El comando**. Esta es la tarea principal del Jefe de Xquads. Termina con otro agente en control de la conversación — no con un informe.

---

Paso 1 - Diagnóstico

Corre `diagnose.md` si el usuario ya ha dicho qué equipo quiere (`*route-to`), saltar derecho al Paso 2.

** Bloqueo:** no avance con confianza  ⁇  50 sin hacer la cuestión de la inequívocación y recibir la respuesta.

---

## Passo 2 — Montar o Handoff Briefing

El líder de la equipo nunca recibe la demanda cruda. Monte este paquete (**máximo 500 fichas** — regla de compactación de mano:

```markdown
## Briefing — {squad-chief}

**Demanda:** {o que o usuário pediu, 1 frase}
**Domínio:** {domínio do catálogo}
**Objetivo final:** {artefato/resultado que precisa existir}
**Contexto conhecido:** {projeto, produto, público, restrições — SÓ o que foi dito}
**Premissas assumidas:** {inferências marcadas como [ASSUMIDO], ou "nenhuma"}
**Fora de escopo:** {o que NÃO é pra fazer}
**Task sugerida:** {task do squad, ex: diagnose.md, write-headline.md}
**Próximo squad na cadeia:** {squad seguinte, ou "nenhum"}
```

## Regras do briefing

Lo que inferiste sigue `Premissas assumidas`, marcado `[ASSUMIDO]`, nunca mezclado con `Contexto conhecido`.
- **Nunca sugáis al experto final.**Escoges el Escuadrón; el Jefe del Escuadrón elige al ATENCIÓN. No invadas su decisión.
- **`Fora de escopo` es obligatorio** cuando la demanda es ambigua — es lo que impide que el Escuadrón expanda el orden solo.
No cargues la conversación completa; carga la conclusión.

---

# Paso 3 — Anunciar y activar

Imprima el bloque de diagnóstico, luego active:

```
🎯 Diagnóstico
Demanda:    {...}
Domínio:    {...}
Squad:      {squad} → {chefe}
Confianza:  {n}% — {motivo}
Cadeia:     {...}

Ativando {chefe}...
```

# Mecanismo de activación

**Modo de la Sess** — el usuario hablará con el jefe del equipo.

Activar la habilidad de la equipo y entregar la sesión informativa como primer mensaje.
abajo trabaja en cualquier Habilidades Agente (Código de la Claude, Codex,
Gemini CLI, Cursor, Copilot, OpenCode, Goose, Amp y los siguientes:

1. Localizar la carpeta de habilidad equipo — junto a ella, en el mismo directorio
   skills (`../{squad}/`).
2. Lea el `SKILL.md` Suyo y siga las instrucciones de activación que están allí.
3. Entregue o briefing e saia de cena.

Escuadrón, habilidad...
|---|---|---|
| copy-squad | `copy-squad` | `agents/copy-chief.md` |
| copy-master | `copy-master` | `agents/copy-master-chief.md` |
| traffic-masters | `traffic-masters` | `agents/traffic-chief.md` |
| brand-squad | `brand-squad` | `agents/brand-chief.md` |
| marketing-squad | `marketing-squad` | `agents/marketing-chief.md` |
| hormozi-squad | `hormozi-squad` | `agents/hormozi-chief.md` |
| storytelling | `storytelling` | `agents/story-chief.md` |
| design-squad | `design-squad` | `agents/design-chief.md` |
| data-squad | `data-squad` | `agents/data-chief.md` |
| cybersecurity | `cybersecurity` | `agents/cyber-chief.md` |
| c-level-squad | `c-level-squad` | `agents/vision-chief.md` |
| advisory-board | `advisory-board` | `agents/board-chair.md` |
| movement | `movement` | `agents/movement-chief.md` |
| claude-code-mastery | `claude-code-mastery` | `agents/claude-mastery-chief.md` |

** Atajos equivalentes**, cuando el cliente ofrece: llame a la habilidad por nombre, o —
sólo Código Claude con instalación heredada en `~/.claude/commands/` - el `legacy_command`
catálogo (por ejemplo. `/copy-squad:agents:copy-chief`).

**Extremo Xquads:**código y desarrollo van al flujo de desarrollo
usuario (en RAPOS, `/raxos` con el Ciclo de Desarrollo de Historia). Dominio sin Escuadrón: `/squad`.

** Modo autónomo** — cuando el usuario pidió el resultado listo, sin querer hablar:

Jefe Spawn como subagente, con información en el aviso. Tipos de subagente disponibles: `copy-chief`, `design-chief`, `traffic-masters-chief`, `cyber-chief`, `data-chief`, `story-chief`, `squad-chief`, `legal-chief`, `tools-orchestrator`.

---

## Passo 4 — Sair de cena

Después de activar:

- No hagas comentarios, no resumas, no preguntes si es bueno.
- El jefe del equipo es el que dirige la conversación.
- Sólo vuelva a asumir el comando si: (a) el equipo devuelve el envío, (b) la cadena tiene el siguiente paso, o (c) el usuario le llama de vuelta.

---

Paso 5 - Jail multi-squad (sólo si es aplicable)

Si el diagnóstico apuntaba a una cadena:

1. Anunciar toda la cadena de inmediato, por lo que el usuario sabe el camino:
   ```
   Cadeia: brand-squad → hormozi-squad → copy-squad → traffic-masters
   Voy a activar uno a la vez, empezando con brand-chief.
   ```
2. Activar **apenas el primero**.
3. Cuando entre en vigor, organice una nueva reunión informativa que incorpore su producción como `Contexto conhecido` Y activa el siguiente.
4. **Nunca active dos patrones en paralelo.** Cada enlace necesita la salida del anterior.
5. El usuario puede interrumpir la cadena en cualquier momento, respeto y para.

---

## Checkpoint


|---|---|



. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

