---
task: setupTracking()
responsavel: "@pixel-specialist"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: platforms
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: website
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: trackingSetup
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Arquitectura de seguimiento mapeado con todas las plataformas" 
  - "[ ] Jerarquía de eventos definida con parámetros" 
  - "[ ] Lista de verificación QA creada y probada" 
---

# Task: Setup Tracking

** ID de la lista:** TRAFFIC-005
**Version:** 1.0.0
**Command:** `*setup-tracking`
**Agente:** Especialista de Pixel (pixel-specialist)
**Purpose:** Diseñar y documentar la configuración de seguimiento y atribución para publicidad pagada.

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
Silencio plataformas Silenciosos lista Silenciosos Sugerencias de usuario Silencio Silencio Plataformas de anuncios en uso (fazbook, google, tiktok, etc.) ←
TENIDO sitio web TENEDA TENEDA DE Usuarios TENIDO Sí TENIDO Sitio web URL y pila de tecnología (WordPress, Shopify, custom, etc.) TEN
| conversion_events Silencioso lista Silenciosos del usuario incitar Sí Silencio Eventos clave para rastrear (purchase, lead, signup, etc.) Silencio
| funnel_pages Silencio lista Silencio Usuario prompt Silencio No Silencio Páginas clave en el embudo (enlace, checkout, gracias) Silencio
| current_tracking TENED TENED SON TENIDO ANTERIOR NO TENIDOS Existing tracking setup description TEN
Silencio ecommerce ← boolean Silencio Usuario prompt Silencio No ← Ya sea que el sitio tenga e-commerce operaciones FORMULADAS

---

## Preconditions

- Acceso a sitios web y editable (o acceso a los administradores de etiquetas disponibles)
- Cuentas de plataforma de anuncios creadas con pixel/tag IDs disponibles
- Eventos de conversión definidos (lo que cuenta como conversión)

---

## Fases de Ejecución

### Fase 1: Rastreando la Arquitectura
1. Mape la pila de seguimiento completa:
   - Administrador de etiquetas: Google Tag Manager, Meta Pixel Helper, platform-native
   - Píxeles: Meta Pixel, Google Ads Tag, TikTok Pixel, LinkedIn Insight Tag
   - Análisis: Google Analytics 4, análisis de plataformas
   - Servidor-side: Conversiones API (CAPI), conversiones offline
2. Definir la jerarquía de eventos de conversión:
   - Primaria: El principal resultado empresarial (purchase, formulario de presentación)
   - Secundaria: Eventos de mecanal (adición al carrito, inicia el checkout, vista de página)
   - Micro: Eventos de compromiso (profundidad de la cámara, tiempo en la página, vista de vídeo)
3. Mapa de eventos a estadios de embudo:
   - Vista de la página → Visita de la página
   - Líder → Presentación de formularios o opt-in
   - Iniciar checkout → Llegada página de salida
   - Compra → Transacción completa
4. Documento estrategia del parámetro UTM para la atribución

## Fase 2: Configuración de plataformas
1. Para cada plataforma, documente los requisitos de configuración:
   - **Meta (Facebook/Instagram):**
     - Instalación de base de pixel
     - API de conversiones (server-side) configuración
     - Optimización de puntuación de calidad de Evento
     - Conversiones personalizadas y eventos estándar
     - Verificación de dominios y medición de eventos agregados
   - ¿Qué?
     - Google Ads tag installation
     - Mejora de la configuración de conversiones
     - Conversión de enlace
     - Integración GA4 para compartir audiencias
   - **TikTok:**
     - Instalación de TikTok Pixel
     - Configuración de la API de Eventos
     - Haga clic en el manejo del parámetro ID
   - **LinkedIn:**
     - Instalación de etiqueta de visión
     - Configuración de seguimiento de conversiones
2. Proporción step-by-step Instrucciones de configuración para cada plataforma
3. Definir el procedimiento de prueba para verificar cada evento dispara correctamente

### Phase 3: Attribution Strategy
1. Definir el modelo de atribución para la presentación de informes:
   - Último clic: Sencillo pero sesgado hacia bottom-of-funnel
   - Data-driven: Recomendado cuando el volumen lo soporta
   - Multi-touch: Para embudos complejos con muchos puntos de contacto
2. Establecer la ventana de atribución por plataforma:
   - Meta: clic de 7 días, vista de 1 día (por defecto)
   - Google: 30 días de clic (por defecto)
   - TikTok: clic de 7 días, vista de 1 día
3. Documentar la expectativa de discrepancia entre plataformas
4. Crear un source-of-truth marco de presentación de informes:
   - ¿Qué plataforma para creer para qué métricas
   - Cómo reconciliarse cross-platform atribución

### Fase 4: QA y Validación
1. Crear una lista de verificación QA de seguimiento:
   - Cada pixel dispara en las páginas correctas
   - Acontecimientos con parámetros correctos (valor, moneda, identificación de contenido)
   - Eventos de servidor coinciden con eventos del navegador (deduplicación)
   - Los parámetros UTM pasan a través del embudo correctamente
   - Gracias eventos de página fuego una vez (sin conversiones duplicadas)
2. Definir el procedimiento de prueba de validación
3. Documentos de limitaciones conocidas y casos de borde
4. Establecer alertas de vigilancia para detectar fallos

---

## Formato de salida

```markdown
## Tracking Setup: {Website/Business}

**Platforms:** {list}
**Tag Manager:** {GTM / platform-native / custom}
**Server-Side:** {yes/no — CAPI, Enhanced Conversions}

---

### Event Map

| Event | Trigger | Platforms | Parameters | Page |
|-------|---------|-----------|------------|------|
| PageView | All pages | All | URL, referrer | * |
| Lead | Form submit | Meta, Google | value, content_name | /thank-you |
| Purchase | Transaction | Meta, Google | value, currency, content_ids | /order-confirmation |

### Platform Setup Guides

#### Meta Pixel + CAPI
{Step-by-step instructions}

#### Google Ads + Enhanced Conversions
{Step-by-step instructions}

#### {Additional platforms}

### UTM Strategy

| Parameter | Convention | Example |
|-----------|-----------|---------|
| utm_source | {platform} | facebook |
| utm_medium | {type} | cpc |
| utm_campaign | {naming convention} | cold_lookalike_offer1 |

### Attribution Framework
**Primary model:** {model}
**Windows:** {per platform}
**Source of truth:** {which system for which metric}

### QA Checklist
- [ ] {item per platform and event}

### Monitoring
| Alert | Condition | Action |
|-------|-----------|--------|
```

---

## Condiciones de veto

- NUNCA lanza anuncios pagados sin seguimiento verificado - el gasto sin medida es dinero quema
- Nunca confíe en la atribución de una sola plataforma en aislamiento - cross-reference
- Nunca salta server-side seguimiento (CAPI) para Meta — browser-only seguimiento pierde 30-40% de eventos
- NUNCA eventos de compra de incendios sin parámetros de valor - el cálculo ROAS depende de él
- Nunca asuma trabajos de seguimiento después de la configuración - siempre ejecutar una prueba de QA con conversiones reales

---

## Criterios de finalización

- [ ] Arquitectura de seguimiento mapeado con todas las plataformas
- [ ] jerarquía de eventos definida con parámetros
[ ] Guías de configuración específicas de la plataforma escritas
- [ ] Estrategia UTM documentada
- [ ] modelo de atribución seleccionado y ventana
- [ ] QA lista de verificación creada y probada
- [ ] Alertas de vigilancia definidas
