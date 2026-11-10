# Claude Code Mastery Squad

> Experiencia de espectro completo en Claude Code: ganchos, habilidades, subagents, MCP, plugins, equipos de agentes, personalización, integración y conocimiento de hoja de ruta.

**Versión:** 1.0.0 Silencio **Creado:** 2026-03-01 Silencio **Total:** 8 agentes, 6.741 líneas

## Squad Architecture

```
                        Orión (Orquestador)
                     claude-mastery-chief [Tier 0]
                              |
            ┌─────────┬───────┴───────┬──────────┐
            |         |               |          |
    ┌───────┴──┐  ┌───┴────┐  ┌──────┴───┐  ┌───┴──────┐
    Silencio Silencio Silencio Silencio Silencio Silencio Silencio Silencio Silencio Silencio Silencio
    ← ← TENED TENED TENED TENED TENED TENIS TENIS TENIS TENIS
    Silencio Tier 1 Silencio Silencio Silencio Tier 1 Silencio Silencio Silencio Silencio Silencio Tier 1 Silencio
    └──────────┘  └────────┘  └──────────┘  └──────────┘
            |         |               |
    ┌───────┴──┐  ┌───┴────┐  ┌──────┴───┐
    Anvil . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
    Silencios de Habilidades Silencio Silencio Silencio
    Silencio Tier 2 Silencio Silencio Silencio Tier 2 Silencio Silencio Silencio
    └──────────┘  └────────┘  └──────────┘
```

## Agents

Silencio Tier Silencioso Agente Persona Silencio basado en Silencio Líneas Silenciosos
|------|-------|---------|----------|-------|-------|
| 0 | claude-mastery-chief Silencio Orion Silencio Original Silencio 554 Silencio, enrutamiento, cross-cutting conocimientos voca
| 1 | hooks-architect TENIDO LAtch TENIDO DESLER (IndyDevDan) TEN 1013 TEN 17 eventos de gancho, automatización, control de daños TENIDO
| 1 | mcp-integrator Silencio Piper Silencio Peter Steinberger (@steipete) Silencio 791 Silenciosos servidores MCP, descubrimiento de herramientas, presupuesto contextual tención
| 1 | swarm-orchestrator Silencio Nexus Silencio Kieran Klaassen + Reuven Cohen TEN 1008 Silencio Equipos de agentes, subagentes, ejecución paralela TENIDO
| 1 | config-engineer Silencio Silencio Silencioso SuperClaude-Org Silencio 663 Silencioso, permisos, CLAUDE.md, sandbox TENIDO
| 2 | skill-craftsman ← Anvil ← BMAD-CODE-ORG TENCIÓN 1.046 ANTERIÓ Habilidades, plugins, comandos, context engineering TEN
| 2 | project-integrator Silencio Conduit Silencio Daniel Miessler (PAI) Silencio 959 Silencio integración del proyecto, CI/CD, puente AIOS ,
| 2 | roadmap-sentinel Silencio Vigil Silencio Boris Cherny ← 707 Silencio Roadmap, changelog, características de adopción Silencio

## Inicio rápido

Este escuadrón é uma [Agent Skill](https://agentskills.io): roda no Claude Code, Codex,
Gemini CLI, Cursor, GitHub Copilot, VS Code, OpenCode y otros clientes compatibles.

Activar el orquestador

Pregunte en lenguaje natural ("Necesito poner ganchos en mi agente") o invocar la habilidad
`claude-code-mastery` por nombre. El líder de la equipo está cargado de
`agents/claude-mastery-chief.md`, en relación con la raíz de esta habilidad.

* Acceso directo a un experto*

El jefe viaja solo, pero puedes pedir un experto por nombre.
archivo en `agents/`:


|---|---|
| `agents/hooks-architect.md` 
| `agents/mcp-integrator.md` 
| `agents/swarm-orchestrator.md`  multi-agente |
| `agents/config-engineer.md` 
| `agents/skill-craftsman.md` ← Habilidades e plugins TENIDO
| `agents/project-integrator.md` 
| `agents/roadmap-sentinel.md` 

<details>
■summary Confeccionar legada por slash comando do Claude Code

Sólo vale la pena en antiguas instalaciones hechas en `~/.claude/commands/`:

```
/AIOS:agentes:claude-mastery-chief
/AIOS:agentes:hooks-architect
/AIOS:agentes:mcp-integrator
/AIOS:agentes:swarm-orchestrator
/AIOS:agentes:config-engineer
/AIOS:agentes:skill-craftsman
/AIOS:agentes:project-integrator
/AIOS:agentes:roadmap-sentinel
```

</details>

## Cobertura de la alimentación

Silencio Código de Claude Característica Silencio Especialista Silencio Mandos Clave Silencio
|-------------------|-----------|-------------|
Silenciosos ganchos (17 eventos) Silencio Latch Silencio `*create-hook`, `*audit-hooks`, `*hook-patterns` |
Silencio MCP Integration Silencio `*add-server`, `*audit-mcp`, `*create-mcp-server` |
Silenciosos Subagentes &amp; Equipos Silencio Nexus Silencio `*create-agent`, `*create-team`, `*orchestrate` |
TENIDO Ajustes &quot; Permisos ANTE Sigil TEN `*configure`, `*permission-strategy`, `*sandbox-setup` |
← Habilidades &amp; Plugins ← Anvil TEN `*create-skill`, `*create-plugin`, `*context-strategy` |
Silencios , integración de proyectos Silenciosos `*integrate-project`, `*brownfield-setup`, `*ci-cd-setup` |
Silencio Vigil Silencio Silencio `*update-knowledge`, `*feature-radar`, `*migration-guide` |
 `*aios-bridge`, `*aios-guide` |

## Elite Minds Research Attribution

Este equipo fue creado a través de investigación iterativa con la validación del abogado del diablo (3 iteraciones). people/projects con marcos documentados:

Silencio Silencio Silencio Silencio Silencio Silencio Silencio Silencio 
|------|-------------|--------|
| **disler** (IndyDevDan) Silencio Hooks Mastery framework, meta-agent patrones, control de daños Silencio [GitHub](https://github.com/disler/claude-code-hooks-mastery) |
Silencio **Peter Steinberger** (@steipete) Silencio claude-code-mcp, multi-instance workflow, CLI-first filosofía TEN [Blog](https://steipete.me/), [GitHub](https://github.com/steipete/claude-code-mcp) |
Silencio **Kieran Klaassen** Silencio TeammateDescubrimiento de herramientas, documentación de patrones enjambre Silencioso [Gists]https://gist.github.com/kieranklaassen) |
Silencio **Reuven Cohen** (ruvnet) Silencio Ruflo orquestation platform, 54+ agents, WASM kernels TEN [GitHub](https://github.com/ruvnet/ruflo) |
Silencio **SuperClaude-Org** TEN 9 personas cognitivas, 5 modos conductuales, puro .md config TENIDO [GitHub](https://github.com/SuperClaude-Org/SuperClaude_Framework) |
Silencio **BMAD-CODE-ORG** TENIDO Método BMAD, 21 agentes, 50+ flujos de trabajo, spec-driven desarrollo TENIDO [Docs](https://docs.bmad-method.org/) |
Silencio **Daniel Miessler** ← Infraestructura Personal AI (PAI), Filosofía Unix para AI Silencioso [Blog]https://danielmiessler.com/), [GitHub](https://github.com/danielmiessler/Personal_AI_Infrastructure) |
Silencio **Boris Cherny** Silencioso creador de Códigos Claude, plan-first la metodología, casos paralelos TENIDO [Blog](https://boristane.com/[Ingeniero Prágmático]https://newsletter.pragmaticengineer.com/p/how-claude-code-is-built) |

# AIOS-Core Integration

Este equipo entiende tanto las capacidades nativas del Código de Claude como el marco AIOS-core:

Silencio AIOS Concept Silencio Claude Code Equivalent Silencio Bridge Agent ←
|-------------|----------------------|-------------|
TENIENTES Agentes (@dev, @qa...) TENIDOS Subagentes (.claude/agents/) Silencio Nexus Silencio
TENIDOS CUESTIONES (.aios-core/tasks/) Habilidades de vida (.claude/skills/) Silencio Silencio Silencio
Silencioso de trabajo ← Sesiones multi-paso Silencio Nexus + Orion  sometida
| core-config.yaml | .claude/settings.json | Sigil |
← Ganchos de Python (monitor/) ← Ganchos nativos (command/http/prompt/agentSilencio, vida.
TEN QUÉ QUÉN QUÉ TENIDO Validación basada en Hook TENIDO LA TIERRA + Sigil TEN
Silencio Entity registry Silencioso Herramienta Buscar + registro MCP Silencio

## Directory Structure

```
squads/claude-code-mastery/
├── config.yaml                    # Configuración de la sede y arquitectura de la ficha
├── README.md                      # This file
├── agents/
│   ├── claude-mastery-chief.md    # Tier 0: Orquesta (Orión)
│   ├── hooks-architect.md         # Tier 1: Hooks (Latch)
│   ├── mcp-integrator.md          # Tier 1: MCP (Piper)
│   ├── swarm-orchestrator.md      # Tier 1: Subagents/Teams (Nexus)
│   ├── config-engineer.md         # Tier 1: Settings/Config (Sigil)
│   ├── skill-craftsman.md         # Tier 2: Skills/Plugins (Anvil)
│   ├── project-integrator.md      # Tier 2: Integración (Conduit)
│   └── roadmap-sentinel.md        # Tier 2: Roadmap (Vigil)
- tareas específicas de cada una
- flujos de trabajo/ # Multifase workflows
- plantillas/ plantillas de salida

- scripts/ # Utility scripts
└── outputs/
    - mentes/ # Extracción de ADN mental
```

## Quality Metrics

TEN TER TER TER TER TER TER ANTE TER ANTE ANTE
|--------|-------|
Silencio Total agents Silencio 8 Silencio

| Avg lines/agent | 843 |
Silencio Tier 0 coverage Silencio 1 orquestador Silencio
Silencio Tier 1 cobertura Silencio 4 especialistas en el núcleo
Silencio Tier 2 cobertura Silencio 3 especialistas estratégicos Silencio
Silenciosidad mental clonado Silencio 8 (de 7 fuentes distintas) Silencio
Silencio Investigación iteraciones Silencio 3 (con el defensor del diablo) ←
← Las colisiones de Naming fijan Silencio 2 (Piper, Sigil)

---

*Claude Code Mastery Squad v1.0 - Creado por Squad Architect*
*Filosofía: "Master la herramienta para dominar el oficio."*
