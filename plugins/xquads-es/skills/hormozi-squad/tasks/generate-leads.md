---
task: generateLeads()
responsavel: "@hormozi-leads"
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
  - campo: leadGenerationSystem
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Las 4 fuentes principales auditadas y anotadas" 
  - "[ ] Imán de plomo diseñado con puente claro a la oferta central" 
  - "[ ] 30-Day plan de lanzamiento creado" 
---

# Task: Generar plomos

** ID de usuario: **HORMOZI-002
**Version:** 1.0.0
**Command:** `*generate-leads`
**Agente:**hormozi-leads)
**Purpose:** Diseñar un sistema de generación de plomo usando el marco de $100M Leads.

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
Silencios empresariales Silenciosidad de usuario inducido por Silencio Si Silencio Tipo de negocio, product/service, y la etapa actual TENIDO
Silencios en la audiencia Silencio Silencio inesperar a nuestros clientes Silenciosos en la vida
Silencio presupuesto Silencio cadena Silencio Usuario prompt Silencio No Silencio Mensaje de marketing mensual range ←
| current_channels Silencio Silencio Silencio Usuario prompt Silencio No Silencio Fuentes de plomo existentes Silencio
| lead_goal Silencio número Silencio Usuario prompt Silencio No Silencio Target lidera por mes Silencio
| business_model TENEDA TENIDO TENIDO ANTERIOR NO TEN B2B, B2C, local, e-commerce, SaaS, servicio Silencioso

---

## Preconditions

- Tipo de negocio y oferta definida
- Público objetivo identificado con suficiente especificidad para encontrarlos

---

## Fases de Ejecución

## Fase 1: Auditoría de fuentes principales
1. Evaluar las 4 fuentes principales (Marco Hormozi):
   - Alcance de alarma: Contactos existentes, clientes anteriores, referencias
   - Cold Outreach: Divulgación directa a extraños (email, DM, teléfono)
   - Contenido (libre): Contenido orgánico que atrae a los clientes a lo largo del tiempo
   - Anuncios pagados: Los medios de pago que compran los cables inmediatamente
2. Partitura de cada fuente sobre la eficacia actual (1-10)
3. Identificar la mayor brecha — ¿qué fuente está subutilizada?
4. Mapa de cada fuente al modelo de negocio y presupuesto

## Fase 2: Diseño de Magneto de plomo
1. Crear un imán de plomo utilizando los criterios de Hormozi:
   - Solves un problema específico y estrecho completamente
   - Proporciona valor en menos de 5 minutos de consumo
   - Naturalmente conduce a la oferta central como el siguiente paso
   - Tiene un nombre convincente y específico
2. Elija el tipo de imán de plomo:
   - Prueba gratuita / muestra
   - Lista de verificación / hoja de trampa
   - Herramienta gratuita / calculadora
   - Formación gratuita / taller
   - Evaluación / examen
   - Plantilla / archivo de hoja de página
3. Nombre el imán de plomo con un result-oriented Título
4. Definir el mecanismo de ejecución

## Fase 3: Estrategia del Canal
1. Para cada canal activo o recomendado, definir:
   - Volumen de destino (de pago por semana)
   - Costo por estimación de gastos
   - Message/content type
   - Frecuencia y cadencia
2. Plan de divulgación de alarma:
   - Estrategia de creación de listas (que contactar primero)
   - Planillas de mensajes (Marco de AAC: Reconocimiento, Complimento, Pregunta)
   - Secuencia de seguimiento
3. Plan de divulgación fría:
   - Método de contratación de listas
   - Oferta de framing para contactos fríos
   - Enfoque de personalización
   - Objetivos de volumen y expectativas de conversión
4. Plan de contenido:
   - Selección de plataformas (donde ya está el público)
   - Los pilares de contenido atados a la oferta central
   - Posting cadence and content types
   - Call...to-action estrategia
5. Plan de anuncios pagados:
   - Recomendación de la Plataforma
   - Asignación presupuestaria
   - Dirección creativa
   - Mecanismo de captura de plomo

## Fase 4: Asamblea del sistema
1. Mapa el flujo de plomo completo: Fuente → Imán de plomo → Nurture → Oferta
2. Definir el follow-up sistema para cada fuente
3. Establecer KPI para cada canal
4. Crear un plan de lanzamiento de 30 días con hitos semanales
5. Defina los desencadenantes de escalado (cuando aumentar spend/effort)

---

## Formato de salida

```markdown
## Lead Generation System: {Business Name}

**Business Model:** {model}
**Lead Goal:** {X}/month
**Budget:** ${range}/month
**Primary Channel:** {recommended}

---

### Lead Source Scorecard

| Source | Current Score | Opportunity | Priority |
|--------|-------------|-------------|----------|
| Warm Outreach | X/10 | {gap} | {1-4} |
| Cold Outreach | X/10 | {gap} | {1-4} |
| Content (Free) | X/10 | {gap} | {1-4} |
| Paid Ads | X/10 | {gap} | {1-4} |

### Lead Magnet
**Name:** {name}
**Type:** {type}
**Problem Solved:** {specific problem}
**Delivery:** {method}
**Bridge to Offer:** {how it leads to the paid product}

### Channel Plans
{Detailed plan per channel}

### Lead Flow Map
{Source} → {Lead Magnet} → {Nurture} → {Offer}

### 30-Day Launch Plan

| Week | Actions | Target Leads | KPI |
|------|---------|-------------|-----|

### Scaling Triggers
| Metric | Threshold | Action |
|--------|-----------|--------|
```

---

## Condiciones de veto

- Nunca recomiende anuncios pagados como el único canal para un negocio sin presupuesto
- Nunca saltes el imán principal - direct-to-offer sólo para most-aware audiencias
- Nunca recomiendo canales donde el público no existe
- Nunca fije objetivos de liderazgo sin definir coste por expectativas de plomo
- Nunca construir un sistema sin un follow-up mecanismo

---

## Criterios de finalización

- [ ] Las 4 fuentes principales auditadas y anotadas
Imán de plomo diseñado con puente claro a la oferta central
- [ ] Planes de canales definidos con objetivos de volumen
- [ ] Flujo de plomo mapeado end-to-end
- [ ] 30 días de lanzamiento plan creado
- [ ] Dispositivos de escalado definidos
- [ ] KPIs fijados para cada canal
