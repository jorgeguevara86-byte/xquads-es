# Changelog — claude-code-mastery

Todos los cambios notables en el equipo de Mastery del Código de Claude.

## [1.0.0] - 2026-03-02

### Added
- 8 agentes especializados: claude-mastery-chief (Orión), hooks-architect (Latch), mcp-integrator (Piper), swarm-orchestrator (Nexus), config-engineer (Sigil), skill-craftsman (Anvil), project-integrator (Conduit), roadmap-sentinel (Vigil)
- 26 tareas ejecutables en todos los agentes
- 3 multi-phase workflows (wf-project-setup, wf-knowledge-update, wf-audit-complete)
- 5 archivos base de conocimiento (quick-ref, project-type-signatures, hook-patterns, ci-cd-patterns, mcp-catalog)
- 7 plantillas (5 CLAUDE.md plantillas de proyecto + 2 GitHub Actions workflows)
- 8 resúmenes de ADN mental (disler, steipete, kieran-klaassen, reuven-cohen, superclaude-org, bmad-code-org, daniel-miessler, boris-cherny)
- 1 script de validación (p.validate-setup.js)
- Arquitectura del tier: Tier 0 (Diagnosis), Tier 1 (Core Mastery), Tier 2 (Strategic & Context)
- Matriz de Handoff con routing completo entre todos los agentes
- Puente de integración AIOS-core (agentes, tareas, ganchos, asignación de configuración)

### Architecture
- Agente de entrada: claude-mastery-chief (Orión) con matriz de enrutamiento de 7 dominios
- Intereses intersectoriales: todos los agentes entienden arquitectura AIOS-core
- Fuentes de conocimiento: Código de Claude, documentos oficiales, recursos comunitarios
