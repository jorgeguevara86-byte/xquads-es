---
task: diagnoseAdvisoryBoard()
responsavel: "@board-chair"
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

# Tarea: Diagnóstico y ruta: equipo del consejo asesor

## Metadata

| Campo | Valor |
|---------------|--------------------------------------------------|
| ID de tarea | `advisory-board:diagnose` |
| Comando | `@advisory-board` o `@advisory-board:board-chair` |
| Orchestrator  | `board-chair`                                    |
| Version       | 1.0.0                                            |
| Created       | 2026-03-05                                       |

## Purpose

Analiza la pregunta estratégica del usuario, proporciona una respuesta inmediata cross-cutting ,
y determine si se necesita enrutamiento especializado. La silla NUNCA carga un asesor
Archivo de agente
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

## Fases de Ejecución

### Fase 1: Solicitud de análisis

1. Extraiga la pregunta principal o la intención del mensaje del usuario.
2. Identificar palabras clave, dominios de asesoramiento y contexto estratégico
3. Determinar el ámbito de asesoramiento: financiero, empresarial, organizacional o filosófico.
4. Determine el estilo de decisión necesario: quantitative/systematic, mental-model-based, first-principles, network-strategic, purpose-driven, courage-based, team-health-basedo minimalist-contrarian.

### Fase 2: Catálogo de enrutamiento de coincidencias

1. Load `data/routing-catalog.yaml`
2. Hacer coincidir las palabras clave extraídas con las listas de palabras clave del dominio
3. Califique cada dominio según la superposición de palabras clave y la relevancia contextual
4. Identifique `primary_agent` y `secondary_agent` para el dominio top-scoring .
5. Si varios dominios obtienen la misma puntuación, considere el estilo de decisión para romper empates:
   - Decisiones cuantitativas: prefiera ray-dalio
   - Preguntas sobre el modelo mental: prefiera charlie-munger
   - Problemas de primeros principios: prefiera peter-thiel, naval-ravikant
   - Network/scaling: prefer reid-hoffman
   - Purpose/culture: prefer simon-sinek, brene-brown
   - Dinámica de equipo: prefiera patrick-lencioni

### Fase 3: Respuesta transversal

**OBLIGATORIO: ejecute siempre esta fase antes de cualquier enrutamiento.**

1. Proporcionar una respuesta inmediata y útil a la pregunta del usuario.
2. La respuesta debe ser viable y demostrar competencia en asesoramiento estratégico.
3. Incluir contexto relevante: marcos, principios o modelos mentales aplicables
4. Haga referencia a la perspectiva de asesoramiento aplicable por nombre
5. Esta respuesta debe ser independiente, incluso si el usuario nunca sigue la sugerencia de ruta

### Fase 4: Evaluación de confianza

Evalúe la confianza del enrutamiento:

| Nivel | Criterios | Acción |
|--------|-----------------------------------------------|-------------------------------|
| ALTA | Concordancia clara de palabras clave, dominio único, inequívoco | Ruta al asesor principal |
| MEDIANO | Coincidencia de varios dominios, ligera ambigüedad | Sugerir primaria + secundaria |
| BAJO | Ninguna coincidencia clara, solicitud vaga, cross-domain | Quédese en la silla, haga preguntas aclaratorias |

## Formato de salida

```yaml
diagnosis:
  intent: "{intención del usuario analizada}" 
  advisory_domain: "financiero | emprendedor | organizacional | filosófico" 
  decision_style: "{estilo de decisión identificado}" 
  matched_domain: "{dominio del catálogo de enrutamiento}" 
  confidence: "ALTO | MEDIANO | BAJO" 
  primary_agent: "{agent-id}"
  secondary_agent: "{agent-id}"
  cross_cutting_answer: "{La respuesta inmediata proporcionada al usuario}"
  routing_suggestion: "{Por qué se eligió a este asesor y qué puede agregar}"
```

## Condiciones de veto

- **NUNCA** ruta sin proporcionar primero una respuesta cross-cutting 
- **NUNCA** ruta cuando la confianza es BAJA: quédese en la silla y haga preguntas aclaratorias
: **NUNCA** cargue un archivo de agente asesor durante el diagnóstico; solo identifique la ruta
: **NUNCA** invoque una reunión de la junta completa durante el diagnóstico; diríjase a un asesor a la vez
- **NUNCA** usa de forma predeterminada el mismo asesor para cada pregunta; coincide con el dominio real

## Criterios de finalización

- [x] Intención del usuario analizada y categorizada
- [x] Dominio de asesoramiento y estilo de decisión identificados
- [x] Catálogo de enrutamiento consultado y dominio coincidente
- [x] Respuesta transversal entregada al usuario
- [x] Nivel de confianza evaluado
- [x] Se proporcionó sugerencia de ruta (si confianza >= MEDIA)
- [x] No se cargaron archivos del agente asesor durante el diagnóstico
