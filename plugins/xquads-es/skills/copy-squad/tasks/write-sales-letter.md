---
task: writeSalesLetter()
responsavel: "@gary-halbert"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: product
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: offer
    tipo: object
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: sales_letter
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Gran promesa y conductor emocional identificado" 
  - "[ ] Carta sigue la estructura AIDA con prueba en todo" 
  - "[ ] CTA aparece mínimo 3 veces con secciones de P.S." 
---

# Task: Write Sales Letter

** ID de la lista:** COPY-002
**Version:** 1.0.0
**Command:** `*write-sales-letter`
Gary Halbertgary-halbert)
**Purpose:** Escribe un texto completo long-form carta de ventas que vende a través de narración y conexión emocional.

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
Silencioso Silencio Silencio Silencio Silencio Silencio Silencio Silencio Product/service con características clave y beneficios Silencio
Silencio audiencia Silencios Silenciosidad de usuario incitar a tu usuario Silencios públicos con puntos de dolor y deseos Silencio
Silencio oferta Silencioso objeto Silencio Usuario prompt Silencio Sí Silencio Precio, garantía, bonos, elementos de urgencia Silencio
| awareness_level TEN enum TENIDO Usuario prompt TEN No TENCIÓN Los 5 niveles de Schwartz — default to problem-aware |
| proof_elements Silencio, lista de casos, estudios de casos Silenciosos, estudios de casos, videos, videos, videos, videos, videos, videos, videos, videos, videos, videos, videos, videos, videos, videos, videos, videos, videos, videos, videos, videos, videos, videos, videos, videos, noticias, noticias, noticias, noticias, noticias, noticias, noticias, noticias, noticias, noticias,
Silencio tono Silenciosidad Silencioso de usuario incitar a la conversación, personal, urgente Silencio
| word_count_target Silencio número Silencio Usuario prompt Silencio No Silencio Por defecto 2000-4000 palabras Silencio

---

## Preconditions

- Beneficios del producto claramente articulados (no sólo características)
- Al menos un elemento de prueba disponible (testimonio, estatus o credenciales)
- Estructura de la oferta definida (precio, garantía, bonos)

---

## Fases de Ejecución

### Phase 1: Research and Strategy
1. Identificar la emoción más poderosa que conduce la perspectiva
2. Definir la "gran promesa" — un resultado transformador
3. Mapear el estado actual de la perspectiva vs. estado deseado
4. Identificar el mecanismo único que hace que este producto sea diferente
5. Catalogar todos los elementos de prueba y rango por potencia persuasiva
6. Determinar la objeción primaria que debe superarse

### Fase 2: Estructurar la Carta
1. Destacando la estructura clásica de Halbert:
   - Atención: Headline + abertura que agarra por la garganta
   - Interés: Historia o revelación impactante que construye intriga
   - Deseo: Beneficios, pruebas y future-pacing
   - Acción: Oferta, garantía, urgencia y CTA clara
2. Planifique el arco emocional: curiosidad por temer a la esperanza de urgencia
3. Identificar 3-5 ganchos de transición para mantener la "slippery diapositiva"
4. Elementos de prueba de posición estratégicamente (creibilidad temprana, prueba social media, inversión tardía del riesgo)

### Fase 3: Escribe el Borrador
1. Escribe el titular y el plomo (primeras 300 palabras) — este es el 80% de la batalla
2. Construir la sección de historia con narrativa personal y relatable
3. La transición de la historia al producto revela con un párrafo "puente"
4. Beneficios de la estaca usando balas (estilo de las asociaciones)
5. Prueba de capas en todo el mundo — nunca más de 3 párrafos sin prueba
6. Escribe la sección de oferta: precio de anclaje, bonos, garantía
7. Cierre con urgencia, escasez y un solo CTA claro
8. Agregue secciones de P.S. (Movimiento de firma de Halbert) — restar oferta + añadir la razón de bonificación

### Fase 4: Polaco y Revisión
1. Lea en voz alta — corte cualquier cosa que rompe el flujo de conversación
2. Verificar todas las reclamaciones se apoyan por prueba
3. Asegurar que la carta pueda ser entendida por un séptimo grado
4. Compruebe que el CTA aparece al menos 3 veces
5. Confirmar la garantía es destacada y audazmente declarada

---

## Formato de salida

```markdown
## Sales Letter: {Product Name}

**Target:** {audience}
**Awareness:** {level}
**Word Count:** {count}
**Emotional Driver:** {primary emotion}
**Big Promise:** {one-line promise}

---

### [HEADLINE]
{headline}

### [SUB-HEADLINE]
{sub-headline}

### [LETTER BODY]
{full sales letter with natural paragraph breaks}

### [P.S. SECTIONS]
P.S. {first postscript}
P.P.S. {second postscript}

---

### Writer's Notes
- **Lead type:** {story, proclamation, prediction, secret, problem-solution}
- **Key proof used:** {list}
- **Primary objection addressed:** {objection + how}
- **Suggested split test:** {element to test}
```

---

## Condiciones de veto

- NUNCA escribe sin una oferta definida (precio + garantía mínima)
- Nunca se abre con el nombre del producto para unaware/problem-aware audiencias
- Nunca escriba una carta sin al menos un elemento de prueba
- Nunca use voz pasiva en el CTA
- Nunca se someten sin secciones de P.S. - son los second-most-read elemento

---

## Criterios de finalización

- Una gran promesa y un conductor emocional identificado
La carta sigue la estructura de AIDA con el estilo personal de Halbert
- El titular y el plomo son piezas independientes.
- [ ] elementos de prueba tejidos a lo largo (no tirados en una sección)
- [ ] Oferta claramente declarada con el anclaje de precios y garantía
- Al menos 2 secciones de P.S. incluidas
- [ ] CTA parece mínimo 3 veces
- [ ] Lecibilidad a nivel 7o o inferior
- [ ] Notas de escritores incluidas con racional estratégico
