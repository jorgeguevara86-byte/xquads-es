---
task: writeHeadline()
responsavel: "@eugene-schwartz"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: product
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: awareness_level
    tipo: enum
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: headline_package
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Nivel de conciencia confirmado o diagnosticado" 
  - "[ ] 10 variaciones de encabezado generadas utilizando 3 fórmulas" 
  - "Top 5 clasificado con puntuación en 4 dimensiones" 
  - "[ ] Capa Psicológica aplicada (Cialdini/Warren principios etiquetados)" 
---

# Task: Write Headline

** ID de la lista: * COPY-M-001
**Version:** 2.0.0
**Command:** `*write-headline`
**Agente: ** Eugene Schwartz (Eugenio Schwartz)eugene-schwartzo Gary Bencivenga ()gary-bencivenga)
**Purpose:** Crear titulares convincentes calibrados al nivel de conciencia del prospecto con psicología de persuasión profunda.

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
Silencioso producto Silenciosidad Silencioso de usuario inducido por Silencio Si Silencio Nombre del producto o del servicio con breve descripción Silencio
Silencios Silencio Silencio Silencio Silencio Silencio Silencio Silencio Para el público descripción Silencio
| awareness_level TEN enum TENIDO Usuarios incitados o inferidos TENIS TENIS ANTERIOR NO TENIENDO, problem-aware, solution-aware, product-aware, most-aware |
Silencio medio Silencioso cadena Silencioso Usuario prompt Silencio No Silencio Dónde aparece el titular (ad, email, página de ventas, VSL) Silencio
Silencio tono Silencioso cuerda Silencioso de usuario insinuar Silencio No ← Tono deseado (urgente, curioso, autorizado, empático) Silencio
| swipe_reference TENED TENIDO TENIDO ANTERIOR NO TENIDO Referencia titular o estilo para emular TENIDO

---

## Preconditions

- Producto o servicio claramente definido
- Público objetivo identificado con al menos demografía básica o psicografía
- Nivel de conciencia determinado (si no se proporciona, el agente debe diagnosticar antes de escribir)

---

# Champion Reference

Estudiar estos real-world campeón titulares antes de escribir:

1. ** "Ellos se reían cuando yo salí al piano — ¡Pero cuando empecé a jugar!"** (John Caples, Escuela de Música de los Estados Unidos) — curiosidad por la historia para los públicos inconscientes
2. ** "¿Haces estas faltas en inglés?"** (Cody de los cerdos) — Pregunta + implícita falla problem-aware audiencias
3. **"Cómo ganar amigos e influencias personas"** (Dale Carnegie) — Beneficio impulsado how-to para solution-aware audiencias
4. ** "El camino del hombre vago a los ricos"** (Joe Karbo) — Promesa contraintuitiva que combina facilidad + resultado
5. **"Amazing Secret Discovered by 37-Aear-Old Mom Exposed by Top Doctors"** (Agora Financial) — Especificación + autoridad + pila de curiosidad

---

## Fases de Ejecución

Fase 1: Diagnóstico de conciencia
1. Confirme el nivel de conciencia de la perspectiva utilizando la escala de 5 niveles de Schwartz
2. Identificar la emoción dominante que conduce la perspectiva (temor, deseo, curiosidad, frustración)
3. Nivel de sensibilización de la hoja de ruta para el enfoque de los titulares:
   - No hay de qué: Lidera con emoción o historia, nunca menciones producto
   - Problema-consciente: Agitar el problema, insinuar la solución
   - Solución-consciente: Diferir el mecanismo o enfoque
   - Información de producto: Prueba de apilamiento, supera las objeciones
   - Lo más consciente: Póngase en oferta, urgencia o trato

### Phase 2: Headline Generation
1. Generar 10 variaciones de los titulares utilizando ángulos distintos
2. Aplicar al menos 3 fórmulas de encabezado diferentes por lote:
   - Cómo llegar
   - Títulos de la pregunta
   - Los titulares de mandos
   - Por qué razón.
   - Títulos testimoniales
   - News/announcement headlines
   - Curiosidad-cabezas de acción
   - Títulos de números específicos
3. Asegurar que cada titular pase la prueba "¿dejaría de dejar de desplazarse?"
4. Longitud de la Vary: incluye corto (menos de 8 palabras), medio (8-15), y largo (15+)

## Fase 3: Capa Psicológica
1. Etiqueta cada titular con el principio Cialdini primario que activa:
   - Reciprocidad, Commitment/Consistency, Social Proof, Authority, Liking, Scarcity, Unity
2. Revise cada encabezado contra la Persuasión de una Sentencia de Blair Warren:
   - ¿Anima sus sueños?
   - ¿Exactúa sus fracasos?
   - ¿Alivia sus miedos?
   - ¿Confirma sus sospechas?
   - ¿Les ayuda a lanzar piedras a sus enemigos?
3. Asegurar que al menos 3 principios diferentes de Cialdini estén representados en los 10 titulares
4. Marcar que Warren palanca cada encabezado tira

### Fase 4: Refinement and Ranking
1. Partitura cada título en 4 dimensiones (1-5 cada uno):
   - Especificación: ¿Promete un resultado concreto?
   - Curiosidad: ¿Crea un bucle abierto?
   - Relevancia: ¿Se ajusta al nivel de conciencia?
   - ¿Es creíble la reclamación?
2. Rango superior 5 por puntuación total
3. Proporción de A/B recomendaciones de pruebas para el primer 2
4. Sugerencia sub-headline pares para el 3 superior

---

## Formato de salida

```markdown
## Headline Package

**Product:** {product}
**Audience:** {audience}
**Awareness Level:** {level}

### Top 5 Headlines (Ranked)

| Rank | Headline | Formula | Specificity | Curiosity | Relevance | Believability | Total | Cialdini Principle | Warren Lever |
|------|----------|---------|-------------|-----------|-----------|---------------|-------|--------------------|--------------|
| 1 | {headline} | {formula} | X | X | X | X | XX | {principle} | {lever} |

### A/B Test Recommendation
**Control:** {headline 1}
**Variant:** {headline 2}
**Rationale:** {why these two}

### Sub-headline Pairings
1. {headline} + {sub-headline}
2. {headline} + {sub-headline}
3. {headline} + {sub-headline}

### Full 10-Headline Bank
1. {headline} — {formula used} — {Cialdini principle}
...
```

---

## Condiciones de veto

- Nunca escriba un titular sin confirmar primero el nivel de conciencia
- NUNCA use clickbait que la copia del cuerpo no puede entregar
- NUNCA ignorar el medio - un encabezado de Facebook ad difiere de un encabezado de página de ventas
- Nunca presentar menos de 10 variaciones
- Nunca utilice el nombre del producto en titulares para públicos sin darse cuenta

---

## Criterios de finalización

Nivel de conciencia confirmado o diagnosticado
- 10 variaciones de los titulares generadas usando fórmulas 3+
Cada titular anotó en 4 dimensiones
- [ ] Top 5 clasificado con racional
- [ ] A/B par de prueba recomendada
- [ ] Pareados subcabezales proporcionados para el 3 superior
[ ] Layer psicologico aplicado - Principios Cialdini etiquetados por título
Blair Warren se identificó por título
- [ ] Formato de salida por plantilla
