---
task: setVision()
responsavel: "@vision-chief"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: company
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: industry
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: strategic_vision
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Declaraciones de misión y visión elaboradas" 
  - "[ ] 3-5 pilares estratégicos establecidos con OKRs" 
  - "[ ] Plancha de 3 años creada con temas anuales" 
---

# Task: Set Vision

** ID de la lista:** CLEVEL-001
**Version:** 1.0.0
**Command:** `*set-vision`
**Agente:** Jefe de Visiónvision-chief)
**Purpose:** Definir la visión de la empresa, la misión, los pilares estratégicos, y crear un multi-year roadmap

---

## Inputs

| Entrada | Fuente | Requerido | Descripción |
|-------|--------|----------|-------------|
| `company` Silencio invocar usuario Silencio Sí Silencio Nombre y descripción de la empresa Silencio
| `industry` Silencio invocar a su usuario Silencioso industria o sector del mercado
| `current_state` Silencioso usuario Silencio Sí Silencio etapa actual, ingresos, tamaño del equipo, retos TENIDO
| `ambition` TENIDO Usuario TENIDO No TENIDO Dónde el fundador quiere estar en 3-5 años TENIDO
| `existing_mission` Silencio Usuario Silencio No Silencio mission/vision declaraciones voca

## Preconditions

- La empresa existe o está en pre-launch con un concepto definido
- El titular de la autoridad de decisión está comprometido
- Marcos ejecutivos cargados (`data/executive-frameworks.yaml`)

## Fases de Ejecución

## Fase 1: Evaluar el estado actual

1. Conducta a **strategic evaluación de la situación**:
   - ¿Dónde estamos ahora? (revenue, equipo, producto, posición de mercado)
   - ¿Cuáles son nuestras fortalezas y moats?
   - ¿Cuáles son nuestras vulnerabilidades críticas?
   - ¿Qué fuerzas externas están conformando nuestra industria?
2. Aplicar ** Análisis de 5 Fuerzas de Portter**:
   - Intensidad competitiva de rivalidad
   - Amenaza de nuevos participantes
   - La amenaza de los sustitutos
   - Poder de negociación de proveedores
   - Poder de negociación de compradores
3. Identificar el **strategic brecha** - distancia entre el estado actual y la ambición
4. Evaluación **organizational preparación** para la transformación
5. Conclusiones de los documentos en un resumen de la evaluación estratégica

### Fase 2: Define Misión y Visión

1. Elabore la declaración de la misión ** (por qué existimos hoy):
   - Formato: "Nosotros [acción] para [audiencia] por [método] para que [de acuerdo]"
   - Debe ser lo suficientemente específico para guiar las decisiones diarias
   - Debe ser lo suficientemente amplio para permitir el crecimiento
2. Elaborar la declaración **Vision** (donde vamos):
   - Formato: "Un mundo donde [estado futuro deseado]"
   - Horario: 5-10 años de horizonte
   - Debe ser inspirador aún alcanzable
3. Definir ** Valores del contrato** (3-5 valores):
   - Cada valor debe tener una definición conductual
   - Los valores deben ser distintivos (no latitudes corporativas genéricas)
   - Prueba: "Debemos sacrificar short-term ¿beneficio por este valor?"
4. Crear la cascada **Vision-Mission-Strategy**:
   - Visión (por qué) √Misión de confianza (qué) √≥ Estrategia (cómo) √cticas (when/where)
5. Validar: ¿Sabe un nuevo empleado leer estos datos qué priorizar?

### Fase 3: Establecer Pilares Estratégicas

1. Definir **3-5 Pilares estratégicos** - las principales apuestas para los próximos 3 años:
   - Cada pilar debe conectarse directamente a la visión
   - Cada pilar debe ser mensurable con resultados claros
   - Los Pilares deben cubrir colectivamente la brecha estratégica
2. Para cada pilar, definir:
   - **Objetivo:** Lo que queremos lograr
   ** Resultados clave:** 2-3 resultados mensurables (estilo de OKR)
   - **Owner:** Que papel de nivel C lidera este pilar
   - **Tiempo:** hitos de 12 meses
   - **Dependencias:** Lo que debe ser cierto para que esto tenga éxito
3. Aplicar la matriz **BCG** a las ofertas actuales y planificadas:
   - Estrellas (alto crecimiento, alta participación): invertir
   - Vacas en efectivo (bajo crecimiento, alta participación): cosecha
   - Marcos de preguntas (alto crecimiento, baja participación): decidir
   - Perros (bajo crecimiento, baja participación): inmersión
4. Identificar **strategic trade-offs* -- lo que NO haremos
5. Validar: ¿ciertan colectivamente los pilares la brecha estratégica?

### Phase 4: Create Roadmap

1. Elaborar una hoja de ruta estratégica **3 años**:
   - Año 1: Fundación (construir capacidades, lograr hitos)
   - Año 2: Escala (creer lo que funciona, cortar lo que no)
   - Año 3: Transformación (reach vision-level impacto)
2. Por cada año, definir:
   - **Tema:** Una palabra que capta el enfoque del año
   * Prioridades generales:** Principales resultados
   **Inversiones clave:** Donde fluirán los recursos
   - ** Criterios de éxito: * Cómo sabemos que estamos en camino
3. Identificar **strategic puntos de inflexión** - decisiones que deberán adoptarse
4. Crear el **quarterly cadencia de examen** - cuándo y cómo se examina la estrategia
5. Definer **pivot desencadenantes** - condiciones que requerirían revisión de la estrategia

## Formato de salida

```yaml
strategic_vision:
  company: "{name}"
  mission: "{declaración de la misión}" 
  vision: "{declaración de la vista}" 
  core_values: ["{value1}", "{value2}", "{value3}"]
  strategic_pillars:
    - name: "{pillar}"
      objective: "{what}"
      key_results: ["{kr1}", "{kr2}"]
      owner: "{c-level role}"
      timeline: "{milestones}"
  porters_five_forces:
    rivalry: "{low habitmedium habithigh}" 
    new_entrants: "{low habitmedium habithigh}" 
    substitutes: "{low habitmedium habithigh}" 
    supplier_power: "{low habitmedium habithigh}" 
    buyer_power: "{low habitmedium habithigh}" 
  roadmap:
    year_1: {theme: "", priorities: [], investments: []}
    year_2: {theme: "", priorities: [], investments: []}
    year_3: {theme: "", priorities: [], investments: []}
  review_cadence: "quarterly"
  deliverables:
    - strategic-assessment.md
    - vision-mission-values.md
    - strategic-pillars.md
    - 3-year-roadmap.md
```

## Condiciones de veto

1. **Nunca definir la visión sin evaluar el estado actual** - la visión sin fundamento es el engaño
2. **Nunca tienen más de 5 pilares estratégicos** - el enfoque requiere decir que no
3. **Nunca saltar el trade-offs**... la estrategia es tanto sobre lo que no harás
4. **Nunca crear una hoja de ruta sin puntos de revisión trimestrales** - la estrategia debe adaptarse
5. **Nunca escriba valores genéricos** -- "integridad" y "excelencia" no significan nada sin definiciones conductuales

## Criterios de finalización

- Estado actual evaluado con 5 Fuerzas de Porter
- [ ] Declaración de la Misión elaborada (específica y factible)
- [ ] Declaración de visión elaborada (inspirante y time-bound)
- [ ] 3-5 valores básicos definidos con descripciones conductuales
- 3-5 pilares estratégicos con OKRs y propietarios
- Matriz BCG aplicada a las ofrendas
- [ ] Hoja de ruta de 3 años creada con temas anuales
- [ ] Pivot dispara y revisa cadence define
- [ ] La salida coincide con el esquema anterior
