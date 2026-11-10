---
task: diagnoseCybersecurity()
responsavel: "@cyber-chief"
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
  - "[ ] Intenciones de usuario perseguidas y evaluadas por puerta ética" 
  - "[ ] Respuesta transversal entregada al usuario" 
  - "[] Sugerencia de ruta proporcionada" 
---

# Task: Diagnose &quot; Route - Cybersecurity Squad

## Metadata

Silencios , , , , . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 
|---------------|------------------------------------------------|
Silencioso ID de tareas `cybersecurity:diagnose`                       |
Silencio `@cybersecurity` o `@cybersecurity:cyber-chief` |
| Orchestrator  | `cyber-chief`                                  |
| Version       | 1.0.0                                          |
| Created       | 2026-03-05                                     |

## Purpose

Analice la pregunta de ciberseguridad del usuario, proporcione una inmediata cross-cutting respuesta,
y determinar si se necesita una trucha especializada. El jefe nunca carga a un especialista
durante el diagnóstico: solo identifica la mejor ruta.

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
3. El contexto de autorización ética se examina para todas las solicitudes ofensivas

## Fases de Ejecución

### Fase 1: Solicitud de análisis

1. Extraiga la pregunta principal o la intención del mensaje del usuario.
2. Identificar palabras clave, dominios de seguridad y contexto técnico
3. Categoría de solicitud de determinación: ofensivo, defensivo, operacional, estratégico o educativo
4. **ETHICAL GATE:** Si la solicitud involucra operaciones ofensivas, verifique:
   - ¿Es para un pentesta autorizado, CTF o contexto educativo?
   - Si no está claro, ASK para el contexto de autorización antes de proceder
   - Si es claramente malicioso, REFUSE con explicación

### Fase 2: Catálogo de enrutamiento de coincidencias

1. Load `data/routing-catalog.yaml`
2. Hacer coincidir las palabras clave extraídas con las listas de palabras clave del dominio
3. Califique cada dominio según la superposición de palabras clave y la relevancia contextual
4. Identifique `primary_agent` y `secondary_agent` para el dominio top-scoring .
5. Si varios dominios marcan por igual, prefiere el más cercano a la intención explícita del usuario

### Fase 3: Respuesta transversal

**OBLIGATORIO: ejecute siempre esta fase antes de cualquier enrutamiento.**

1. Proporcionar una respuesta inmediata y útil a la pregunta del usuario.
2. La respuesta debe ser factible y demostrar la competencia de dominio
3. Incluir el contexto pertinente: conceptos, orientación rápida, mejores prácticas
4. Para las solicitudes ofensivas: incluir recordatorios éticos y límites de alcance
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
  category: "ofensiva Silencio defensivo Silencio operacional Silencio estratégico Silencio educacional" 
  ethical_clearance: "Silencio needs_authorization . Rechazada" 
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
* * * * * * * * * Proporciona orientación ofensiva sin contexto de autorización ética
- **Nunca** ayudar con operaciones explícitamente maliciosas, no autorizadas o destructivas
* ** NUNCA** agentes de herramientas de ruta (nivel 2) directamente sin confirmar el contexto operativo

## Criterios de finalización

- [x] Intención del usuario analizada y categorizada
- [x] Puerta ética evaluada (para solicitudes ofensivas)
- [x] Catálogo de enrutamiento consultado y dominio coincidente
- [x] Respuesta transversal entregada al usuario
- [x] Nivel de confianza evaluado
- [x] Se proporcionó sugerencia de ruta (si confianza >= MEDIA)
- [x] No hay archivos de agente especializado cargados durante el diagnóstico
