---
task: diagnoseDesignChallenge()
responsavel: "@design-chief"
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
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: diagnosis
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[] Intención del usuario analizada y categorizada" 
  - "[ ] Respuesta transversal entregada al usuario" 
  - "[) Nivel de confianza evaluado" 
---

# Task: Diagnose &quot; Route - Design Squad

## Metadata

| Campo | Valor |
|---------------|--------------------------------------------------|
Silencioso ID de tareas `design-squad:diagnose`                          |
Silencio `@design-squad` o `@design-squad:design-chief`  |
| Orchestrator  | `design-chief`                                   |
| Version       | 1.0.0                                            |
| Created       | 2026-03-05                                       |

## Purpose

Analice la pregunta de diseño del usuario, proporcione una inmediata cross-cutting respuesta,
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

## Fases de Ejecución

### Fase 1: Solicitud de análisis

1. Extraiga la pregunta principal o la intención del mensaje del usuario.
2. Identificar palabras clave, dominios de diseño y contexto técnico
3. Determinar el dominio del diseño: sistemas, operaciones, experiencia o producción
4. Determinar el patrón de colaboración si es aplicable:
   - Flujo de creación de sistemas de diseño
   - Nuevo flujo de diseño de características
   - Flujo de configuración de las operaciones de diseño

### Fase 2: Catálogo de enrutamiento de coincidencias

1. Load `data/routing-catalog.yaml`
2. Hacer coincidir las palabras clave extraídas con las listas de palabras clave del dominio
3. Califique cada dominio según la superposición de palabras clave y la relevancia contextual
4. Identifique `primary_agent` y `secondary_agent` para el dominio top-scoring .
5. Si múltiples dominios marcan por igual, considere el dominio del diseño para romper los lazos:
   - Preguntas de sistemas: preferir brad-frost
   - Cuestiones de operaciones: preferir dave-malouf
   - Preguntas de experiencia: preferir ux-designer
   - Cuestiones de producción: preferir design-system-architect o ui-engineer

### Fase 3: Respuesta transversal

**OBLIGATORIO: ejecute siempre esta fase antes de cualquier enrutamiento.**

1. Proporcionar una respuesta inmediata y útil a la pregunta del usuario.
2. La respuesta debe ser factible y demostrar la competencia de dominio del diseño
3. Incluir el contexto pertinente: metodologías, patrones o principios de diseño aplicables
4. Referencia del marco o metodología de diseño aplicable por nombre
5. Esta respuesta debe ser independiente, incluso si el usuario nunca sigue la sugerencia de ruta

### Fase 4: Evaluación de confianza

Evalúe la confianza del enrutamiento:

| Nivel | Criterios | Acción |
|--------|-----------------------------------------------|-------------------------------|
TENIDO ALTO TENIDO CALENDARIO DE palabras clave claras, un solo dominio, inequívoca TENIDO Ruta a la especialista primaria TEN
| MEDIANO | Coincidencia de varios dominios, ligera ambigüedad | Sugerir primaria + secundaria |
TEN LOW TENER No hay partido claro, solicitud vaga, cross-domain    Silencio Mantente con el jefe, haz preguntas aclaratorias

## Formato de salida

```yaml
diagnosis:
  intent: "{intención del usuario analizada}" 
  design_domain: "sistemas Silenciosos operaciones Silencioso experiencia viv" 
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
- ############################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################### multi-specialist flujo de colaboración durante el diagnóstico - un especialista en un momento
- ############################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################### brad-frost para cada pregunta — coincida con el dominio de diseño real

## Criterios de finalización

- [x] Intención del usuario analizada y categorizada
- [x] Dominio de diseño identificado
- [x] Catálogo de enrutamiento consultado y dominio coincidente
- [x] Respuesta transversal entregada al usuario
- [x] Nivel de confianza evaluado
- [x] Se proporcionó sugerencia de ruta (si confianza >= MEDIA)
- [x] No hay archivos de agente especializado cargados durante el diagnóstico
