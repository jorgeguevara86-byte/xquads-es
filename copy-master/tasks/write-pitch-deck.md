---
task: writePitchDeck()
responsavel: "@oren-klaff"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: business
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: audience
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: pitch_deck_copy
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] método STRONG totalmente ejecutado (todos los 6 elementos)" 
  - "[ ] Estrategia de control de marcos definida para cada sección" 
  - "[ ] Intriga + arco de tensión mantenido en todo" 
  - "[ ] Capa Psicológica aplicada (Cialdini/Warren principios etiquetados)" 
---

# Task: Write Pitch Deck Copy

** ID de la lista:** COPY-M-013
**Version:** 2.0.0
**Command:** `*write-pitch-deck`
*Oren Klaff*oren-klaff)
**Purpose:** Escribe copia de la cubierta de campo usando el método STRONG con control de marco y psicología de persuasión en capas.

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
Silencio Silencio Silencio Silencio Silencio Silencio Silencio Silencio Silencio Business/product con la propuesta de valor básico TEN
Silencios en la audiencia Silencio en la vida Insistencia de usuario Silenciosos inversores, partners, clientes, internal-stakeholders |
Silencio preguntar Silencio cadena Silencio Usuario prompt Silencio Silencio Silencio Lo que estás pidiendo (cuarto financiero, asociación, acuerdo, buy-in) |
Silencio viv miento Silencio objeto Silencio Usuario prompt Silencio No Silencio Revenue, users, growth rate, hitos Silencio
| market_data Silencioso objeto Silencio Usuario prompt Silencio No Silencio TAM, SAM, SOM, tendencias de mercado Silencio
Silencio equipo Silencio lista Silencio Usuario prompt Silencio No Silencio Miembros del equipo clave y credenciales Silencio
| competitive_advantage Silencio Silencio Silencio Silencio Usuario prompt Silencio No Silencio Única moat o injusta ventaja
| pitch_context Silencio Silencio Silencio Silencio Silencio Silencio Where/how el lanzamiento se entregará (papel, día de demostración, virtual, 1-on-1) |

---

## Preconditions

- Proposición de valor empresarial claramente definida
- Tipo de audiencia identificado (los diferentes públicos requieren diferentes marcos)
- El "ask" es específico y cuantificado
- Al menos algunos datos de tracción o puntos de prueba disponibles

---

# Champion Reference

Estudiar estos real-world campeón lanza antes de escribir:

1. ** La cubierta original de la perra de Arbnb** (2009) — Clean problem/solution framing, tamaño del mercado con especificidad, prueba de tracción, conciso preguntar
2. **El método de "Pitch Any" de Oren Klaff** — Control de marco, intriga, tension-release patrón, alineación del estado
3. **Steve Jobs iPhone Launch** (2007) — "Tres productos revolucionarios" patrón interrumpe, demonstration-driven prueba, dominio del estado
4. **Plantilla de cubierta de punta de capital de Sequoia** — El estándar: Problema, solución, ¿por qué ahora, mercado, competencia, producto, equipo, finanzas, pregunte
5. **La cubierta transparente de la marca de la marca de la burbuja** — Metrics-forward, honesta sobre los desafíos, la prueba social a través de la transparencia

---

## Fases de Ejecución

## Fase 1: Marco de Métodos ESTRONG

1. **S -- Establecer el marco:** Establecer el marco antes de que el público establezca el suyo
   - Marco de poder: Ponerse como premio, no como el suplicante
   - Marco de tiempo: Crear urgencia ("tengo 20 minutos para mostrarte algo importante")
   - Marco analista: No te metas en los detalles de la hoja de cálculo - quédate en big-picture
   - Marco de premios: Necesitan calificar para trabajar con USTED
2. **T -- Cuéntase la historia:** Árco narrativo que crea intriga
   - Hombre...in-the-jungle: Lucha - confianza Discovery - Confeccionamiento
   - Usar la novedad y la tensión para mantener la atención
   - Nunca sea aburrido - si el cerebro de la audiencia se desconecta, pierde
3. **R - Revelar la Intriga:** El "momento de la acción" que cambia todo
   - Lo que la mayoría de la gente no sabe de esto market/opportunity
   - La visión contraintuitiva que hace que este trabajo
   - La ventaja injusta que hace que la competencia sea irrelevante
4. **O -- Ofrezca el Premio**: Posición del acuerdo como una oportunidad escasa
   - No es que pidas dinero, es que ofreces un asiento en la mesa.
   - Enmarcar la ventana de oportunidad: "Si no ahora, entonces nunca"
   - Que el público se apoye para conseguir el acuerdo
5. **N -- Nail the Hookpoint:** El momento en que deben decidir
   - Borrar, pregunta específica con términos
   - Marco binario: dentro o fuera
   - No hay espacio para "déjenme pensar en ello" - crear urgencia para decidir
6. **G -- Tomar la decisión:** Cerrar con el control de marco
   - El tiempo se cierra: "Necesito una decisión para el viernes"
   - "Esto puede no ser adecuado para todos"
   - Siguientes pasos: exactamente lo que sucede después de que digan sí

## Fase 2: Capa Psicológica

1. Mapa Cialdini principios en la estructura de lanzamiento:
   - **Autoridad:** Credenciales, tracción, equipo, menciones de los medios (sin salida)
   - **Seguridad:** Asignación limitada, ronda de cierre, ventana de oportunidad
   - **Proofo Social:** Otros inversores, clientes, asesores ya
   - **Comité:** Obtenga pequeños síes por todo ("¿Esto resona?")
   - **Escupiendo:** Historia personal, visión compartida, relatabilidad
   - Unity: * "Estamos construyendo algo juntos" — misión compartida enmarcando
   - **Reciprocidad:** Comparte una valiosa información que pueden usar incluso si no invierten
2. Aplicar las palancas de Blair Warren:
   - Anime sueños: Pinta la enorme boca
   - Justificar los fracasos: "Las inversiones de pas en este espacio fallaron porque carecían de X"
   - Teme a Allay: Desarriesgar la inversión con hitos y datos
   - Confirma sospechas: "Probablemente has notado [la tendencia del mercado] — tienes razón"
   - Tiren piedras a los enemigos: Los incumbentes son vulnerables porque...
3. Técnicas de control de marcos por sección:
   - Nunca dejes que el público te ponga un "fragmento de poder"
   - Usar la conciencia de "beta traps" - no caer en posición subserviente
   - Mantener el estado controlando la temperatura emocional de la habitación

## Fase 3: Escribir por escrito

1. ** Diapositiva del texto:** one-liner, no nombre de empresa
2. **Problema Slide:** Vivid, punto de dolor específico con datos
3. **Solution Slide:** Su mecanismo único en una oración
4. **Por qué ahora deslizamiento:** Tiempo de mercado / punto de convergencia / inflexión
5. ** Tamaño del mercado Slide:** TAM - título SAM - título SOM con bottom-up lógica
6. **Deslice del producto:** Demo o captura de pantalla con 3 diferenciadores clave
7. **Diapositiva de tracción:** Métricas que demuestran el impulso (el gráfico subiendo y a la derecha)
8. ** Deslización del modelo de negocios:** Cómo hacer dinero, economía de unidad
9. **Diapositiva de la competencia:** Matriz de posicionamiento (no comparación de características)
10. **Diapositiva del equipo:** Por qué este equipo gana (creencias + ventaja injusta)
11. **La diapositiva de la pregunta:** Cantidad específica, uso de fondos, términos, plazo
12. **Diapositiva de la visión:** La imagen de 10 años que los hace querer ser parte de ella

## Fase 4: Notas de entrega

1. Escribe notas de altavoz por diapositiva (qué decir, no qué leer)
2. Marcos momentos de control de marcos (donde empujar hacia atrás, redireccionar o tomar control)
3. Identificar los desencadenantes de "cognición caliente" (latidos emocionales que superan el pensamiento analítico)
4. Plan para el croc-brain: mantener la imagen, mantener la novela, seguir
5. Preparar respuestas a las objeciones para los 5 problemas más probables
6. Defina los momentos de "página de intriga": líneas diseñadas para crear curiosidad

---

## Formato de salida

```markdown
## Pitch Deck Copy: {Company/Product Name}

**Method:** STRONG (Klaff)
**Audience:** {audience type}
**The Ask:** {specific request}
**Duration:** {X} minutes

### Persuasion Architecture
| Slide/Section | STRONG Element | Cialdini Principles | Warren Levers | Frame Control |
|--------------|---------------|--------------------|--------------  |--------------|
| Title | Set the Frame | Authority | Encourage dreams | Prize frame |
| Problem | Tell the Story | Liking | Confirm suspicions | Power frame |
| ... | ... | ... | ... | ... |

---

### Slide 1: {Title}
**On-slide copy:** {text that appears on the slide}
**Speaker notes:** {what to say}
**Frame control:** {technique for this moment}
**Intrigue ping:** {curiosity trigger}

### Slide 2: {Problem}
**On-slide copy:** {text}
**Speaker notes:** {what to say}
**Data point:** {specific proof}
**Emotional beat:** {hot cognition trigger}

### Slides 3-12: ...

---

### Frame Control Playbook
| Situation | Their Frame | Your Counter-Frame |
|-----------|------------|-------------------|
| "We need more data" | Analyst frame | "I'll send the details — but first, does the vision resonate?" |
| "What about competitor X?" | Power frame | "Good question — here's why they can't do what we do" |
| "Let me think about it" | Delay frame | "I understand — I should mention we're closing [date]" |

### Objection Responses
| Objection | Response | Cialdini Principle Used |
|-----------|---------|----------------------|

### Delivery Notes
- **Total slides:** {count}
- **Key frame control moments:** {list}
- **Hot cognition triggers:** {list}
- **Croc-brain survival tips:** {list}
- **Post-pitch follow-up:** {next steps}
```

---

## Condiciones de veto

- Nunca te posicionas como el súplica - el lanzamiento es USTED que ofrece una oportunidad
- Nunca dejes que la cubierta supere 12 diapositivas para los lanzamientos de inversores - los lazos de atención son finitos
- NUNCA presenta el tamaño del mercado sin bottom-up lógica — top-down TAM no tiene sentido
- Nunca saltes la tracción - incluso early-stage las empresas deben mostrar impulso
- Nunca termina sin un específico, time-bound pedir — vaga pide respuestas vagas

---

## Criterios de finalización

- [ ] método STRONG totalmente ejecutado (todos los 6 elementos presentes)
- [ ] Estrategia de control de marcos definida para cada sección
- [ ] Diapositiva ...by-slide copia escrita on-slide notas de texto y oradores
- [ ] Intriga + arco de tensión mantenido en todo
- [ ] Traction/proof datos integrados
La Pregunta es específica, cuantificada y time-bound
- [ ] Libro de juegos de control de marcos para objeciones comunes
Notas de entrega con activadores de cognición caliente
- [ ] Capa Psicológica aplicada - Principios Cialdini mapeados por diapositiva
Blair Warren se accionó a través del arco de lanzamiento
