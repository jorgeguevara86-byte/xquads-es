---
task: diagnoseStorytelling()
responsavel: "@story-chief"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: user_message
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: routing_catalog
    tipo: string
    origem: data/routing-catalog.yaml
    obrigatorio: true

Saida:
  - campo: diagnosis
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[] Intención del usuario analizada y categorizada" 
  - "[ ] Respuesta transversal entregada al usuario" 
  - "[] Sugerencia de ruta proporcionada" 
---

# Task: Diagnose &gt; Route — Storytelling Squad

## Metadata

Silencios , , , , . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 
|---------------|------------------------------------------------|
Silencioso ID de tareas `storytelling:diagnose`                        |
Silencio `@storytelling` o `@storytelling:story-chief` |
| Orchestrator  | `story-chief`                                  |
| Version       | 1.0.0                                          |
| Created       | 2026-03-05                                     |

## Purpose

Analice la narrativa o pregunta narrativa del usuario, proporcione una inmediata cross-cutting
respuesta, y determinar si se necesita una pudrición especializada.
archivo de agente especializado durante el diagnóstico — solo identifica la mejor ruta.

## Inputs

| Entrada | Fuente | Requerido |
|------------------|---------------------|----------|
| `user_message` | Mensaje de usuario | SÍ |
| `routing_catalog` | `data/routing-catalog.yaml` | YES |
| `config`         | `config/config.yaml` | YES     |
| `conversation_history` | Contexto de la sesión | NO |

## Preconditions

1. El mensaje de usuario no está vacío
2. El catálogo de rutas está cargado y accesible

## Fases de Ejecución

### Fase 1: Solicitud de análisis

1. Extraiga la pregunta principal o la intención del mensaje del usuario.
2. Identificar palabras clave, dominios narrativos y contexto narrativo
3. Determinar la escala de historia: micro (anecdota, post), meso (presentación, episodio), macro (imagen, novela) o meta (movimiento, cultural)
4. Determinar el dominio narrativo: mítico, estructural, personal, empresarial, performativo o movimiento

### Fase 2: Catálogo de enrutamiento de coincidencias

1. Load `data/routing-catalog.yaml`
2. Hacer coincidir las palabras clave extraídas con las listas de palabras clave del dominio
3. Califique cada dominio según la superposición de palabras clave y la relevancia contextual
4. Identifique `primary_agent` y `secondary_agent` para el dominio top-scoring .
5. Si varios dominios marcan por igual, considere la escala de historia para romper los lazos:
   - Micro escala: preferir matthew-dicks, kindra-hall, park-howell
   - Escala Meso: prefiere nancy-duarte, oren-klaff, dan-harmon, blake-snyder
   - Escala de macros: preferir blake-snyder, shawn-coyne, joseph-campbell
   - Meta escala: preferir marshall-ganz, joseph-campbell

### Fase 3: Respuesta transversal

**OBLIGATORIO: ejecute siempre esta fase antes de cualquier enrutamiento.**

1. Proporcionar una respuesta inmediata y útil a la pregunta del usuario.
2. La respuesta debe ser factible y demostrar la competencia de dominio narrativo
3. Incluir el contexto pertinente: marcos mencionados, orientación rápida de narración
4. Referencia del principio o marco narrativo aplicable por nombre
5. Esta respuesta debe ser independiente, incluso si el usuario nunca sigue la sugerencia de ruta

### Fase 4: Evaluación de confianza

Evalúe la confianza del enrutamiento:

| Nivel | Criterios | Acción |
|--------|-----------------------------------------------|-------------------------------|
TENIDO ALTO TENIDO CALENDARIO DE palabras clave claras, un solo dominio, inequívoca TENIDO Ruta al agente primario TEN
| MEDIANO | Coincidencia de varios dominios, ligera ambigüedad | Sugerir primaria + secundaria |
TEN LOW TENER No hay partido claro, solicitud vaga, cross-domain    Silencio Mantente con el jefe, haz preguntas aclaratorias

## Formato de salida

```yaml
diagnosis:
  intent: "{intención del usuario analizada}" 
  narrative_domain: "mito Silencio estructural Silencio personal Silencioso negocio Silencio performativo Silencio movimiento" 
  story_scale: "micro" 
  matched_domain: "{dominio del catálogo de enrutamiento}" 
  confidence: "ALTO | MEDIANO | BAJO" 
  primary_agent: "{agent-id}"
  secondary_agent: "{agent-id}"
  cross_cutting_answer: "{La respuesta inmediata proporcionada al usuario}"
  routing_suggestion: "{¿Por qué este especialista fue elegido y lo que pueden añadir}"
```

## Condiciones de veto

- **NUNCA** ruta sin proporcionar primero una respuesta cross-cutting 
* * NUNCA* ruta cuando la confianza es LOW – quédate con el jefe y haz preguntas aclaradoras
- ** NUNCA** cargar un archivo de agente especializado durante el diagnóstico - sólo identificar la ruta
- ############################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################### multi-specialist flujo durante el diagnóstico - un especialista a la vez
- ############################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################### joseph-campbell para cada pregunta — coincide con el dominio real

## Criterios de finalización

- [x] Intención del usuario analizada y categorizada
- [x] Se identifican los dominios narrativos y la escala de historias
- [x] Catálogo de enrutamiento consultado y dominio coincidente
- [x] Respuesta transversal entregada al usuario
- [x] Nivel de confianza evaluado
- [x] Se proporcionó sugerencia de ruta (si confianza >= MEDIA)
- [x] No hay archivos de agente especializado cargados durante el diagnóstico
