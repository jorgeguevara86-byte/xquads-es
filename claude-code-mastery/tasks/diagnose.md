# Task: Diagnosticar la pregunta del Código de Claude

** ID de usuario** CCM-CHIEF-001
**Version:** 1.0.0
**Command:** `*diagnose`
Orión (Orquesta)claude-mastery-chief)
**Purpose:** Triage Claude Code questions and problems, provide a quick answer, and route to the appropriate specialist agent when domain-specific es necesario contar con conocimientos especializados.

---

## Overview

```
  Pregunta de usuario
       |
       v
  +------------------+
  Silencio 1. Parse Request Silencio
  TENCIÓN Extractar palabras clave
  +------------------+
       |
       v
  +------------------+
  Silencio 2. Concordancia con Routing Silencio
  |    Matrix          |
  +------------------+
       |
       +-------+-------+
       |               |
       v
  Interruptores de dominio específicos
       |               |
       v
  +----------+    +------------------+
  Silencio 3a. Respuesta involuntaria Silencioso 3b. Respuesta rápida
  Silencio Directamente Silencio Silencioso + Ruta para Silencio
  +----------+    |  Specialist       |
       |          +------------------+
       v               |
  +------------------+ |
  Silencio 4. Informe de salida Silencio
  +------------------+
```

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
Silencioso pregunta Silencio Silencio Silencio Sugerencia de usuario Silencio Silencio Novato idioma natural pregunta o problema descripción Silencio
Silencio contexto Silencioso objeto Silencioso sesión estado Silencio No Silencio Historia activa, rama, errores recientes si está disponible Silencio

---

## Preconditions

- El equipo de Mastery del Código Claude está activo con Orion como agente de entrada
- La matriz de oxidación se carga de la definición de agente (triage.routing_matrix)
- Los 7 agentes especializados están registrados config.yaml

---

## Fases de Ejecución

### Fase 1: Solicitud de análisis (Extracción de palabras clave)

1. Parse la pregunta del usuario o descripción del problema
2. Extraer las palabras clave primarias y las señales de intención
3. Identificar la categoría de solicitud:
   - ¿Es una pregunta de "cómo"?
   - ¿Es un debugging/troubleshooting ¿Problema?
   - ¿Es un setup/configuration ¿Preguntar?
   - ¿Es un conceptual/comparison ¿Pregunta?
4. Observe cualquier dominio secundario que pueda ser relevante

### Fase 2: Coincidencia contra la matriz de rugido

Aplicar la palabra clave que coincida con los 7 dominios especializados:

Silencio Silencio Silencio Palabras clave Silencio Ruta Para Silencio Persona Silencio
|--------|----------|----------|---------|
Silenciosos ganchos vivientes gancho, pre_tool_use, post_tool_use, ciclo de vida, interceptación, bloque, código de salida, tubería de automatización, pre_compact, notificación, control de daños TENIDO hooks-architect TEN ANTERIOR ANTERIOR
TEN mcp TEN mcp, servidor, búsqueda de herramientas, stdio, sse, http streamable, mcp____, context7, exa, puerta de puerta de muelle, añadir servidor TEN mcp-integrator Silencio, amor, amor, viv , .
TEN subagents TEN subagent, el equipo de agente, enano, compañero de equipo, worktree, paralel, agente de fondo, desgastado, multi-agent, TeammateTool Silencio swarm-orchestrator Silencio Nexus Silencio
TENCIÓN TENCIÓN TENIDO , permiso, CLAUDE.md, reglas, sandbox, gestionado, empresa, permitir, negar, keybinding, ventana context, compaction TEN config-engineer Silencio Silencio Silencio
← habilidades vocatorias habilidad, comando, plugin, SKILL.md, comando slash, ingeniería contextual, spec-driven, .claude/commands, .claude/skills, marketplace TEN skill-craftsman Silencio Silencio Silencio
TEN-Intección TENI integrar, repositorio, configuración de proyectos, CI/CD, sin cabeza, brownfield, monorepo, AIOS, git workflow TENIDO project-integrator Silencio Silencio Silencio
TENVR TEN TERRITOR , actualización, cambio de página, versión, hoja de ruta, nueva característica, lo que cambió, migración, actualización, adopción TEN roadmap-sentinel Silencio Vigil Silencio

**Reglas de puntuación:**
- Contar coincidencias de palabras clave por dominio
- Si un dominio puntua significativamente más alto (2+ coinciden por encima de otros), ruta allí
- Si múltiples dominios se atan o la pregunta abarca dominios, trate como cross-cutting
- Si ningún dominio coincide con fuerza, trate como cross-cutting (Orión responde directamente)

## Fase 3a: Respuesta cruzada (Direct)

Si la pregunta es cross-cutting o general:

1. Sintetizar el conocimiento del quick_reference Sección y sensibilización de la AIOS
2. Proporcionar una respuesta completa y factible
3. Referencia de los agentes especializados relevantes que el usuario puede consultar para una exploración más profunda
4. Incluir fragmentos de código, ejemplos de configuración o tablas de referencia según corresponda

## Fase 3b: Respuesta del dominio-específico (Quick + Route)

Si la pregunta se mapea a un dominio específico:

1. **Proporcione una respuesta rápida primero** - Nunca la ruta sin dar valor inmediato
   - Responder a la pregunta a nivel superficial (3-5 líneas mínimo)
   - Incluya un ejemplo de concreto (código snippet, bloque de configuración o comando)
2. **Recorrido al especialista** para obtener más experiencia:
   - Nombrar el agente especialista y persona
   - Explicar qué profundidad adicional puede proporcionar el especialista
   - Proporcione el comando de activación: `@claude-code-mastery:{agent-id}`
   - Sugerir un comando especializado específico si es aplicable (por ejemplo, `*create-hook`, `*audit-settings`)

### Fase 4: Evaluación de confianza

Valorar la confianza del diagnóstico:

| Confianza | Criterios | Acción |
|------------|----------|--------|
TENIDO ALTO TENIDO 3+ palabras claves en un solo dominio, clara intención TENIDO Ruta con confianza TEN
TENIDO MEDIUM TENIDO 1-2 fósforos, intención ambigua TENIDO Proporcionar respuesta + sugerir 2 posibles especialistas TENIDO
TEN LOW TENEDN No hay un dominio claro TEN Respuesta directamente, hacer aclaraciones sobre la pregunta TENIDO

---

## Formato de salida

```markdown
## Diagnosis

**Category:** {domain-name | cross-cutting}
**Confidence:** {HIGH | MEDIUM | LOW}
**Specialist:** {persona-name} ({agent-id}) | Direct Answer

### Quick Answer

{3-10 line answer with concrete example}

### Recommended Next Step

{Route instruction OR follow-up question for clarification}
```

---

## Condiciones de veto

- ** NUNCA** ruta a un especialista sin proporcionar al menos una respuesta rápida primero. El usuario debe recibir valor inmediato de cada interacción con Orión.
- **Nunca** ruta cuando la confianza es LOW - hacer una pregunta aclaradora en su lugar.
- ** NUNCA** cargar un archivo de agente especializado durante el diagnóstico. Sólo proporciona instrucciones de enrutamiento para que el usuario active el especialista.
- ** NUNCA** adivina el dominio cuando las palabras clave son ambiguas - sintetizar a cross-cutting responder y dejar que el usuario refina.

---

## Criterios de finalización

- [ ] Pregunta de usuario analizada y palabras clave extraídas
- [ ] Matriz de rutina consultada con resultados marcados
Respuesta rápida proporcionada con ejemplo concreto
- [ ] Ruta especializada proporcionada (si domain-specific)
- Nivel de confianza indicado en la salida
