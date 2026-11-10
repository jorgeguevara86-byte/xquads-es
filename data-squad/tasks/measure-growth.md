---
task: measureGrowth()
responsavel: "@sean-ellis"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: product
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: current_metrics
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: growth_analysis
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] La métrica North Star definida con métricas de entrada" 
  - "Al menos 5 hipótesis generadas y con ICE" 
  - "[ ] Registro de experimentos creado con plan de seguimiento" 
---

# Task: Measure Growth

** ID de usuario:** DATOS-002
**Version:** 1.0.0
**Command:** `*measure-growth`
Sean Ellis (*)sean-ellis)
**Purpose:** Encuentre la Metric de North Star, experimente crecimiento del diseño usando ICE puntuación, y analice resultados

---

## Inputs

| Entrada | Fuente | Requerido | Descripción |
|-------|--------|----------|-------------|
| `product` Silencio invocar usuario Silencio Sí Silencio Descripción del producto o servicio Silencio
| `current_metrics` Silencio Usuario Silencio Sí Silencio Números de crecimiento actuales (usuarios, ingresos, retención) Silencio
| `pmf_status` TEN TENIDO Usuario TEN No TENIDO Estado de ajuste del mercado de productos (pre/post PMF) Silencio
| `growth_stage` Silencioso usuario TENIDO No TENIDO Stage: tracción, transición, crecimiento, madura TENIDO
| `experiment_budget` Silencio Usuario Silencio No Silencio Recursos disponibles para la experimentación Silencio

## Preconditions

- El producto existe con actividad de usuario mensurable
- Análisis básico en su lugar (puede medir las acciones del usuario)
- Marcos de medición cargados (`data/metrics-frameworks.yaml`)

## Fases de Ejecución

## Fase 1: Encuentra la Metricia de la Estrella del Norte

1. Evaluar **Product-Market Fit** utilizando la prueba Sean Ellis:
   - Encuesta: "¿Cómo te sentirías si ya no pudieras usar este producto?"
   - **Muy decepcionado** √≥4 % = PMF alcanzada
   - &quot; 40 % &quot; , centrado en la PMF antes del crecimiento
2. Identificar el **core momento de valor** - la acción única que ofrece valor
3. Define la métrica **North Star (NSM)** - la métrica que captura la entrega de valor
   - Debe reflejar **customer valor** (no sólo ingresos de la empresa)
   - Debe ser...*leadable** (el equipo puede influir en él)
   - Debe ser...*measurable** (puede seguir el rastro semanal)
4. Mapa de la **input métricas** que conducen el NSM:
   - Pantalones (cuántas usuarios)
   - Profundidad (cuánta participación de cada usuario)
   - Frecuencia (cuán a menudo se dedican)
5. Validar: ¿Mejorando el NSM siempre mejora el negocio?

### Fase 2: Experimento de diseño (punto de la EI)

1. Generar **5-10 hipótesis de crecimiento** del análisis de embudos AARRR:
   - **Acquisición:** Cómo nos encuentran los usuarios
   *Activación*: Experiencia de primer valor
   - **Retención:** Los usuarios regresan
   - **Referencia:** Los usuarios traen a otros
   - **Revisenue:** Los usuarios pagan
2. Partitura de cada hipótesis utilizando **ICE Framework**:
   ¿Cuánto moverá el NSM?
   - **Confianza** (1-10): ¿Qué tan seguro vamos a funcionar?
   - **Ease** (1-10): ¿Qué tan fácil es esto para implementar?
   - **ICE Score** = (Impact + Confianza + Facilidad) / 3
3. Experimentos de Rancho por puntuación ICE
4. Seleccione los experimentos de 2-3 para la actual sprint
5. Para cada experimento seleccionado, defina:
   - Declaración de hipótesis: "Si [actuamos], entonces [mejor] [cambia] porque [razon]"
   - Meta de éxito
   - Tamaño mínimo de la muestra
   - Duration

## Fase 3: Ejecutar el Test

1. Definir **control y variante** para cada experimento
2. Configuración **tracking################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################ experiment-specific métricas
3. Determinación **statistical requisitos de significación** (típicamente p  0 0 0 0 05)
4. Planificar el **experiment c) cronología** (mínimo a 1 semana)
5. Identifique **guardrail métricas** - qué NO debe disminuir durante el experimento
6. Documentar el experimento en el **experiment log**

### Fase 4: Analizar resultados

1. Recopilar datos después de completar la duración del experimento
2. Calcular **statistical significación** de los resultados
3. Medida **impact en NSM** - ¿Se movió la Estrella del Norte?
4. Check **guardrail métricas** - ¿Algo resultó dañado?
5. Veredicto de determinación:
   **Winner:** Implementar permanentemente, document learning
   - **Perdedor:** Matar, documentar el aprendizaje
   **Inconclusive:** Extender la duración o aumentar la muestra
6. Actualizar el **growth modelo** con nuevos aprendizajes
7. Resultados de la alimentación de vuelta a la siguiente ronda de puntuación ICE

## Formato de salida

```yaml
growth_analysis:
  product: "{name}"
  pmf_score: "{percentage} muy decepcionada" 
  pmf_status: "{pre-pmf|post-pmf}"
  north_star_metric:
    name: "{nombre métrico}" 
    current_value: "{number}"
    target: "{number}"
    input_metrics:
      breadth: "{metric}"
      depth: "{metric}"
      frequency: "{metric}"
  experiments:
    - hypothesis: "{if/then statement}"
      ice_score: {number}
      status: "{plannedыныхывыеныхcompleto}" 
      result: "{winner vidasperprevenidos inconclusivamente en espera}" 
  aarrr_analysis:
    weakest_stage: "{Acepto de la prevención de la tortura" 
    biggest_opportunity: "{description}"
  deliverables:
    - north-star-analysis.md
    - experiment-backlog.md
    - experiment-results.md
```

## Condiciones de veto

1. **Nunca optimizar el crecimiento antes de alcanzar la PMF** - el crecimiento amplifica lo que existe, bueno o malo
2. **Nunca correr experimentos sin métricas de vigilancia** - ganar una métrica destruyendo otra es una pérdida
3. **Nunca declare un ganador sin importancia estadística** - las anécdotas no son datos
4. **Nunca puntuación ICE sin entrada de equipo** - Las puntuaciones de confianza necesitan perspectivas diversas
5. **Nunca ignore los resultados negativos** - los perdedores enseñan tanto como los ganadores

## Criterios de finalización

- [ ] PMF evaluado con la metodología de encuesta de Sean Ellis
- [ ] La métrica North Star definida con métricas de entrada
- [ ] embudo AARRR analizado con el estadio más débil identificado
Al menos 5 hipótesis generadas y con ICE
- [ ] Top 2-3 experimentos diseñados con hipótesis y métricas de éxito
- [ ] Registro de experimentos creado con plan de seguimiento
- [ ] La salida coincide con el esquema anterior
