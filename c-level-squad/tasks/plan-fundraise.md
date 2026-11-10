---
task: planFundraise()
responsavel: "@vision-chief"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: company
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: round_target
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: fundraise_plan
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Evaluación de la lectura completada (10 dimensiones)" 
  - "[ ] tesis de inversión y arco narrativo elaborado" 
  - "[ ] Lista de destino de inversores construida y empatada" 
---

# Task: Plan Fundraise

** ID de la lista:** CLEVEL-005
**Version:** 1.0.0
**Command:** `*plan-fundraise`
**Agente:** Jefe de Visiónvision-chief) + Arquitecto CMO (cmo-architect)
**Fuente:** Elaborar una estrategia completa de recaudación de fondos para la evaluación de la preparación mediante la preparación de la presentación de proyectos

---

## Inputs

| Entrada | Fuente | Requerido | Descripción |
|-------|--------|----------|-------------|
| `company` TENIDO TENIDO ANTERIOR SI TENIDO Nombre, etapa y descripción de la empresa
| `financials` Silencio Usuario Silencio Sí Silencio Ingresos actuales, velocidad de quemadura, pista de aterrizaje, unidad económica TEN
| `round_target` TENIDO Usuario TENIDO Sí TENIDO Meta subir cantidad y tipo redondo (pre-seed, semilla, A, B) Silencio
| `traction` ← TENIDO TENIDO Sí TENIDO métricas clave de tracción (usuarios, ingresos, tasa de crecimiento) TEN
| `existing_investors` ← Silencio No Silencio Actual cap table and investor relations Silencio
| `use_of_funds` Silencio Usuario Silencio No Silencio Cómo se desplegarán los fondos

## Preconditions

- La compañía existe con tracción demostrable (o plan claro para pre-seed)
- Datos financieros disponibles (incluso si son básicos)
- Marcos ejecutivos cargados (`data/executive-frameworks.yaml`)

## Fases de Ejecución

### Fase 1: Evaluar la lecidad (vision-chief)

1. Aplicar la Evaluación de la Lectura ** (10 dimensiones):
   - **Producto:** ¿Hay un producto de trabajo? ¿Ingreso?
   - ¿Qué? TAM/SAM/SOM ¿Definido? ¿Definido el tiempo de mercado?
   ¿Retención? ¿Tracción de ingresos?
   ¿Los fundadores son complementarios?
   - **Unit Economics:** CAC, LTV, ¿mínculos entendidos?
   - Posición competitiva: ¿Defensibilidad?
   ¿Un camino creíble?
   - **Financiales:** ¿Libros limpios?
   ¿Protegido por IP?
   ¿Los datos soportan las afirmaciones?
2. Partitura cada dimensión 1-5 y calcular **readiness puntuación** (de 50)
   - 40+: Listo para levantar
   - 30-39: Casi listo, primero se subsanan las lagunas
   - 20-29: Prepa significativa necesaria
   -  ⁇ 20: No listo, enfocarse en los fundamentos de negocio
3. Identificar **critical deficiencias** que provocaría el rechazo de los inversores
4. Crear un **gap-closing plan** con plazos
5. Determinación **optimal tiempo** para el aumento

### Fase 2: Define Narrative (vision-chief)

1. Elabore la tesis **Inversión** - por qué es una gran inversión:
   - El problema (grande, creciente, doloroso)
   - La solución (unique, defensible, escalable)
   - El mercado (grande, el tiempo es adecuado)
   - La tracción (prueba que funciona)
   - El equipo (por qué ganarán estos fundadores)
   - La pregunta (cuanto, qué, qué pasa, qué sucede después)
2. Definir el **narrative arc** para el lanzamiento:
   - Una frase que capta la atención
   - Problema: Hacer el dolor visceral y relatable
   - Solución: Mostrar el momento de "aha"
   - Tracción: Deje que los números hablen
   - Mercado: Pinta la oportunidad
   - Modelo de negocio: Mostrar cómo fluye el dinero
   - Equipo: Prove founder-market ajuste
   - Pregunta: Cantidad clara, uso claro, hitos claros
3. Desarrollar **key puntos de prueba** para cada reclamación:
   - Testimonios de clientes
   - Gráficos de crecimiento
   - Desglose de la economía unitaria
   - Comparaciones competitivas
4. Prepararse **objection manipulación** para las 10 principales preocupaciones de los inversores
5. Crear el **one-liner** que explica la compañía en 10 segundos

### Fase 3: Construir la cubierta (cmo-architect)

1. Diseño de la **pitch cubierta** (12-15 diapositivas):
   - Diapositiva 1: Título + one-liner
   - Diapositiva 2: Problema
   - Diapositiva 3: Solución
   - Diapositiva 4: Producto demo/screenshots
   - Diapositiva 5: Tracción y hitos
   - Diapositiva 6: Tamaño del mercado (TAM/SAM/SOM)
   - Diapositiva 7: Modelo de negocio
   - Diapositiva 8: Go-to-market estrategia
   - Diapositiva 9: Paisaje competitivo
   - Diapositiva 10: Equipo
   - Diapositiva 11: Proyecciones financieras (3 años)
   - Diapositiva 12: La solicitud y el uso de fondos
   - Diapositiva 13: Visión/declaración final
2. Cree materiales de apoyo:
   - **Lista de verificación de la sala de datos** (financieros, legales, métricas, contratos)
   - **Resumen ejecutivo** (PDF de 2 páginas)
   - **Modelo financiero** (Proyecciones a 3 años con supuestos)
3. Aplicar los principios de diseño de la plataforma:
   - Un mensaje clave por diapositiva
   - Visualizaciones de datos sobre texto
   - Lenguaje visual consistente
   - Máximo 20 palabras por diapositiva (sin incluir datos)

### Fase 4: Inversores objetivo y preparación de la presentación (vision-chief + cmo-architect)

1. Cree la **investor lista de objetivos** (30-50 inversores):
   - Nivel 1 (sueño): 10 inversores (mejor opción, más difícil de conseguir)
   - Nivel 2 (fuerte): 15 inversores (buen ajuste, realista)
   - Nivel 3 (respaldo): 15-25 inversores (aceptable, accesible)
2. Para cada inversor, investigue:
   - Tesis de inversión y preferencia de etapa
   - Inversiones recientes (empresas de cartera)
   - Partner to target (que se centra en tu sector)
   - Ruta de introducción cálida (quién puede conectarte)
3. Crea la secuencia **outreach **:
   - Semana 1-2: Nivel 3 (lanzamientos de práctica)
   - Semana 3-4: Nivel 2 (generar impulso, recopilar hojas de términos)
   - Semana 5-6: Nivel 1 (apalancamiento del interés existente)
4. Prepárese para la **pitch ejecución**:
   - Presentación de 3 minutos (versión rápida para introducciones)
   - Presentación de 15 minutos (reunión estándar de VC)
   - Presentación de 45 minutos (inmersión profunda con preguntas y respuestas)
   - Sesiones de lanzamientos simulados (al menos 3 antes de lanzamientos reales)
5. Definir **negotiation parámetros**:
   - Rango de valoración (piso y techo)
   - Términos para aceptar, negociar o rechazar
   - Puntos de presión en la línea de tiempo
   - Condiciones de alejamiento

## Formato de salida

```yaml
fundraise_plan:
  company: "{name}"
  round: "{pre-seed|seed|series-a|series-b}"
  target_raise: "{amount}"
  readiness:
    score: "{X/50}"
    status: "{ready|near-ready|prep-needed|not-ready}"
    critical_gaps: ["{gap1}", "{gap2}"]
  narrative:
    one_liner: "{presentación de 10 segundos}" 
    investment_thesis: "{resumen de 2 oraciones}" 
    hook: "{frase inicial}" 
  deck:
    slides: {number}
    status: "{borrador|revisión|final}" 
  investor_pipeline:
    tier_1: {count: 0, warm_intros: 0}
    tier_2: {count: 0, warm_intros: 0}
    tier_3: {count: 0, warm_intros: 0}
  timeline:
    prep_weeks: {number}
    pitch_weeks: {number}
    close_target: "{date}"
  deliverables:
    - readiness-assessment.md
    - investment-narrative.md
    - pitch-deck.md
    - investor-target-list.md
    - data-room-checklist.md
    - financial-model-outline.md
```

## Condiciones de veto

1. **NUNCA haga una propuesta antes de evaluar la preparación**: plantear demasiado pronto daña la reputación ante los inversores
2. **NUNCA comience con inversores de nivel 1**: practique primero en las lower-stakes reuniones
3. **NUNCA presente sin un uso claro de los fondos** -- "crecimiento" no es un uso de los fondos
4. **NUNCA infle métricas o proyecciones**: la debida diligencia de los inversores encontrará la verdad
5. **NUNCA subas sin entender la dilución**: debes saber exactamente a qué estás renunciando

## Criterios de finalización

- [ ] Evaluación de preparación completada (10 dimensiones puntuadas)
- [ ] Brechas críticas identificadas con el plan gap-closing 
- [ ] Tesis de inversión y arco narrativo elaborado
- [ ] Lanzamientos de una sola línea, de 3 y 15 minutos preparados
- [ ] Presentación resumida (12-15 diapositivas)
- [ ] Lista de objetivos de inversores creada (30-50, escalonada)
- [ ] Secuencia de divulgación prevista
- [ ] Parámetros de negociación definidos
- [ ] Lista de verificación de la sala de datos creada
- [ ] La salida coincide con el esquema anterior
