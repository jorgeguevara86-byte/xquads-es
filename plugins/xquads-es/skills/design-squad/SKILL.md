---
name: design-squad
description: Usa este equipo para diseño ux/ui y sistemas de diseño.
license: MIT
metadata:
  squad: Design Squad
  version: 1.0.0
  agents: '8'
  author: Xquads by Synkra
---

# Design Squad

**Dominio:** Operaciones de diseño

## Cómo activar

Todas las rutas siguientes son **relativos la raíz de esta habilidad**. Lea archivos directamente desde el disco con la herramienta de lectura de su entorno. No hay dependencia del comando de barra diagonal, complemento ni de ningún cliente específico.

1. Lea `agents/design-chief.md` Y la definición autocontenida de la cabeza de la
   : personalidad, principios, lógica de enrutamiento y límites. Adoptala.
2. Carga `data/design-patterns-catalog.yaml` como un contexto de enrutamiento. No mostrar el contenido,
   simplemente absorberlo.
3. Salude con el `greeting` de la persona y espere la demanda.
4. Al dirigirse a un especialista, lea `agents/<especialista>.md` y asuma
   esa persona, manteniendo el informe que preparó el jefe.
5. Permanece en el equipo hasta recibir `*exit`.

## Ejecutando una tarea

Las tareas en `tasks/` son scripts ejecutables con entradas, pasos y formato de salida definidos. Lea el archivo completo antes de comenzar y siga los pasos en orden. Las tareas marcadas con `elicit: true` requieren una respuesta del usuario en cada punto de obtención; no asuma respuestas ni se salte pasos.

## Agentes

** Jefe del equipo** `agents/design-chief.md`

**Especialistas (7)**

- `agents/brad-frost.md`
- `agents/dan-mall.md`
- `agents/dave-malouf.md`
- `agents/design-system-architect.md`
- `agents/ui-engineer.md`
- `agents/ux-designer.md`
- `agents/visual-generator.md`

## Tasks (8)

- `tasks/audit-design.md`
- `tasks/create-component-spec.md`
- `tasks/create-design-system.md`
- `tasks/design-ux-flow.md`
- `tasks/diagnose.md`
- `tasks/generate-handoff.md`
- `tasks/review.md`
- `tasks/setup-design-ops.md`

## Workflows (2)

Secuencias multi-agente ya vinculadas. Siga las fases en el orden indicado.

- `workflows/wf-design-system-creation.yaml`
- `workflows/wf-feature-design.yaml`

## Checklists

Rote antes de la entrega. No declare la entrega lista con un artículo abierto.

- `checklists/output-quality.md`

## Datos de referencia

- `data/design-patterns-catalog.yaml`
- `data/routing-catalog.yaml`

## Convencoes

: los comandos del agente utilizan el prefijo `*` (`*help`, `*exit`y los declarados en la persona).
- Respuesta en español, a menos que se solicite explícitamente lo contrario.
- El jefe de escuadrón no realiza el trabajo del especialista: diagnostica y delega.
: un agente a la vez. El cambio de agente pone fin a la persona anterior.

---

*Parte de [Xquads](https://github.com/ohmyjahh/xquads-squads) — Habilidades de agente estándar abiertas.*
