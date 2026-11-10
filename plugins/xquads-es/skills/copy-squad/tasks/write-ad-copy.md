---
task: writeAdCopy()
responsavel: "@dan-kennedy"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: product
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: platform
    tipo: enum
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: ad_copy_package
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Limitaciones de la plataforma identificadas y respetadas" 
  - "[ ] 5 variaciones de anuncios escritas con ángulos distintos" 
  - "[ ] Plan de prueba con pares priorizados proporcionados" 
---

# Task: Write Ad Copy

** ID de la lista:** COPY-005
**Version:** 1.0.0
**Command:** `*write-ad-copy`
Dan Kennedy (Dan Kennedy)dan-kennedy)
**Purpose:** Escriba copia de anuncio de respuesta directa para cualquier plataforma de medios pagados.

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
Silencioso Silencio Silencio Silencio Silencio Silencio Silencio Silencio Product/service con beneficio clave Silencio
Silencio audiencia Silencio Silencio Silencio Sugerencia de usuario Silencio Silencio Público objetivo con comportamiento de plataforma TENIDO
Silencio soberbia plataforma Silencio enum Silencio Sugerencia de usuario Silencio Silencio facebook, instagram, google-search, google-display, youtube, tiktok, linkedin Silencio
TEN objective TENED enum TENIDO Usuario prompt TENED Sí TENEDEN conciencia, tráfico, leads, ventas, retargeting TEN
Silencioso oferta Silencioso cadena Silencio Usuario prompt Silencio No Silencio Lo que el anuncio está conduciendo a (imán de carga, venta, webinar, etc.) Silencio
| budget_context TENEDA TENCIÓN ANTERIOR NO TENIDOS Nivel de Spend — afecta el volumen de variaciones TEN
Silenciosos competidores Silenciosos lista de usuarios Silencio No Silencio Conocido competidores para diferenciación Silencio

---

## Preconditions

- Plataforma seleccionada con una comprensión clara de las limitaciones de formato
- Objetivo de la campaña definido
- La página de aterrizaje o destino existe (o se está construyendo en paralelo)

---

## Fases de Ejecución

## Fase 1: Estrategia de Plataforma-Específica
1. Definir las limitaciones de formato por plataforma:
   - Facebook/Instagram: Texto primario (125 chars above fold), titular (40 chars), descripción (30 chars), image/video
   - Google Search: 3 titulares (30 chars cada uno), 2 descripciones (90 chars cada uno)
   - YouTube: Ganar en 5 segundos (esquipable), 15-30 para non-skip
   - TikTok: Tono nativo, gancho en 2 segundos, video script 15-60s
   - LinkedIn: Tono profesional, intro de 150 caracteres, titular
2. Identificar el estilo de comunicación nativo de la plataforma
3. Mapear el escenario del embudo para el enfoque de mensajería:
   - Tráfico frío: plomo con problema o curiosidad
   - Tráfico de calor: plomo con prueba o mecanismo
   - Caliente traffic/retarget: Liderazgo con oferta y urgencia

## Fase 2: Creación de Copias Ad
1. Escribe 5 variaciones de anuncios por formato utilizando ángulos distintos:
   - Ángulo de agitación de problemas
   - Ángulo de beneficios
   - Ángulo de prueba social
   - Curiosity/news angle
   - Ángulo de oferta directa
2. Para cada variación se proporcionan:
   - Texto primario / copia corporal
   - Headline
   - Description / sub-headline
   - Recomendación del texto del botón CTA
3. Escribe una copia que coincida con el tono nativo de la plataforma
4. Asegurar que cada anuncio pueda permanecer solo (sin dependencia de creativo)

### Fase 3: Marco de Pruebas
1. Organizar anuncios en un plan de pruebas estructurado
2. Recomendar qué 2 anuncios para probar primero y por qué
3. Definir las métricas de éxito por plataforma y objetivo
4. Sugerir notas de dirección creativa para cada anuncio (image/video orientación)
5. Proporcionar variantes de anuncios de retargeting para non-converters

---

## Formato de salida

```markdown
## Ad Copy Package: {Product}

**Platform:** {platform}
**Objective:** {objective}
**Audience:** {audience}
**Funnel Stage:** {cold / warm / hot}

---

### Ad Variation 1: {Angle Name}
**Primary Text:** {body copy}
**Headline:** {headline}
**Description:** {description}
**CTA:** {button text}
**Creative Direction:** {image/video guidance}

---

### Ad Variation 2-5: ...

---

### Testing Plan

| Priority | Ad # | Angle | Test Against | Success Metric |
|----------|------|-------|-------------|----------------|

### Retargeting Variants
{2-3 retargeting ad variations for non-converters}

### Platform-Specific Notes
{Character limits respected, format compliance, policy considerations}
```

---

## Condiciones de veto

- Nunca supere los límites de caracteres de plataforma
- NUNCA escribe anuncios sin especificar la plataforma - el formato de limitaciones materia
- Nunca utilice el mismo ángulo para las 5 variaciones
- NUNCA ignorar las políticas de publicidad de plataformas (sin reclamaciones exageradas, sin categorías prohibidas)
- Nunca escriba un anuncio sin un CTA claro

---

## Criterios de finalización

- [ ] Limitaciones de la plataforma identificadas y respetadas
- 5 variaciones de anuncios escritas con ángulos distintos
- Cada anuncio incluye todos los elementos de formato requeridos
- Plan de prueba con pares priorizados
- [ ] Variantes de retargeting incluidas
- [ ] Notas de dirección creativa proporcionadas
Verificación de la política de la plataforma
