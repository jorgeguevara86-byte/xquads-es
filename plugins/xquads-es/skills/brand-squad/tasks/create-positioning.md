---
task: createPositioning()
responsavel: "@al-ries"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: brand
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: category
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: "Estrategia de posicionamiento" 
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Escala de categorías asignada con posiciones de la competencia" 
  - "[ ] Declaración de posicionamiento formal escrita con alternativas" 
  - "[ ] Se proporcionan pautas de mensajería y puntos de prueba" 
---

# Tarea: Crear Posicionamiento

**ID de tarea:** MARCA-002
**Version:** 1.0.0
**Command:** `*create-positioning`
**Agente:** Al Ries (al-ries)
**Propósito:** Crear una declaración de posicionamiento que ocupe un espacio distinto en la mente del cliente potencial.

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
| marca | cadena | Mensaje de usuario | Sí | Nombre de la marca y descripción actual |
| categoría | cadena | Mensaje de usuario | Sí | Categoría de mercado en la que compite la marca |
| audiencia | cadena | Mensaje de usuario | Sí | Público objetivo |
| competidores | lista | Mensaje de usuario | Sí | Competidores clave con su posicionamiento |
| diferenciador | cadena | Mensaje de usuario | No | Punto de diferencia conocido o sospechado |
| brand_values | lista | Mensaje de usuario | No | Valores y creencias fundamentales |

---

## Preconditions

- Panorama competitivo entendido (quién más compite por el mismo espacio mental)
- Público objetivo definido con sus percepciones actuales

---

## Fases de Ejecución

### Fase 1: Análisis de categorías
1. Defina la escala de categorías: cómo los clientes potenciales organizan mentalmente las opciones
2. Identificar quién posee la posición #1 en la categoría
3. Asigne a todos los competidores sus posiciones reclamadas
4. Identifique las posiciones abiertas (espacios en blanco) en la mente del cliente potencial.
5. Valorar si competir en la categoría existente o crear una nueva:
   - Si #1 es vulnerable: Desafía al líder
   - Si el número 1 es dominante: busque una posición abierta (nicho, atributo o caso de uso)
   - Si no hay una categoría clara: crea la categoría y hazte con ella

### Fase 2: Estrategia de posicionamiento
1. Aplicar los principios de posicionamiento de Ries:
   - **Restringe el enfoque:** Es mejor poseer un nicho pequeño que competir ampliamente
   - **Tener una palabra:** ¿Qué palabra debería tener la marca en la mente del cliente potencial?
   - **Ser lo opuesto:** Si el líder es X, posicionarse como lo opuesto a X
   - **Sé el primero:** Si no puedes ser el primero en la categoría, crea una categoría donde seas el primero
2. Defina el triángulo de posicionamiento:
   - Objetivo: ¿Para quién es esto específicamente?
   - Marco de Referencia: ¿En qué categoría compite?
   - Punto de diferencia: ¿Qué lo hace excepcionalmente mejor para el objetivo?
   - Razón para creer: ¿Qué pruebas respaldan la afirmación?
3. Pruebe el posicionamiento según 3 criterios:
   - ¿Es relevante para el público objetivo?
   - ¿Se diferencia de la competencia?
   - ¿Es creíble y entregable?

### Fase 3: Declaración de posicionamiento
1. Escriba la declaración de posicionamiento formal:
   "Para {público objetivo} que {need/want}, {brand} es el {category} ese {punto de diferencia} porque {razón para creer}."
2. Escribe 3 variaciones con diferente énfasis:
   - Dirigido por objetivos: enfatiza para quién es
   - Basado en beneficios: enfatiza lo que ofrece
   - Dirigido por categorías: enfatiza la nueva categoría o nicho propio.
3. Escribe el eslogan de posicionamiento (5-8 palabras máximo)
4. Defina los puntos de prueba de posicionamiento (3-5 elementos de evidencia)

### Fase 4: Activación de Posicionamiento
1. Traducir el posicionamiento en pautas de mensajería:
   - Mensajes clave por segmento de audiencia
   - Lanzamiento de ascensor (30 segundos)
   - Narrativa de posicionamiento larga (1-2 párrafos)
2. Defina qué significa el posicionamiento para:
   - Desarrollo de productos (qué construir y qué no construir)
   - Marketing (qué decir y qué no decir)
   - Ventas (cómo promocionar y diferenciarse)
3. Identificar riesgos de posicionamiento:
   - Escenarios de respuesta de la competencia
   - Cambios de categoría que podrían invalidar el puesto
4. Establecer la cadencia de revisión de posicionamiento

---

## Formato de salida

```markdown
## Positioning Strategy: {Brand Name}

**Category:** {category}
**Target:** {audience}
**Owned Word:** {the word this brand will own}
**Strategy Type:** {challenge-leader / find-niche / create-category}

---

### Category Map

| Position | Brand | Claim |
|----------|-------|-------|
| #1 | {brand} | {their position} |
| #2 | {brand} | {their position} |
| Open | — | {white space} |
| **Ours** | **{brand}** | **{our position}** |

### Positioning Statement
"For {target} who {need}, {brand} is the {category} that {difference} because {proof}."

### Alternative Versions
1. **Target-led:** {version}
2. **Benefit-led:** {version}
3. **Category-led:** {version}

### Tagline
{5-8 word tagline}

### Proof Points
1. {evidence}
2. {evidence}
3. {evidence}

### Messaging Guidelines
**Elevator Pitch:** {30-second version}
**Key Messages:**
- For {segment 1}: {message}
- For {segment 2}: {message}

### Positioning Narrative
{1-2 paragraph story of the positioning}

### Risks and Mitigations
| Risk | Likelihood | Mitigation |
|------|-----------|------------|
```

---

## Condiciones de veto

- NUNCA posicione sin analizar el panorama competitivo: el posicionamiento es relativo
- NUNCA reclames una posición que la marca no pueda poseer de manera creíble
- NUNCA intentes ser todo para todos: el enfoque limitado gana
- NUNCA posicione únicamente basándose en el precio: es la estrategia de posicionamiento más débil
- NUNCA cambies de posicionamiento sin entender lo que la marca tiene actualmente en mente

---

## Criterios de finalización

- [ ] Escala de categorías asignada con posiciones de la competencia
- [ ] Espacio en blanco identificado
- [ ] Estrategia de posicionamiento seleccionada (reto, nicho o creación)
- [ ] Declaración de posicionamiento formal escrita con alternativas
- [ ] Lema creado
- [ ] Puntos de prueba definidos
- [ ] Se proporcionan pautas de mensajería
- [ ] Riesgos identificados con mitigaciones
