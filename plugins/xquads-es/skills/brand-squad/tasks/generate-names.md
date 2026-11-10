---
task: generateNames()
responsavel: "@naming-strategist"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: what
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: positioning
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: "Estrategia de nombres con finalistas" 
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] 30-50 candidatos sin procesar generados en más de 4 categorías" 
  - "[ ] Todos los candidatos puntuaron en 7 criterios" 
  - "[ ] Final 3-5 presentado con perfiles completos" 
---

# Tarea: Generar nombres

**ID de tarea:** MARCA-006
**Version:** 1.0.0
**Command:** `*generate-names`
**Agente:** Estratega de nombres (naming-strategist)
**Propósito:** Desarrollar el nombramiento de candidatos a través de una metodología creativa estructurada y evaluación estratégica.

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
| qué | cadena | Mensaje de usuario | Sí | Qué se denomina (empresa, producto, característica, servicio) |
| posicionamiento | cadena | Mensaje de usuario | Sí | Posicionamiento o propuesta de valor |
| audiencia | cadena | Mensaje de usuario | Sí | Público objetivo |
| tono | cadena | Mensaje de usuario | No | Tono deseado (moderno, clásico, juguetón, serio, técnico) |
| restricciones | lista | Mensaje de usuario | No | Límites de longitud, requisitos de idioma, sonidos a evitar |
| domain_needed | booleano | Mensaje de usuario | No | Si importa la disponibilidad del dominio .com |
| category_names | lista | Mensaje de usuario | No | Nombres de competidores para evitar similitudes |

---

## Preconditions

- Lo que se está nombrando está claramente definido
- El posicionamiento proporciona suficiente contexto para generar nombres relevantes

---

## Fases de Ejecución

### Fase 1: Estrategia de nombres
1. Definir los objetivos de naming:
   - Debe transmitir: {lo que el nombre debe comunicar}
   - Debe sentir: {la calidad emotional/tonal }
   - Debe evitar: {asociaciones, sonidos o superposición de competidores}
2. Seleccione categorías de nombres para explorar:
   - **Descriptivo:** Dice lo que hace (PayPal, YouTube)
   - **Sugerente:** Implica una cualidad o beneficio (Slack, Sprint)
   - **Resumen:** Acuñado o inventado (Kodak, Xerox)
   - **Metafórico:** Significado prestado (Amazon, Apple)
   - **Acrónimo:** Iniciales o abreviatura (IBM, BMW)
   - **Founder/Personal:** Nombrado en honor a una persona (Tesla, Disney)
   - **Compuesto:** Dos palabras combinadas (Facebook, Snapchat)
3. Asigne la exploración en al menos 4 categorías
4. Definir los criterios de evaluación antes de generar nombres.

### Fase 2: Generación de nombre
1. Genere entre 30 y 50 nombres candidatos sin procesar en las categorías seleccionadas.
2. Para cada categoría, utilice técnicas específicas:
   - Descriptivo: Combina palabras funcionales con modificadores
   - Sugerente: Utilice etimología, raíz de palabras y simbolismo de sonido.
   - Resumen: Crea nuevas palabras usando una fonética agradable
   - Metafórico: Mitología, naturaleza, ciencia y cultura mía
   - Compuesto: emparejar combinaciones de palabras inesperadas
3. Aplicar principios fonéticos:
   - Los nombres fuertes suelen comenzar con consonantes duras (K, T, P, B)
   - Los nombres cortos (1-3 sílabas) son más memorables
   - Las terminaciones vocales se sienten amigables y accesibles.
   - Las terminaciones de consonantes se sienten fuertes y decisivas.
4. Verifique cada nombre para detectar significados no deseados en los principales idiomas.

### Fase 3: Evaluación y preselección
1. Califique cada nombre según 7 criterios (1-5 cada uno):
   - **Memorabilidad:** Fácil de recordar después de escuchar una vez
   - **Pronunciabilidad:** Fácil de decir sin explicación
   - **Deletreabilidad:** Fácil de escribir después de escuchar
   - **Características distintivas:** Diferente a la competencia
   - **Relevancia:** Se conecta al posicionamiento o valor
   - **Escalabilidad:** Funciona a medida que la marca crece hacia nuevas áreas
   - **Resonancia emocional:** Evoca el sentimiento correcto
2. Clasifique por puntuación total y seleccione los 10 mejores
3. Del top 10, recomienda del 3 al 5 final con toda la justificación
4. Tenga en cuenta la posible disponibilidad del dominio para los finalistas (si el dominio es importante)

### Fase 4: Presentación del nombre
1. Para cada finalista, proporcione:
   - Guía de nombres y pronunciación
   - Categoría y etimología
   - Lo que comunica
   - Cómo puntúa en todos los criterios
   - Posible emparejamiento de eslogan
   - Posibilidades visuales (cómo podría verse como marca denominativa)
2. Proporcione el "caballo oscuro": un nombre inesperado que podría funcionar
3. Sugerir los siguientes pasos: búsqueda de marcas, adquisición de dominios, pruebas de grupos focales

---

## Formato de salida

```markdown
## Naming Strategy: {What Is Being Named}

**Positioning:** {statement}
**Tone:** {desired tone}
**Audience:** {audience}

---

### Top 5 Finalists

#### 1. {Name}
**Category:** {type}
**Etymology:** {origin and meaning}
**Communicates:** {what it says about the brand}
**Pronunciation:** {phonetic guide}
**Tagline Pairing:** {suggested tagline}
**Scores:** Mem {X} / Pro {X} / Spe {X} / Dis {X} / Rel {X} / Sca {X} / Emo {X} = **{Total}/35**

#### 2-5: ...

### Dark Horse
{Unexpected option with rationale}

### Full Candidate List

| # | Name | Category | Total Score | Notes |
|---|------|----------|-------------|-------|

### Rejected with Rationale
| Name | Why Rejected |
|------|-------------|

### Next Steps
1. Trademark search for top 3
2. Domain availability check
3. Audience reaction testing
```

---

## Condiciones de veto

- NUNCA envíe menos de 30 candidatos sin procesar: la cantidad permite la calidad
- NUNCA recomiendes nombres sin comprobar si hay significados negativos en otros idiomas
- NUNCA recomiendes nombres que sean impronunciables sin una guía
- NUNCA generes nombres de una sola categoría: la diversidad revela las mejores opciones
- NUNCA omita los criterios de evaluación: la intuición no es una estrategia para nombrar

---

## Criterios de finalización

- [ ] Estrategia de naming definida con objetivos y restricciones
- [ ] 30-50 candidatos sin procesar generados en más de 4 categorías
- [ ] Todos los candidatos puntuaron en 7 criterios
- [ ] Top 10 identificados y clasificados
- [ ] Final 3-5 presentado con perfiles completos
- [ ] Opción Dark Horse incluida
- [ ] Nombres rechazados documentados con justificación
- [ ] Próximos pasos definidos (marca, dominio, pruebas)
