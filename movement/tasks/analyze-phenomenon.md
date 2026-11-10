---
task: analyzePhenomenon()
responsavel: "@fenomenologo"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: subject
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: audience
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: phenomenological_analysis
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Experiencia viva identificada con estructuras esenciales" 
  - "[ ] Tensión colectiva mapeada con calificación de intensidad" 
  - "[ ] Potencial de movimiento valorado con justificación" 
---

# Task: Analyze Phenomenon

** ID de la lista:** MOVIMIENTO-002
**Version:** 1.0.0
**Command:** `*analyze-phenomenon`
**Agente:** Fenomenolog (fenomenolog)
**Purpose:** Realizar análisis fenomenológicos para identificar experiencias vividas compartidas que puedan provocar un movimiento

---

## Inputs

| Entrada | Fuente | Requerido | Descripción |
|-------|--------|----------|-------------|
| `subject` Silencio invocar a un usuario Silencio Silencio El fenómeno, la experiencia o la tensión para analizar Silencio
| `audience` Silencio invocar a un usuario Silencio Silencio El grupo cuya experiencia se está analizando Silencio
| `context` Silencio Silencio No Silencio Cultural, de mercado o de contexto social
| `data_sources` ← No TENEDA Entrevistas, encuestas, redes sociales, foros TEN

## Preconditions

- Marcos de movimiento cargados (`data/movement-frameworks.yaml`)
- El sujeto es una experiencia humana, no una característica del producto
- El público objetivo es identificable y accesible

## Fases de Ejecución

### Fase 1: Identificar la experiencia vivida

1. Definir el **phenomenon** - qué experiencia se está examinando
2. Hipótesis de la bobina -- suspende las preconcepciones sobre la experiencia (epoché)
3. Recopilación*first-person cuentas** - cómo la gente describe esta experiencia en sus propias palabras
4. Identificar **essential estructuras** - qué elementos están siempre presentes en la experiencia
5. Mapa de la **emotional paisaje** - qué sentimientos acompañan la experiencia
6. Document raw findings in unfiltered form

## Fase 2: Mapa de la Tensión Colectiva

1. Identificar el **gap# Entre cómo son las cosas y cómo la gente quiere que sean
2. Nombre del **frustration** -- qué dolor específico o fricción siente la gente
3. Detectar **systemic patrones** - es esta tensión personal o estructural
4. Evaluación **tension intensidad** en una escala de 5 puntos:
   - 1: La molestia leve (potencia de chispa débil)
   - 2: La frustración recurrente (potencia moderada)
   - 3: Punto de dolor activo (buen potencial)
   - 4: Conflicto de nivel de identidad (potencia fuerte)
   - 5: Tensión existencial (movement-grade potencial)
5. Map who else feel this tension -- scope and scale

### Phase 3: Find Shared Narrative

1. Extraer el **common historia** La gente se cuenta sobre esta experiencia
2. Identificar el **villain** -- ¿qué o quién es culpado por la tensión
3. Identificar el **hero arquetipo** - que hace gente aspira a convertirse en
4. Encontrar el **turning punto** - ¿Qué cambiaría todo
5. Prueba de resonancia narrativa - ¿esta historia se siente universalmente verdadera para el público
6. Destilarse en un **narrative kernel** - un párrafo que captura la historia compartida

### Fase 4: Aspiración de partículas

1. Definir el **desired futuro estado** - cómo es el mundo cuando la tensión se resuelve
2. Nombre del **transformation** -- qué cambios para el individuo
3. Nombre del **impact** - qué cambios para el colectivo
4. Artesanía el **aspiration declaración** - una frase que captura el sueño
5. Validar: ¿esta aspiración siente ambiciosa y alcanzable
6. Potencial de movimiento de tarifas: LOW / MEDIUM / ALTO / CRITICAL

## Formato de salida

```yaml
phenomenological_analysis:
  phenomenon: "{name}"
  audience: "{grupo de metag.}" 
  lived_experience:
    essential_structures: ["{element1}", "{element2}", "{element3}"]
    emotional_landscape: ["{emotion1}", "{emotion2}", "{emotion3}"]
  collective_tension:
    gap: "{ Estado actual vs estado deseado}" 
    frustration: "{Nombrada frustración}" 
    intensity: {1-5}
    scope: "{personales incomunity" 
  shared_narrative:
    villain: "{what/who es culpado" 
    hero_archetype: "¿Quién aspira ser?" 
    turning_point: "¿Qué cambiaría todo?" 
    narrative_kernel: "{un párrafo compartido historia}"
  aspiration:
    desired_future: "{Estado de la diversión}" 
    transformation: "{cambio individual}" 
    impact: "{cambio colectivo}" 
    aspiration_statement: "{una frase}" 
  movement_potential: "{LOW resistMEDIUM uponHIGH sometidaCRITICAL}" 
```

## Condiciones de veto

1. **Nunca analice una característica de producto como fenómeno** - La fenomenología estudia la experiencia humana, no los productos
2. **Nunca inventar experiencias vividas** - todos los hallazgos deben rastrear a cuentas humanas reales
3. **Nunca saltar el paso entre corchetes** - hipótesis contaminar el análisis
4. **NUNCA potencial de movimiento de tasa por encima de MEDIUM sin intensidad  ⁇ = 3** - tensión débil no puede sostener un movimiento
5. **Nunca produce un núcleo narrativo sin validar la resonancia** - una historia que no resona es la ficción

## Criterios de finalización

- [ ] Experiencia viva identificada con estructuras esenciales documentadas
- [ ] Tensión colectiva mapeada con calificación de intensidad (1-5)
- [ ] narrativa compartida destilada con villano, héroe, y punto de inflexión
- [ ] Aspiración articulada con transformación e impacto
- [ ] Potencial de movimiento valorado con justificación
[ ] núcleo narrativo escrito y resonance-tested
- [ ] La salida coincide con el esquema anterior
