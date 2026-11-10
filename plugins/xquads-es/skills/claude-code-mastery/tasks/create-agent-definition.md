# Task: Create Custom Subagent Definition

** ID de la lista:** create-agent-definition
**Version:** 1.0
**Purpose:** Crear un purpose-built archivo de definición subagente para uso con la herramienta Agente
**Orquestador:**swarm-orchestrator (Nexus)
**Modelo:** Interactivo (elicito: verdadero)
**Calidad Estándar:** El archivo de agente pasa lint, carga correctamente y ejecuta el aviso de prueba

---

## Overview

Esta tarea crea una definición subagente personalizada en `.claude/agents/` que se puede invocar a través de la herramienta Agente. Los subagentes son instancias especializadas de Claude con instrucciones de alcance, selección de modelos y restricciones opcionales de herramientas.

```
INPUT (INPUT)agent_purpose + alcance + complejidad)
    |
[FAPACIDAD 1: DEFINICIÓN DE LA PURPOSE]
    - No importa lo que el agente hace y no hace
    - identificar herramientas y conocimientos necesarios
    - necesidades de aislamiento
    |
[FAPACIDAD 2: TYPE SELECTION]
    - Español Elige tipo subagente (general, explore, plan)
    - Seleccione modelo (opus, soneto, haiku)
    - Limitaciones de herramientas de Define
    |
[FILSO 3: QUIERO CREACIÓN]
    - Crear .claude/agents/{name}.md
    - Escribe YAML frontmatter
    - Escribe cuerpo de instrucción en marcado
    |
[FAPACIDAD 4: INSTRUCCIÓN ENGINEERING]
    - Escribe instrucciones claras de comportamiento
    - Actualizar las expectativas de formato de salida
    - agregar correas y limitaciones
    |
[FAPÉS 5: SELECCIÓN MODELO]
    - Emplear la complejidad para modelar el tier
    - Confeccionar cost/quality tradeoff
    - Set max_turns si es necesario
    |
[FAPACIDAD 6: VALIDACIÓN]
    - Agente de prueba con herramienta Agente
    - Revisar el acceso a herramientas funciona según lo esperado
    - Calidad de salida de datos
    |
OUTPUT: Archivo de definición de agente + resultados de prueba
```

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
| agent_name TENEDA TENIDO Usuario TENIDO SI ANTERIOR KABBAB-case, no espacios (por ejemplo, code-reviewer) |
| agent_purpose TENCIÓN TENIDO TENIDO Usuario TENIDO sí TENIDO Descripción de una sola-sentencia de lo que hace el agente TENIDO
TENSI TENISTERIOR TENIDO Usuario o auto TENIDO SI TENSI simple / standard / complex TEN
| tools_needed TENIDO SUPERIO TENIDO NO TENIDO Lista de herramientas que el agente necesita acceso a TEN
| output_format Silencio Silencio Silencio Silencio Usuario Silencio no Silencio Estructura esperada de salida (marca atrás, json, yaml) Silencio

---

## Preconditions

1. `.claude/agents/` directorio existe (crear si no)
2. Entendimiento de la tarea que el agente realizará
3. El Código de Claude está en funcionamiento para los ensayos

---

## Phase 1: Purpose Definition

** Objetivo:** Examinar claramente lo que el agente hará y no hará.

### Steps

1.1 Definir la responsabilidad principal del agente en una frase.
1.2. Lista 3-5 tareas específicas que el agente debe manejar.
1.3. Lista 2-3 cosas que el agente no debe hacer (anti-scope).
1.4. Identificar qué contexto necesita el agente (archivos, conocimiento de proyecto, etc.).

### Purpose Template

```
Agent: {name}
¿Tiene: { responsabilidad primaria}
Tasks: {task1}, {task2}, {task3}
NO: {anti1}, {anti2}
Needs: {context1}, {context2}
```

---

## Fase 2: Selección de Tipo

** Objetivo:** Elige la configuración de subagente adecuada.

* Tipos subgent*

Silencio Tipo Silencioso Herramientas disponibles Silencio Mejor para Silencio
|------|----------------|----------|
Silencio **Con fines generales** (por defecto) Silencio Todas las herramientas ANTERIVISIÓN, análisis, tareas complejas TENIDO
Silencio **Explore** Silencio Read, Glob, Grep, Bash(read-only) ¦ Investigación, búsqueda de código, búsqueda de documentación Silencio
Silencio **Plan** Silencio Read, Glob, Grep (no escribir) Silencio Diseño, arquitectura, tareas de planificación ←

### Steps

2.1. Coincide con el propósito del agente a un tipo.
2.2. Si no cabe, utilice general-purpose con explícita `allowed-tools` restricciones.
2.3. Documentar la decisión y la justificación del tipo.

---

## Fase 3: Creación de archivos

** Objetivo:** Crear el archivo de definición de agente con la estructura adecuada.

Plantilla de Archivo de Agentes

```markdown
---
name: {agent-name}
description: {one-line description}
model: {opus-4|sonnet-4|haiku-4}
allowed-tools:
  - Read
  - Write
  - Edit
  - Bash
  - Grep
  - Glob
---

# {Agent Name}

## Role
{Detailed description of agent's role and expertise}

## Instructions
{Step-by-step behavioral instructions}

## Constraints
{What the agent must NOT do}

## Output Format
{Expected output structure}
```

### Steps

3.1. Crear `.claude/agents/{name}.md` usando la plantilla anterior.
3.2. Llenar en la primera máquina de YAML con nombre, descripción, modelo y allowed-tools.
3.3. Los campos de la primera planta son:
   - `name`: Nombre de la pantalla para el agente
   - `description`: Breve descripción mostrada en los listados de agentes
   - `model`: Que modelo Claude utilizar (ver Fase 5)
   - `allowed-tools`: Array de herramientas que el agente puede acceder (omit para todas las herramientas)

---

Fase 4: Ingeniería de la Instrucción

** Objetivo:** Escribir instrucciones claras y efectivas en el cuerpo marcado.

### Instrucción Buenas Prácticas

1. **Sé específico** -- "Analyze imports and suggest barrel files" no "Ayuda con código"
2. **Set output expectations** - Describa el formato exacto que desee
3. **Añada ejemplos** - Mostrar input/output pares cuando sea posible
4. **Definir los límites** - Lo que el agente debe rechazar o escalar
5. **Incluir la carga de contexto** -- Diga al agente qué archivos leer primero

### Seccións de Instrucción

```markdown
## Role
You are a {role} specialized in {domain}. Your job is to {primary task}.

## Process
1. First, read {relevant files}
2. Then, analyze {what to look for}
3. Finally, produce {output format}

## Rules
- ALWAYS {mandatory behavior}
- NEVER {prohibited behavior}
- When unsure, {fallback behavior}

## Output Format
Return your analysis as:
{format specification}
```

4.1. Escriba la sección Role con identidad clara.
4.2. Escriba la sección Proceso con pasos numerados.
4.3. Escribir la sección Reglas con ALWAYS/NEVER limitaciones.
4.4. Escriba la sección Formato de salida con especificación de la estructura.

---

## Fase 5: Selección de Modelo

** Objetivo:** Elige el modelo adecuado para el equilibrio de costes y calidad.

### Guía de selección de modelos

Silencioso modelo Silencioso costos Silenciosos
|-------|------|-------|----------|
| **claude-opus-4** ← High ← Sola Silencioso análisis complejos, decisiones de arquitectura, escritura matizada Silencio
| **claude-sonnet-4** ← Medium Silencio Medium Silencio Tareas estándar, revisión de código, implementación ←
| **claude-haiku-4** TENIDO TENIDO ANTERIENTE TENIDO Simples búsquedas, formato, tareas repetitivas TEN

### Decision Matrix

```
¿Es el complejo de tareas con entradas ambiguas?
  Sí - título opus
  NO - ES ¿Necesita generación o análisis de códigos?
    Sí - hijonet
    NO - ¿Es una tarea sencilla de búsqueda o formato?
      Sí.
      NO - título sonnet (predeterminado seguro)
```

5.1. Evaluar la complejidad de la tarea contra la matriz.
5.2. Establecer el `model` campo en primera.
5.3 Considerar que los subagentes incurren per-call costos - haiku para high-frequency agentes.

---

## Phase 6: Validation

** Objetivo:** Probar que el agente funciona correctamente.

### Steps

6.1. Invocar al agente usando la herramienta Agente con un impulso representativo.
6.2. Verificar el agente:
   - Usa sólo sus herramientas permitidas
   - Sigue sus instrucciones
   - Produce la producción en el formato esperado
   - Permanecer dentro de su alcance definido
6.3. Si el agente falla, se comprime con instrucciones (la solución más común).
6.4. Ejecute 2-3 diferentes puntas de prueba para cubrir los casos de borde.

---

## Formato de salida

```yaml
agent_definition_result:
  file: ".claude/agents/{name}.md"
  name: "{agent-name}"
  type: "{general vidasexplore soportes para el plan.]" 
  model: "{opus-4|sonnet-4|haiku-4}"
  tools_allowed: [...]
  test_results:
    - prompt: "Inmediatamente de prueba 1" 
      status: "pass"
    - prompt: "Inmediata de prueba 2" 
      status: "pass"
  ready: true
```

---

## Condiciones de veto

Silencio Silencio Silencio Silencio Silencio Silencio
|-----------|--------|
tención El propósito de agente es demasiado amplio (cubre 5+ dominios no relacionados) TEN- dividido en múltiples agentes TEN
Silencio No hay un formato de salida claro definido TEN- define la salida esperada antes de la creación 
TEN-Agente requiere herramientas que no existen TEN-JO-E-L-E-Investigar la disponibilidad de herramientas
tención La prueba requiere que todo falle TEN HALT -- reescribir instrucciones, no enviar agente roto TEN
Silencio Agente conflictos con el agente existente TEN HALT - elegir el nombre único TEN
