---
task: diagnoseBusinessChallenge()
responsavel: "@hormozi-chief"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: request
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: revenue_stage
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
  - "[ ] Respuesta rápida proporcionada con referencia marco Hormozi" 
---

# Task: Diagnosticar el desafío de negocios

** ID de usuario:** HORMOZI-CHIEF-001
**Version:** 1.0.0
**Command:** `*diagnose`
**Orquesta:* Jefe Hormozi (Hormozi)hormozi-chief)
**Purpose:** Triage business challenges, provide quick answer using Hormozi frameworks, route to specialist.

---

## Overview

```
Solicitud de usuario → Analizar palabras clave → Coincidir con el catálogo de enrutamiento → Answer/Route → Salida
     │              │                    │                     │
     ▼              ▼                    ▼                     ▼
  Entrada cruda Extraer dominios Puntuación Respuesta rápida +
              tipo de desafío contra 15 dominios ruta especializada
              + etapa + métrica (objetivo de Ecuación de Valores)
```

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
Silencioso petición Silencio cadena Silencio Sugerencia de usuario Silencio Silencio Novato de negocios desafío descripción Silencio
Silencio contexto Silencioso objeto Silencioso sesión estado Silencio No Silencio etapa de negocios, ingresos, industria, actualidad de métricas Silencio
| revenue_stage TENCIÓN TENIDO ANTERIOR NO TENIDO ANTERIOR PRE-revenue, ANTE 1M, $1-3M, $3-10M, $10M+ ANTE

---

## Preconditions

- Hormozi Squad está activo con el Jefe Hormozi como agente de entrada
- Catálogo de enrutamiento cargado desde data/routing-catalog.yaml
- Los 15 agentes especializados registrados config.yaml
- contexto de fórmulas básicas: valor = (Dream Resultado x probabilidad percibida) / (Delay temporal x esfuerzo &quot; Sacrificio)

---

## Fases de Ejecución

### Fase 1: Analizar solicitud

1. Parse el desafío de negocio del usuario
2. Extraiga las palabras clave principales y la intención
3. Identificar la función de negocio (ofertas, leads, precios, ventas, escalada, retención, etc.)
4. Identificar la etapa de negocio si se menciona (pre-revenue, startup, growth, scale)
5. Tenga en cuenta qué parte de la Ecuación de Valores es insuficiente

### Fase 2: Coincidencia contra el catálogo de enrutamiento

| Dominio | Palabras clave | Ruta a |
|--------|----------|----------|
← Oferta Creacion vivificante oferta, gran slam, valor apilado, bonos, garantia  hormozi-offers / hormozi-pricing |
← Generación de plomo Silencio guía, imanes, adquisiciones, extensión, tráfico TENIDO hormozi-leads / hormozi-ads |
TENEDA DE LA ESTRATEGIA TENIDO , cobra más, prima, márgenes, precio punto TENIDO hormozi-pricing / hormozi-offers |
← Ventas Copiar Silencioso copia de ventas, landing page copy, texto de anuncio, escribir copia  hormozi-copy / hormozi-hooks |
← Paid Ads Silencio anuncios, anuncios pagados, publicidad, gasto publicitario, compras de medios hormozi-ads / hormozi-hooks |
 hormozi-content / hormozi-hooks |
← Hooks &quot; Headlines  durable ganchos, titulares, atención, pergaminos, apertura TEN hormozi-hooks / hormozi-copy |
Ø Lanzamiento de productos Silenciosos lanzamiento, ir al mercado, MVP, primeros clientes TEN hormozi-launch / hormozi-offers |
← Ventas Ropa Silencio cerca, llamada de ventas, objeciones, CLOSER, alta entrada TENIDO hormozi-closer / hormozi-offers |
TENCIÓN Taller Diseño TENIDO taller, seminario, evento, entrenamiento, masterclass TEN hormozi-workshop / hormozi-closer |
TENIDO Churn &amp; Retención TENIDO churn, retención, cancelación, LTV, mantener a los clientes TEN hormozi-retention / hormozi-scale |
← Escalada de Negocios Silencioso escala, crecer, $1M, $10M, $100M, expandir, alquilar Silencio hormozi-scale / hormozi-models |
TEN Business Model TENIDO modelo de negocio, ingresos recurrentes, suscripción, SaaS TEN hormozi-models / hormozi-scale |
TEN TERRITORIO DE TERRENO TENER auditar, evaluar, diagnosticar, embotellar, problemas TEN hormozi-audit / hormozi-models |
TENIDO Estrategia General TENIDO estrategia, consejo, dirección, siguiente paso, mentor TENIDO hormozi-advisor / hormozi-chief |

**Reglas de puntuación:**
- Contar coincidencias de palabras clave por dominio
- 2+ coincidencias por encima de otras --> ruta al especialista principal de ese dominio
- Tie o cross-domain -- Español Hormozi Respuestas principales utilizando el objetivo de Ecuación de Valor
- No hay partido claro -- Conf preguntar sobre el escenario de negocios y el cuello de botella primario

### Fase 3a: Respuesta Transversal

Si la solicitud es general o cross-domain:
- Aplicar la Ecuación de Valores para diagnosticar el problema central
- Identificar qué palanca (Dream Resultado, probabilidad, retraso del tiempo, esfuerzo) necesita trabajo
- Referencia de qué especialistas podrían profundizar más

### Fase 3b: Ruta específica del dominio

Si la solicitud se asigna claramente a un dominio:
1. ** Respuesta rápida primero** (3-5 líneas mínimo + referencia marco Hormozi)
2. **Reino:** Nombre del especialista, explique su valor único, proporcione el comando de activación
   - Ejemplo: "Tu oferta necesita el marco de Grand Slam. Activar con `@hormozi-squad:hormozi-offers`"

### Fase 4: Evaluación de confianza

| Confianza | Criterios | Acción |
|------------|----------|--------|
| ALTA | Más de 3 coincidencias de palabras clave en un dominio | Ruta con confianza al especialista primario |
| MEDIANO | 1-2 coincidencias o divididas en 2 dominios | Responder + sugerir 2 especialistas |
TEN LOW TENEDN Ninguna clara coincidencia o vaga solicitud TEN Respuesta con la Ecuación de Valor, haga aclaración pregunta TENIDO

---

## Formato de salida

```markdown
## Diagnosis
**Category:** {domain | cross-cutting}
**Confidence:** {HIGH | MEDIUM | LOW}
**Specialist:** {Name} ({agent-id}) | Direct Answer

### Quick Answer
{3-10 line answer using Hormozi frameworks}

### Recommended Next Step
{Route instruction with activation command, or follow-up question}
```

---

## Condiciones de veto

- NUNCA realice rutas sin proporcionar primero una respuesta rápida
- NUNCA ruta cuando la confianza es LOW - respuesta utilizando la Ecuación de Valor y hacer preguntas aclaradoras
- NUNCA cargue un archivo de agente especializado durante el diagnóstico
- Nunca adivina el escenario del negocio - preguntar si no está claro
- Nunca dar consejo genérico sin referenciar un marco específico de Hormozi

---

## Criterios de finalización

- [ ] Solicitud analizada y palabras clave extraídas
- Tipo de desafío de negocios identificado
- [ ] Catálogo de enrutamiento consultado con resultados puntuados
Respuesta rápida proporcionada con referencia marco de Hormozi
- [ ] Ruta especializada proporcionada (si domain-specific)
- [ ] Nivel de confianza indicado
