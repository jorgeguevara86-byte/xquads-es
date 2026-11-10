---
name: xquads
description: Usa este equipo para diagnóstico y selección del equipo apropiado.
license: MIT
metadata:
  squad: Jefe de Xquads
  version: 1.0.0
  agents: '1'
  author: Xquads by Synkra
---

# Jefe de Xquads

**Dominio:** Meta-orquestración - puerto de entrada único de los 14 equipos Xquads

## Cómo activar

Todas las rutas siguientes son **relativos la raíz de esta habilidad**. Lea archivos directamente desde el disco con la herramienta de lectura de su entorno. No hay dependencia del comando de barra diagonal, complemento ni de ningún cliente específico.

1. Lea `agents/xquads-chief.md` Y la definición autocontenida de la cabeza de la
   : personalidad, principios, lógica de enrutamiento y límites. Adoptala.
2. Carregue `data/routing-catalog.yaml` como contexto de roteamento. Nao exiba o conteudo,
   simplemente absorberlo.
3. Salude con el `greeting` de la persona y espere la demanda.
4. Al dirigirse a un especialista, lea `agents/<especialista>.md` y asuma
   esa persona, manteniendo el informe que preparó el jefe.
5. Permanece en el equipo hasta recibir `*exit`.

## Ejecutando una tarea

Las tareas en `tasks/` son scripts ejecutables con entradas, pasos y formato de salida definidos. Lea el archivo completo antes de comenzar y siga los pasos en orden. Las tareas marcadas con `elicit: true` requieren una respuesta del usuario en cada punto de obtención; no asuma respuestas ni se salte pasos.

## Squads que ele ativa

Silencio Dominio da demanda Silencio Habilidad ativar Silencio
|---|---|
← Copiado, titular, VSL, email, carta de vendas TEN `copy-squad` |
 `copy-master` |
← Trafego pago, Meta Ads, Google Ads, escalada, seguimiento Silencioso `traffic-masters` |
 `brand-squad` |
 `marketing-squad` |
 `hormozi-squad` |
 `storytelling` |
TEN UX, UI, sistema de diseño, componente, handoff TEN `design-squad` |
 `data-squad` |
 `cybersecurity` |
 go-to-market, captura, decisión ejecutiva `c-level-squad` |
 `advisory-board` |
 `movement` |
TENCIÓN Hooks, MCP, subagents, configuracao do agente TEN `claude-code-mastery` |

#Como ativar um squad. # Habilidades nao tem namespacing por slash command, e cada
cliente expone la invocación de una manera. El procedimiento siguiente funciona en todos:

1. Localizar la carpeta de habilidad cuadrada. Está al lado de esto, en el mismo directorio
   de las aptitudes (`../<squad>/`), o en el directorio de habilidades ambientales.
2. Lea el `SKILL.md` el cuadrado y seguir las instrucciones de activación que están allí.
3. Entregue ao chefe do squad o briefing de handoff (maximo 500 fichas) e saia de
   El jefe del Escuadrón lleva de allí en adelante.

Si el cliente muestra las habilidades por nombre (comandancia, menú o llamada implícita),
Use este camino —y equivalente y más directo.

√ **No se instala la casilla = ruta no disponible.** Antes de activar, confirme que la carpeta
√≥n de la plaza existe. Si no existe, dígale al usuario, indique cómo instalar
> (`install.sh <squad>`) y ofrece la alternativa más cercana entre los instalados.
Nunca finjas haber activado un Escuadrón perdido.

**Desarrollo y código de software de Xquads**. Esto va al ámbito de la Xquads
flujo de desarrollo de usuarios (en el RAPOS, Story Development Cycle), nunca
Para um pelotón de marketing.

## Agentes

** Jefe del equipo** `agents/xquads-chief.md`

## Tasks (3)

- `tasks/diagnose.md`
- `tasks/review.md`
- `tasks/route.md`

## Workflows (1)

Secuencias multi-agente ya vinculadas. Siga las fases en el orden indicado.

- `workflows/wf-route-to-squad.yaml`

## Checklists

Rote antes de la entrega. No declare la entrega lista con un artículo abierto.

- `checklists/output-quality.md`

## Datos de referencia

- `data/routing-catalog.yaml`

## Convencoes

: los comandos del agente utilizan el prefijo `*` (`*help`, `*exit`y los declarados en la persona).
- Respuesta en español, a menos que se solicite explícitamente lo contrario.
- El jefe de escuadrón no realiza el trabajo del especialista: diagnostica y delega.
: un agente a la vez. El cambio de agente pone fin a la persona anterior.

---

*Parte de [Xquads](https://github.com/ohmyjahh/xquads-squads) — Habilidades de agente estándar abiertas.*
