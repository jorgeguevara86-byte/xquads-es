---
task: diagnose()
responsavel: "@copy-chief"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: request
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: diagnosis
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Solicitud de persiana y palabras clave extraídas" 
  - "[ ] Catálogo de enrutamiento consultado con resultados puntuados" 
  - "[ ] Respuesta rápida proporcionada con enrutamiento especializado" 
---

# Task: Diagnostique Copywriting Request

** ID de la lista: * COPY-CHIEF-001
**Version:** 1.0.0
**Command:** `*diagnose`
**Orquestador:** Jefe de la Copia (copy-chief)
**Purpose:** Procesar solicitudes de redacción, proporcionar respuesta rápida, ruta a especialista.

---

## Overview

```
Solicitud de usuario → Analizar palabras clave → Coincidir con el catálogo de enrutamiento → Answer/Route → Salida
     │              │                    │                     │
     ▼              ▼                    ▼                     ▼
  Entrada cruda Extractor la intención Dominios de puntuación Respuesta rápida +
              + conciencia contra 17 dominios ruta especializada
              nivel + medio
```

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
Silencioso petición Silencio cadena Silencio Sugerencia de usuario Silencio Silencio Novato copywriting-related descripción voca
Silencio contexto Silencioso objeto Silencioso sesión estado Silencio No Silencio contexto del proyecto, audiencia objetivo, nivel de conciencia Silencio
Silencio medio Silencio cadena Silencioso Usuario prompt Silencio No TENIDO titular, correo electrónico, VSL, carta de ventas, anuncio, embudo, etc. TENIDO

---

## Preconditions

- Copia Squad está activo con el Jefe de Copia como agente de entrada
- Catálogo de enrutamiento cargado desde data/routing-catalog.yaml
- Los 22 agentes especializados registrados config.yaml

---

## Fases de Ejecución

### Fase 1: Analizar solicitud

1. Parse la solicitud del usuario para la intención de redacción
2. Extraiga las palabras clave principales y la intención
3. Identificar el medio de copia (cabeza, carta de ventas, correo electrónico, VSL, anuncio, embudo, etc.)
4. Determinar el nivel de conciencia si se menciona (sin darse cuenta, problem-aware, solution-aware, product-aware, most-aware)
5. Nota de dominios secundarios (por ejemplo, "secuencia de correo electrónico para un producto de salud" = email_sequence + financial_health_copy)

### Fase 2: Coincidencia contra el catálogo de enrutamiento

| Dominio | Palabras clave | Ruta a |
|--------|----------|----------|
TENCIÓN DE ABOGADO TENIDO, línea de asunto, gancho, atención, niveles de conciencia TENIDO eugene-schwartz / gary-halbert |
TENIDO Carta de Ventas TENIDO carta de venta, long-form, correo directo, copia larga  gary-halbert / john-carlton |
← Correo electrónico secuencia TENIDO, autoresponder, telenovela, nutricion TEN andre-chaperon / ben-settle |
TEN VSL TEN VSL, carta de venta de vídeo, video script, RMBC TEN stefan-georgi / jon-benson |
← Webinar Script ← webinar, script webinar, webinar perfecto, presentación ← russell-brunson / todd-brown |
← Oferta Creacion Silencioso oferta, oferta irresistible, garantía, bonificación, pila  dan-kennedy / joe-sugarman |
TENEDA RECIBRO ANTERIOR, landing page, opt-in, tripwire, upsell Silencio russell-brunson / frank-kern |
TENIDO Idea grande TENIDO gran idea, concepto de campaña, mecanismo único, E5 TEN todd-brown / eugene-schwartz |
TENEDOR Puntos de Bala TENIDO balas, fascinaciones, teasers, curiosidad TENIDO gary-bencivenga / clayton-makepeace |
← Correos electrónicos diarios Silencio diariamente email, compromiso, newsletter, anti-guru | ben-settle / dan-koe |
← Correo clásico Silencioso carta clásica, correo directo, carta de empatía, magalog TEN robert-collier / jim-rutz |
| Financial/Health TENIDO copia financiera, copia de salud, suplemento, inversión TEN clayton-makepeace / parris-lampropoulos |
TEN Brand Copy TENIDO brand copy, premium, elegante, sofisticado TEN david-ogilvy / david-deutsch |
← Ad Copy ← ad copy, anuncios pagados, Facebook ad, PPC, copia corta TEN dan-kennedy / frank-kern |
← Lanzamiento de la copia Silencioso lanzamiento, lanzamiento de productos, secuencia de lanzamiento, car frank-kern / russell-brunson |
TENIEN Personal Brand TENIDO marca personal, one-person empresa, creador, autoridad TENIDO dan-koe / ry-schwartz |
← Copiar Revisión Silencioso copia revisión, crítica, retroalimentación, análisis, reescribir  copy-chief / eugene-schwartz |

**Reglas de puntuación:**
- Contar coincidencias de palabras clave por dominio
- 2+ coincidencias por encima de otras --> ruta al especialista principal de ese dominio
- Tie o cross-domain -- Confía Copiar respuestas jefe directamente, sugiere 2 especialistas
- No hay coincidencia clara -- Confía en aclarar la pregunta sobre el nivel medio y de conciencia

### Fase 3a: Respuesta Transversal

Si la solicitud es general o cross-domain:
- Respuesta sintetizada a partir de múltiples tradiciones de redacción
- Referencia que especialistas podrían añadir profundidad
- Proporcionar asesoramiento de redacción de textos de forma inmediata

### Fase 3b: Ruta específica del dominio

Si la solicitud se asigna claramente a un dominio:
1. ** Respuesta rápida primero** (3-5 líneas mínimo + ejemplo concreto o referencia marco)
2. **Reino:** Nombre del especialista, explique su valor único, proporcione el comando de activación
   - Ejemplo: "Para los scripts VSL, el método RMBC de Stefan Georgi es el estándar de oro. Activar con `@copy-squad:stefan-georgi`"

### Fase 4: Evaluación de confianza

| Confianza | Criterios | Acción |
|------------|----------|--------|
| ALTA | Más de 3 coincidencias de palabras clave en un dominio | Ruta con confianza al especialista primario |
| MEDIANO | 1-2 coincidencias o divididas en 2 dominios | Responder + sugerir 2 especialistas |
TENIDO TENIDO TENIDO No hay partido claro o medio ambiguo TENIDO Respuesta directamente, preguntar aclaración pregunta TENIDO

---

## Formato de salida

```markdown
## Diagnosis
**Category:** {domain | cross-cutting}
**Confidence:** {HIGH | MEDIUM | LOW}
**Specialist:** {Name} ({agent-id}) | Direct Answer

### Quick Answer
{3-10 line answer with concrete copywriting advice}

### Recommended Next Step
{Route instruction with activation command, or follow-up question}
```

---

## Condiciones de veto

- NUNCA realice rutas sin proporcionar primero una respuesta rápida
- NUNCA enrute cuando la confianza sea BAJA: responda directamente y haga preguntas aclaratorias
- NUNCA cargue un archivo de agente especializado durante el diagnóstico
- Nunca adivina cuándo el medio de copia es ambiguo - pregunte al usuario
- Nunca asignar nivel de conciencia sin señales explícitas de la solicitud

---

## Criterios de finalización

- [ ] Solicitud analizada y palabras clave extraídas
- [ ] Copiado medio identificado (o aclaración solicitada)
- [ ] Catálogo de enrutamiento consultado con resultados puntuados
Respuesta rápida proporcionada con un consejo de acción
- [ ] Ruta especializada proporcionada (si domain-specific)
- [ ] Nivel de confianza indicado
