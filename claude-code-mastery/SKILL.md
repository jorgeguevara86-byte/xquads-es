---
name: claude-code-mastery
description: >-
  Escuadrón de 8 agentes especializados en masterización de herramientas de desarrollo de
  agencias: ganchos, habilidades, subagents, MCP, plugins, equipos de agentes, ingeniería
  contextual e integración con proyectos existentes. Uso para configurar el entorno de agente,
  configuraciones de auditoría y permisos, ganchos, integración de plan MCP, escribir archivos de
  instrucciones de proyecto, trabajo descompuesto en paralelo y reducir la poda de contexto.
  CLAUDE.md, AGENTS.md, contexto rot, worktree, configuración de agente.
license: MIT
metadata:
  squad: "Claude Code Mastery Squad"
  version: "1.0.0"
  agents: "8"
  author: "Xquads by Synkra"
---

# Claude Code Mastery Squad

**Dominio:** Código Claude — Pleno de la especialización del espectro

## Cómo activar

Todas las rutas siguientes son **relativos la raíz de esta habilidad**. Lea archivos directamente desde el disco con la herramienta de lectura de su entorno. No hay dependencia del comando de barra diagonal, complemento ni de ningún cliente específico.

1. Lea `agents/claude-mastery-chief.md` Y la definición autocontenida de la cabeza de la
   : personalidad, principios, lógica de enrutamiento y límites. Adoptala.
2. Carga `data/mcp-integration-catalog.yaml` como un contexto de enrutamiento. No mostrar el contenido,
   simplemente absorberlo.
3. Salude con el `greeting` de la persona y espere la demanda.
4. Al dirigirse a un especialista, lea `agents/<especialista>.md` y asuma
   esa persona, manteniendo el informe que preparó el jefe.
5. Permanece en el equipo hasta recibir `*exit`.

## Ejecutando una tarea

Las tareas en `tasks/` son scripts ejecutables con entradas, pasos y formato de salida definidos. Lea el archivo completo antes de comenzar y siga los pasos en orden. Las tareas marcadas con `elicit: true` requieren una respuesta del usuario en cada punto de obtención; no asuma respuestas ni se salte pasos.

## Agentes

** Jefe del equipo** `agents/claude-mastery-chief.md`

**Especialistas (7)**

- `agents/config-engineer.md`
- `agents/hooks-architect.md`
- `agents/mcp-integrator.md`
- `agents/project-integrator.md`
- `agents/roadmap-sentinel.md`
- `agents/skill-craftsman.md`
- `agents/swarm-orchestrator.md`

## Tasks (26)

- `tasks/audit-integration.md`
- `tasks/audit-settings.md`
- `tasks/audit-setup.md`
- `tasks/brownfield-setup.md`
- `tasks/ci-cd-setup.md`
- `tasks/claude-md-engineer.md`
- `tasks/configure-claude-code.md`
- `tasks/context-rot-audit.md`
- `tasks/create-agent-definition.md`
- `tasks/create-rules.md`
- `tasks/create-team-topology.md`
- `tasks/diagnose.md`
- `tasks/enterprise-config.md`
- `tasks/hook-designer.md`
- `tasks/integrate-project.md`
- `tasks/mcp-integration-plan.md`
- `tasks/mcp-workflow.md`
- `tasks/multi-project-setup.md`
- `tasks/optimize-context.md`
- `tasks/optimize-workflow.md`
- `tasks/parallel-decomposition.md`
- `tasks/permission-strategy.md`
- `tasks/sandbox-setup.md`
- `tasks/setup-repository.md`
- `tasks/setup-wizard.md`
- `tasks/worktree-strategy.md`

## Workflows (3)

Secuencias multi-agente ya vinculadas. Siga las fases en el orden indicado.

- `workflows/wf-audit-complete.yaml`
- `workflows/wf-knowledge-update.yaml`
- `workflows/wf-project-setup.yaml`

## Checklists

Rote antes de la entrega. No declare la entrega lista con un artículo abierto.

- `checklists/agent-team-readiness-checklist.md`
- `checklists/brownfield-readiness-checklist.md`
- `checklists/change-checklist.md`
- `checklists/context-rot-checklist.md`
- `checklists/integration-audit-checklist.md`
- `checklists/multi-agent-review-checklist.md`
- `checklists/pre-push-checklist.md`

## Datos de referencia

- `data/ci-cd-patterns.yaml`
- `data/claude-code-quick-ref.yaml`
- `data/hook-patterns.yaml`
- `data/mcp-integration-catalog.yaml`
- `data/project-type-signatures.yaml`

## Convencoes

: los comandos del agente utilizan el prefijo `*` (`*help`, `*exit`y los declarados en la persona).
- Respuesta en español, a menos que se solicite explícitamente lo contrario.
- El jefe de escuadrón no realiza el trabajo del especialista: diagnostica y delega.
: un agente a la vez. El cambio de agente pone fin a la persona anterior.

---

*Parte de [Xquads](https://github.com/ohmyjahh/xquads-squads) — Habilidades de agente estándar abiertas.*
