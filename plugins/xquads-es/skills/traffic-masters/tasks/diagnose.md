---
task: diagnoseTrafficChallenge()
responsavel: "@traffic-chief"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: request
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: platform
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: false

Saida:
  - campo: diagnosis
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Solicitud de persiana y palabras clave extraídas" 
  - "[ ] Catálogo de enrutamiento consultado con resultados puntuados" 
  - "[ ] Respuesta rápida proporcionada con referencia métrica" 
---

# Task: Diagnose Traffic Challenge

** ID de la lista de documentos** TRAFFIC-CHIEF-001
**Version:** 1.0.0
**Command:** `*diagnose`
**Orquestador:** Jefe de Tráfico (traffic-chief)
**Purpose:** Triage pay traffic challenges, provide quick answer, route to platform expert or functional specialist.

---

## Overview

```
Solicitud de usuario → Analizar palabras clave → Coincidir con el catálogo de enrutamiento → Answer/Route → Salida
     │              │                    │                     │
     ▼              ▼                    ▼                     ▼
  Plataforma de extracción de entrada cruda Dominios de puntuación Respuesta rápida +
              + función + contra 17 dominios ruta especializada
              contexto métrico + enrutamiento de plataforma (platform-aware)
```

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
Silencioso petición Silencio cadena Silencio Sugerencia de usuario Silencio Silencio Novato traffic/ads-related descripción voca
Silencio contexto Silencioso objeto Silencioso sesión estado Silencio No Silencio Información general, métricas actuales, presupuesto Silencio
Silencioso plataforma Silencio Silencio Silencioso de usuario inaplicable Silencio No Silencio Facebook, Google, YouTube, TikTok, LinkedIn, cross-platform |

---

## Preconditions

- Los Masters de Tráfico están activos con el Jefe de Tráfico como agente de entrada
- Catálogo de enrutamiento cargado desde data/routing-catalog.yaml
- Los 15 agentes especializados registrados config.yaml
- Mapa de la plataforma disponible para platform-specific triage

---

## Fases de Ejecución

### Fase 1: Analizar solicitud

1. Parse el desafío de tráfico del usuario
2. Extraiga las palabras clave principales y la intención
3. Identificar la plataforma (Facebook/Meta, Google, YouTube, TikTok, LinkedIn, o cross-platform)
4. Identificar la función (creativa, escalada, seguimiento, auditoría, presupuestación, compra de medios)
5. Nota de métricas clave mencionadas (ROAS, CPA, CTR, CPM, nivel de gasto)

### Fase 2: Coincidencia contra el catálogo de enrutamiento

| Dominio | Palabras clave | Ruta a |
|--------|----------|----------|
| Facebook/Meta Estrategia viv Facebook anuncios, Meta ads, Instagram anuncios Silencio molly-pittman / depesh-mandalia |
← Facebook escalar Silencioso escala Facebook, aumentar el gasto, método BPM  depesh-mandalia / ralph-burns |
Silencio YouTube Ads Silencio YouTube anuncios, anuncios de vídeo, pre-roll, TrueView TENIDO tom-breeze / ad-midas |
Silencio Google Ads Silencio Google Ads, PPC, Performance Max, search ads Silencio kasim-aslam / performance-analyst |
← Facebook de alto contenido TENIDO ROI, Give-Give-Ask, anuncios de relación TENIDO nicholas-kusmich / molly-pittman |
| Brazil/LATAM Tráfico TEN Brasil, LATAM, método Sobral, anuncios españoles TEN pedro-sobral / depesh-mandalia |
← Ad Creative ← creativo, ad creativo, UGC, video creativo  ad-midas / creative-analyst |
← Medios de comunicación Comprando Silenciosos medios comprando, organizador de campañas, licitación, colocación media-buyer / ralph-burns |
TENCIÓN TENIDO Análisis de rendimiento TENIDO analytics, reportajes, métricas, ROAS, datos TEN performance-analyst / ads-analyst |
Silencio para el examen creativo A/B prueba, prueba de división, fatiga creativa, iteración TEN creative-analyst / ad-midas |
Silencio Campaña Escalando campañas de escala Silencioso, aumentar el presupuesto, parecer  scale-optimizer / depesh-mandalia |
| Tracking/Attribution TENCIÓN, Píxel, CAPI, Atribución, iOS 14 TENIDO pixel-specialist / performance-analyst |
TENER Auditoría de la Cuenta Ad TENIS, auditoría de cuentas, salud de cuentas, desperdicios, optimización TENCIÓN ads-analyst / performance-analyst |
Silencioso presupuesto tención presupuesto, gasto de anuncio, control de costos, asignación TENIDO fiscal / scale-optimizer |
TEN Full-Funnel Strategy TENIENDO el embudo completo, TOFU, MOFU, BOFU, el viaje al cliente TEN ralph-burns / molly-pittman |
TENIDO Tránsito Perpetual TENIDO tráfico perpetuo, siempreverde, always-on, sostenible , ralph-burns / molly-pittman |

**Platform shortcut routing:**
- Facebook/Meta mencionado -- molly-pittman, depesh-mandalia, ralph-burns (cerradura por función)
- YouTube mencionado - tom-breeze
- Google mencionó - Cómodo kasim-aslam
- TikTok mencionó... media-buyer, ad-midas
- LinkedIn mencionó... media-buyer, nicholas-kusmich
- Cross-platform / poco claro - traffic-chief respuestas, sugerir expertos en plataforma

**Reglas de puntuación:**
- Contar coincidencias de palabras clave por dominio
- 2+ coincidencias por encima de otras --> ruta al especialista principal de ese dominio
- Plataforma + función partido -- ruta de confianza a experto en plataforma primero
- Tie o cross-platform -- Jefe de Tráfico responde directamente
- No hay coincidencia clara -- confiar preguntar sobre plataforma, presupuesto y métricas actuales

### Fase 3a: Respuesta Transversal

Si la solicitud es general o cross-platform:
- Proveed platform-agnostic asesoramiento sobre tráfico
- Referencia de métricas clave para evaluar (ROAS, CPA, CTR)
- Sugerir platform-specific expertos para un análisis más profundo

### Fase 3b: Ruta específica del dominio

Si la solicitud se asigna claramente a un dominio:
1. ** Respuesta rápida primero** (3-5 líneas mínimo + punto de referencia métrico concreto o táctica)
2. **Real:** Nombre del especialista, explique su metodología, proporcione el comando de activación
   - Ejemplo: "Para escalar el gasto en Facebook, el método BPM de Depesh Mandalia se prueba a escala. Activar con `@traffic-masters:depesh-mandalia`"

### Fase 4: Evaluación de confianza

| Confianza | Criterios | Acción |
|------------|----------|--------|
TENGH HIGH TEN 3+ palabras claves + plataforma clara TEN Ruta con confianza para el especialista primario TEN
Silencio Silencio Silencio 1-2 partidos o plataforma incierto Silencio Respuesta + sugerir 2 especialistas Silencio
TEN LOW TEN No hay partido claro o muy vago TEN Responder directamente, preguntar acerca de la plataforma y el presupuesto TEN

---

## Formato de salida

```markdown
## Diagnosis
**Category:** {domain | cross-platform}
**Confidence:** {HIGH | MEDIUM | LOW}
**Platform:** {Facebook | Google | YouTube | TikTok | LinkedIn | Cross-platform}
**Specialist:** {Name} ({agent-id}) | Direct Answer

### Quick Answer
{3-10 line answer with concrete traffic advice}

### Recommended Next Step
{Route instruction with activation command, or follow-up question}
```

---

## Condiciones de veto

- NUNCA realice rutas sin proporcionar primero una respuesta rápida
- NUNCA ruta cuando la confianza es LOW - responder directamente y preguntar sobre plataforma + métricas
- NUNCA cargue un archivo de agente especializado durante el diagnóstico
- Nunca asuma una plataforma cuando no se menciona explícitamente
- Nunca asesorar sin referenciar métricas específicas o puntos de referencia

---

## Criterios de finalización

- [ ] Solicitud analizada y palabras clave extraídas
[ ] Plataforma identificada (o aclaración solicitada)
- [ ] Catálogo de enrutamiento consultado con resultados puntuados
Respuesta rápida proporcionada con referencia métrica
- [ ] Ruta especializada proporcionada (si domain-specific)
- [ ] Nivel de confianza indicado
