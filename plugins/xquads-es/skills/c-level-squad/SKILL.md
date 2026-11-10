---
name: c-level-squad
description: Usa este equipo para dirección ejecutiva, estrategia y operaciones.
license: MIT
metadata:
  squad: Equipo de nivel C
  version: 1.0.0
  agents: '6'
  author: Xquads by Synkra
---

# Equipo de nivel C

**Dominio:** Liderazgo Ejecutivo y Operaciones Estratégicas

## Cómo activar

Todas las rutas siguientes son **relativos la raíz de esta habilidad**. Lea archivos directamente desde el disco con la herramienta de lectura de su entorno. No hay dependencia del comando de barra diagonal, complemento ni de ningún cliente específico.

1. Leia `agents/vision-chief.md` por completo. E a definicao autocontida do chefe do
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

**Chefe del equipo** — `agents/vision-chief.md`

**Especialistas (5)**

- `agents/caio-architect.md`
- `agents/cio-engineer.md`
- `agents/cmo-architect.md`
- `agents/coo-orchestrator.md`
- `agents/cto-architect.md`

## Tasks (7)

- `tasks/design-operations.md`
- `tasks/diagnose.md`
- `tasks/evaluate-technology.md`
- `tasks/plan-fundraise.md`
- `tasks/plan-go-to-market.md`
- `tasks/review.md`
- `tasks/set-vision.md`

## Workflows (2)

Secuencias multi-agente ya vinculadas. Siga las fases en el orden indicado.

- `workflows/wf-board-presentation.yaml`
- `workflows/wf-strategic-planning.yaml`

## Checklists

Rote antes de la entrega. No declare la entrega lista con un artículo abierto.

- `checklists/output-quality.md`

## Datos de referencia

- `data/executive-frameworks.yaml`
- `data/routing-catalog.yaml`

## Convencoes

: los comandos del agente utilizan el prefijo `*` (`*help`, `*exit`y los declarados en la persona).
- Respuesta en español, a menos que se solicite explícitamente lo contrario.
- El jefe de escuadrón no realiza el trabajo del especialista: diagnostica y delega.
: un agente a la vez. El cambio de agente pone fin a la persona anterior.

---

*Parte de [Xquads](https://github.com/ohmyjahh/xquads-squads) — Habilidades de agente estándar abiertas.*
