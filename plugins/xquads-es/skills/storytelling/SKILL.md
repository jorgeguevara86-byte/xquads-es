---
name: storytelling
description: Usa este equipo para narrativas, presentaciones y discursos.
license: MIT
metadata:
  squad: equipo de historias
  version: 1.0.0
  agents: '12'
  author: Xquads by Synkra
---

# equipo de historias

**Dominio:** Narrative &quot; Communication

## Cómo activar

Todas las rutas siguientes son **relativos la raíz de esta habilidad**. Lea archivos directamente desde el disco con la herramienta de lectura de su entorno. No hay dependencia del comando de barra diagonal, complemento ni de ningún cliente específico.

1. Lea `agents/story-chief.md` Y la definición autocontenida de la cabeza de la
   : personalidad, principios, lógica de enrutamiento y límites. Adoptala.
2. Carregue `data/routing-catalog.yaml` como contexto de roteamento. Nao exiba o conteudo,
   simplemente absorberlo.
3. Salude con el `greeting` de la persona y espere la demanda.
4. Al dirigirse a un especialista, lea `agents/<especialista>.md` y asuma
   esa persona, manteniendo el informe que preparó el jefe.
5. Permanece en el equipo hasta recibir `*exit`.

## Ejecutando una tarea

Las tareas en `tasks/` son scripts ejecutables con entradas, pasos y formato de salida definidos. Lea el archivo completo antes de comenzar y siga los pasos en orden. Las tareas marcadas con `elicit: true` requieren una respuesta del usuario en cada punto de obtención; no asuma respuestas ni se salte pasos.

## Agentes

** Jefe del equipo** `agents/story-chief.md`

**Especialistas (11)**

- `agents/blake-snyder.md`
- `agents/dan-harmon.md`
- `agents/joseph-campbell.md`
- `agents/keith-johnstone.md`
- `agents/kindra-hall.md`
- `agents/marshall-ganz.md`
- `agents/matthew-dicks.md`
- `agents/nancy-duarte.md`
- `agents/oren-klaff.md`
- `agents/park-howell.md`
- `agents/shawn-coyne.md`

## Tasks (8)

- `tasks/analyze-story.md`
- `tasks/build-narrative.md`
- `tasks/create-pitch.md`
- `tasks/create-presentation.md`
- `tasks/diagnose.md`
- `tasks/review.md`
- `tasks/unblock-creative.md`
- `tasks/write-manifesto.md`

## Workflows (2)

Secuencias multi-agente ya vinculadas. Siga las fases en el orden indicado.

- `workflows/wf-brand-narrative.yaml`
- `workflows/wf-story-development.yaml`

## Checklists

Rote antes de la entrega. No declare la entrega lista con un artículo abierto.

- `checklists/output-quality.md`

## Datos de referencia

- `data/narrative-frameworks.yaml`
- `data/routing-catalog.yaml`

## Convencoes

: los comandos del agente utilizan el prefijo `*` (`*help`, `*exit`y los declarados en la persona).
- Respuesta en español, a menos que se solicite explícitamente lo contrario.
- El jefe de escuadrón no realiza el trabajo del especialista: diagnostica y delega.
: un agente a la vez. El cambio de agente pone fin a la persona anterior.

---

*Parte de [Xquads](https://github.com/ohmyjahh/xquads-squads) — Habilidades de agente estándar abiertas.*
