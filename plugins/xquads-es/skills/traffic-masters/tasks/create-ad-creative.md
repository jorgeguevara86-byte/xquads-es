---
task: createAdCreative()
responsavel: "@ad-midas"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: product
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: platform
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: adCreativePackage
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Conceptos desarrollados con ángulos distintos" 
  - "[ ] Cada concepto incluye gancho, copia, dirección visual y CTA" 
  - "[ ] Marco de prueba definido con pares y métricas" 
---

# Task: Create Ad Creative

** ID de la lista:** TRAFFIC-004
**Version:** 1.0.0
**Command:** `*create-ad-creative`
**Agente:** Ad Midas (Agencia)ad-midas) o Analista Creativo (creative-analyst)
**Purpose:** Desarrollar conceptos creativos ad con ganchos, copia, dirección visual y plan de pruebas.

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
Silencioso Silencio Silencio Silencio Silencio Silencio Silencio Silencio Product/service ser anunciado Silencio
Silencio, plataforma, confidencialidad, efectos, efectos, efectos, efectos, efectos, efectos, efectos, efectos, efectos, efectos,
Silencio audiencia Silencio Silencio Silencio Sugerencia de usuario Silencio Silencio Público de la respuesta
| funnel_stage Silencio enum Silencio Sugerencia de usuario Silencio Silencioso, caliente, caliente
tención formato TENIDO enum TENIDO Usuario prompt TEN No TENEDEN imagen, video, carousel, UGC — defaults to platform best practice TEN
| num_concepts TENEDAD NVI TENIDO ANTERIOR NO TENIDO Defaults to 5 concepts TEN
| brand_guidelines TENEDA TENCIÓN TENIDO NO TENIDO Colores, fuentes, limitaciones de tono TEN

---

## Preconditions

- Plataforma seleccionada con limitaciones de formato entendidas
- Audiencia definida con los desencadenantes emocionales identificados
- El estadio del embudo determina el ángulo de mensajería

---

## Fases de Ejecución

### Fase 1: Investigación Creativa
1. Analizar los patrones creativos ganadores para la plataforma:
   - ¿Qué formato domina (estático, vídeo, UGC)?
   - ¿Qué estilos de gancho funcionan (preguntas, choque, resultado, historia)?
   - Qué estilos visuales atraen (limpio, crudo, text-heavy¿Pesicótico?
2. Estudie los hábitos de consumo de contenido del público en la plataforma
3. Identificar patrones creativos de la competencia (lo que diferenciar de)
4. Mapear el creativo a la etapa del embudo mensajería:
   - Cold: Curiosidad, sensibilización sobre problemas, valor de entretenimiento
   - Proofía, educación, diferenciación, construcción de confianza
   - Caliente: Oferta, urgencia, testimonios, directo CTA

### Fase 2: Desarrollo Conceptual
1. Desarrollar conceptos creativos utilizando ángulos distintos:
   - **Problema-Agitación:** Mostrar el dolor que experimentan
   - **Before/After:** Transformación visual o narrativa
   - Proofía Social: result-based
   - **Educación:** Enseñar algo valioso, CTA es el siguiente paso
   - **Pattern Interrupt:** Unesperado visual o declaración que rompe el desplazamiento
2. Para cada concepto se dispone:
   - Gancho (primer 2-3 segundos para video, encabezado para imagen)
   - Mensaje básico (el único viaje)
   - Dirección visual (lista de imágenes, diseño, color, estilo)
   - Copia (texto primario, titular, descripción por especificaciones de plataforma)
   - CTA (texto de botón y acción)
3. Formatos Vary dentro del lote de concepto
4. Asegurar al menos un concepto de estilo UGC (para plataformas sociales)

### Fase 3: Breves de Producción
1. Escribir production-ready breves para cada concepto:
   - Para video: Lista de disparos, script, duración, dirección musical
   - Para la imagen: Descripción de diseño, texto superpuesto, dirección de imágenes
   - Para Carousel: Tarjeta...by-card desglose con progresión de ganchos
2. Especificar las dimensiones y los requisitos de formato por plataforma
3. Observe cualquier límite de superposición de texto (Resolución de la regla del 20% del libro de Facebook, etc.)
4. Proporcionar ejemplos de referencia o tablas de estado de ánimo donde sea útil

### Fase 4: Marco de Pruebas
1. Defina lo que se está poniendo a prueba por concepto:
   - Prueba de gancho: el mismo cuerpo, diferentes ganchos
   - Prueba de formato: el mismo mensaje, diferentes formatos
   - Prueba angosta: misma audiencia, diferentes enfoques
2. Recomendar pares de pruebas (que 2 conceptos para probar primero)
3. Definir las métricas de éxito por concepto
4. Establecer el presupuesto mínimo y la duración de la importancia estadística

---

## Formato de salida

```markdown
## Ad Creative Package: {Product}

**Platform:** {platform}
**Audience:** {audience}
**Funnel Stage:** {stage}
**Concepts:** {count}

---

### Concept 1: {Name} — {Angle}
**Format:** {format}
**Hook:** {first 2-3 seconds or headline}
**Core Message:** {single takeaway}

**Copy:**
- Primary Text: {body copy}
- Headline: {headline}
- Description: {description}
- CTA: {button text}

**Visual Direction:**
{Shot list, layout, or imagery description}

**Production Notes:**
{Specs, dimensions, duration, special requirements}

---

### Concept 2-N: ...

---

### Testing Plan

| Test | Concept A | Concept B | Variable | Budget | Duration |
|------|-----------|-----------|----------|--------|----------|

### Platform Specs Checklist
| Spec | Requirement | Status |
|------|------------|--------|
```

---

## Condiciones de veto

- NUNCA crear anuncios sin especificar la plataforma - las limitaciones dan forma al creativo
- Nunca use el mismo ángulo para todos los conceptos - la variedad es el punto de prueba
- Nunca escriba guiones de vídeo sin un gancho en los primeros 3 segundos
- Nunca ignores platform-specific requisitos de formato
- NUNCA saltar el plan de pruebas - creativo sin pruebas es adivinar

---

## Criterios de finalización

- [ ] Patrones creativos de plataforma investigados
- [ ] Conceptos desarrollados con ángulos distintos
Cada concepto incluye gancho, copia, dirección visual y CTA
- [ ] Breves de producción escritas para todos los conceptos
- [ ] Marco de prueba definido con pares y métricas
- [ ] Especificaciones de plataforma verificadas para todos los formatos
