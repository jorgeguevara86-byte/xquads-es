---
task: writeVslScript()
responsavel: "@stefan-georgi"
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
  - campo: vsl_script
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Marco de RMBC ejecutado plenamente (todas las 4 secciones)" 
  - "[ ] Ganar el gancho convincente en los primeros 60 segundos" 
  - "[ ] Cuestiones de dirección visual y notas de producción incluidas" 
  - "[ ] Capa Psicológica aplicada (Cialdini/Warren principios etiquetados)" 
---

# Task: Write VSL Script

** ID de la lista: * COPY-M-003
**Version:** 2.0.0
**Command:** `*write-vsl-script`
**Agente: ** Stefan Georgi (*stefan-georgi)
**Purpose:** Escribe un script de Cartas de Ventas de Video usando el método RMBC con psicología de persuasión estratada.

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
Silencioso Silencio Silencio Silencio Silencio Silencio Silencio Silencio Product/service con transformación que entrega Silencio
Silencio audiencia Silencios Silenciosidad de usuario incitar a tu usuario Sí Silencio audiencia con estado emocional y deseos Silencio
Silencio oferta Silencioso objeto Silencioso de usuario inducido Silencio Sí Silencio Precio, garantía, bonos, urgencia 
| duration_target TENCIÓN TENIDO ANTERIOR NO TENIDO corto (10-15min), medio (20-30min), largo (45-60min) — predeterminados a la TER media
| unique_mechanism Silencio Silencio Silencio Silencio No Silencio Lo que hace que esta solución sea diferente Silencio
| proof_elements | lista | Mensaje de usuario | No | Testimonios, resultados, credenciales |
Silencio plataforma Silencioso cadena Silencioso de usuario insinuar Silencio No Silencio Dónde se ejecutará el VSL (página de aterrizaje, YouTube, webinar) Silencio

---

## Preconditions

- Transformación de productos claramente definida (before/after Estado)
- Estructura de oferta completa con precio y garantía
- Se identificaron los desencadenantes emocionales de la audiencia de blanco

---

# Champion Reference

Estudiar estos real-world campeón VSLs antes de escribir:

1. ** "El Fin de América"** (Stansberry Research, Mike Palmer) — 60 minutos fear-driven VSL, proof-heavy, generados $100M+
2. **"Patriot Health Alliance"** (Stefan Georgi) — La ejecución de libros de texto RMBC, suplemento VSL con un mecanismo fuerte revelan
3. **"Flat Belly Fix"** (Todd Lamb / Stefan Georgi) — Salud de corta duración VSL, RMBC apretado, ganador de tráfico masivo en frío
4. ** "Video Secrets"** (Jon Benson) — Pioneer of the text-on-screen Formato VSL, conversacional micro-commitment estilo
5. **"El Club de Oxford Pitch"** (Agora Financial) — VSL financiero de larga duración, autoridad + apilación de pruebas sociales

---

## Fases de Ejecución

## Fase 1: Configuración Marco RMBC
1. **R -- Relate:** Define la historia de apertura relatable o escenario
   - Identifica un momento en el que la perspectiva ha vivido
   - Elige first-person o second-person ángulo narrativo
   - Mapear el gancho emocional (frustración, vergüenza, miedo, desesperación)
2. **M - Mecanismo:** Definir el mecanismo único
   - Nombrar el mecanismo (de ser posible un nombre propietario)
   - Explique por qué todo lo demás falló (invalidar competidores)
   - Construir credibilidad para el mecanismo con prueba o lógica
3. **B -- Beneficios:** Ataque los beneficios en orden emocional
   - Lidera con la transformación #1
   - Beneficios secundarios de capa que pintan la "nueva vida"
   - Uso future-pacing para hacer beneficios viscerales
4. **C -- Cerrar:** Estructurar la secuencia cercana
   - Estrategia de anclaje de precios
   - Posición de garantía
   - Montaje de bonos con llamadas de valor individuales
   - Urgency/scarcity element
   - CTA final con el siguiente paso exacto

## Fase 2: Capa Psicológica
1. Mapa Cialdini principios en la estructura VSL:
   - **Sección de la lista:** El amor (lucha compartida), la unidad (identidad compartida)
   ** Sección de Mecanismo:** Autoridad (ciencia, credenciales), Compromiso (pequeños acuerdos)
   - **Sección de beneficios:** Proofo Social (testimonios), Reciprocidad (información gratuita)
   **Sección de cierre:** Escasa (limitada) time/spots), Consistencia (ya acordaron)
2. Aplicar 5 palancas de Blair Warren:
   - Relate = Justificar los fracasos + Teme a Allay
   - Mecanismo = Confirmación de sospechas + Tire rocas a enemigos
   - Beneficios = Anime sueños
3. Asegurar que cada sección de RMBC active al menos 2 principios psicológicos
4. Documentar la arquitectura de persuasión

### Phase 3: Script writing
1. Escriba el gancho (primer 60 segundos) - debe detener el pergamino y ganar atención
2. Escribe la sección "relatar" con arc de historia (conversación - confianza descubrimiento - cambio de confianza)
3. La transición al mecanismo revela con la interrupción del patrón
4. Prestaciones actuales utilizando "imagina..." y "qué si..." lenguaje
5. Insertar bloques de pruebas entre secciones principales (testimonios, estadísticas, demos)
6. Escribe el cierre con el precio revelar, apilar, garantizar y urgencia
7. Agregue los golpes y la copia del formulario de pedido si es aplicable
8. Escribe el "caminar" cerca — qué sucede si no hacen nada

## Fase 4: Notas de producción
1. Add.1 visual/slide instrucciones en los corchetes
2. Marca puntos de énfasis para la modulación de voz
3. Identificar dónde deben aparecer las imágenes de B-roll o demostración
4. Tiempo estimado de ejecución a 150 words/minute hablando de ritmo
5. Secciones de bandera que pueden ser cortadas para versiones más cortas

---

## Formato de salida

```markdown
## VSL Script: {Product Name}

**Method:** RMBC (Relate-Mechanism-Benefits-Close)
**Target Duration:** {X} minutes (~{Y} words)
**Audience:** {audience}
**Emotional Hook:** {primary emotion}
**Unique Mechanism:** {mechanism name}

### Persuasion Architecture
| RMBC Section | Cialdini Principles | Warren Levers |
|--------------|--------------------|--------------  |
| Relate | {principles} | {levers} |
| Mechanism | {principles} | {levers} |
| Benefits | {principles} | {levers} |
| Close | {principles} | {levers} |

---

### HOOK (0:00 - 1:00)
{Opening hook script}
[VISUAL: {direction}]

### RELATE (1:00 - {X}:00)
{Relatable story section}
[VISUAL: {direction}]

### MECHANISM ({X}:00 - {Y}:00)
{Mechanism reveal and explanation}
[VISUAL: {direction}]

### BENEFITS ({Y}:00 - {Z}:00)
{Benefits stack with future-pacing}
[VISUAL: {direction}]

### PROOF BLOCKS
{Testimonial/proof insertions with timestamps}

### CLOSE ({Z}:00 - END)
{Price reveal, stack, guarantee, urgency, CTA}
[VISUAL: {direction}]

---

### Production Notes
- **Estimated runtime:** {X} minutes
- **Word count:** {Y}
- **Key visual moments:** {list}
- **Suggested A/B tests:** {hook variant, close variant}
```

---

## Condiciones de veto

- NUNCA salta la sección Relate - sin conexión emocional el VSL falla
- Nunca revelar el producto antes de establecer el mecanismo
- NUNCA precio actual sin anclaje a un valor superior primero
- Nunca escriba un VSL sin visual/slide dirección cues
- Nunca supere la duración del objetivo en más del 20%

---

## Criterios de finalización

- [ ] Marco de RMBC ejecutado plenamente (todas las 4 secciones presentes)
- El gancho es convincente en los primeros 60 segundos.
- Mecanismo único llamado y explicado
- [ ] Manifestación de bloques insertados entre secciones principales
- [ ] Close incluye el anclaje de precios, garantía, pila de bonificación, urgencia
- [ ] Cuestiones de dirección visual incluidas en todas partes
Estimación de tiempo de ejecución calculada
- [ ] Notas de producción proporcionadas
- [ ] Layer Psicológica aplicada - Principios Cialdini mapeados por sección RMBC
Blair Warren se identificó y activó
