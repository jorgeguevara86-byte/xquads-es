---
task: diagnose()
responsavel: "@copy-master-chief"
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
  - "[ ] Catálogo de Routing consultado con resultados marcados (27 dominios, 32 agentes)" 
  - "[ ] Respuesta rápida proporcionada con enrutamiento especializado" 
---

# Task: Diagnostique Copywriting Request

** ID de la lista: * COPY-M-CHIEF-001
**Version:** 2.0.0
**Command:** `*diagnose`
**Orquestador:** Copia Jefe de Jefe (copy-master-chief)
**Purpose:** Probar solicitudes de redacción, proporcionar respuesta rápida, llegar a los mejores 32 agentes especializados de 27 dominios.

---

## Overview

```
Solicitud de usuario - otorgante Parse Palabras clave - Match Routing Catalog - confianza Answer/Route - Producto
     |              |                    |                     |
     v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v v
  Entrada cruda Extractor la intención Dominios de puntuación Respuesta rápida +
              + conciencia contra 27 dominios ruta especializada
              nivel + medio (32 agentes)
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

- Copiar Master Squad está activo con el Jefe de la Copia como agente de entrada
- Catálogo de oxidación cargado con todos los 27 dominios
- Los 32 agentes especializados registrados

---

## Fases de Ejecución

### Fase 1: Analizar solicitud

1. Parse la solicitud del usuario para la intención de redacción
2. Extraiga las palabras clave principales y la intención
3. Identificar el medio de copia (cabeza, carta de ventas, correo electrónico, VSL, anuncio, embudo, webinar, pitch, etc.)
4. Determinar el nivel de conciencia si se menciona (sin darse cuenta, problem-aware, solution-aware, product-aware, most-aware)
5. Nota de dominios secundarios (por ejemplo, "secuencia de correo electrónico para un producto de salud" = email_sequence + financial_health_copy)

### Fase 2: Coincidencia contra el catálogo de oxidación (27 Dominios, 32 Agentes)

| Dominio | Palabras clave | Ruta a |
|--------|----------|----------|
TENCIÓN DE ABOGADO TENIDO, línea de asunto, gancho, atención, niveles de conciencia TENIDO eugene-schwartz / gary-bencivenga |
TENIDO Carta de Ventas TENIDO carta de venta, long-form, correo directo, copia larga  gary-halbert / john-carlton |
← Correo electrónico secuencia TENIDO, autoresponder, telenovela, nutricion TEN andre-chaperon / ben-settle |
TEN VSL TEN VSL, carta de venta de vídeo, video script, RMBC TEN stefan-georgi / jon-benson |
← Webinar Script ← webinar, script webinar, webinar perfecto, presentación ← russell-brunson / todd-brown |
← Pitch Deck ¦ pitch, plataforma de lanzamiento, inversor, método STRONG, control de marco TEN oren-klaff |
← Oferta Creacion Silencioso oferta, oferta irresistible, garantía, bonificación, pila  dan-kennedy / alex-hormozi |
TENEDA RECIBRO ANTERIOR, landing page, opt-in, tripwire, upsell Silencio russell-brunson / frank-kern |
TENIDO Idea grande TENIDO gran idea, concepto de campaña, mecanismo único, E5 TEN todd-brown / eugene-schwartz |
TENEDOR Puntos de Bala TENIDO balas, fascinaciones, teasers, curiosidad TENIDO gary-bencivenga / clayton-makepeace |
← Correos electrónicos diarios Silencio diariamente email, compromiso, newsletter, anti-guru | ben-settle / dan-koe |
← Correo clásico Silencioso carta clásica, correo directo, carta de empatía, magalog TEN robert-collier / jim-rutz |
← Copia financiera Silencioso copia financiera, inversión, cartera, trading TEN clayton-makepeace / parris-lampropoulos |
← Salud Copiar Silencioso salud copia, suplemento, bienestar, fitness TENIDO parris-lampropoulos / evaldo-albuquerque |
TEN Brand Copy TENIDO brand copy, premium, elegante, sofisticado TEN david-ogilvy / david-deutsch |
← Ad Copy ← ad copy, anuncios pagados, Facebook ad, PPC, copia corta TEN dan-kennedy / frank-kern |
← Lanzamiento de la copia Silencioso lanzamiento, lanzamiento de productos, secuencia de lanzamiento, car frank-kern / russell-brunson |
TENIEN Personal Brand TENIDO marca personal, one-person empresa, creador, autoridad TENIDO dan-koe / ry-schwartz |
← Copiar Revisión Silencioso copia revisión, crítica, retroalimentación, análisis, reescribir  copy-master-chief / eugene-schwartz |
TENED Psicología TENIDO persuasión, influencia, psicología, desencadenantes, cumplimiento TENIDO robert-cialdini / blair-warren |
Silencioso Negociación Copiar Silencioso negociación, manejo de objeciones, cierre, empatía táctica chris-voss |
← SaaS Copy ← SaaS, software, prueba, a bordo, product-led | joanna-wiebe |
Silencioso de optimización de conversión Silencioso CRO, velocidad de conversión, A/B prueba, optimización de páginas TENIDO joanna-wiebe / joe-sugarman |
← Creenciales Cambio de creencia, paradigma, visión del mundo, puente epifanía TEN evaldo-albuquerque / todd-brown |
← Historia-ventas escritas Silencio historia, narración, historia de origen, epifanía TEN gary-halbert / russell-brunson |
← Oferta Arquitectura Silencioso valor ecuación, Grand Slam oferta, precios, valor pila  alex-hormozi / dan-kennedy |
TENED Publicidad científica TENIDO pruebas, prueba de división, métricas, data-driven copy FORMULADA ANTERIOR claude-hopkins / john-caples |

**Reglas de puntuación:**
- Contar coincidencias de palabras clave por dominio
- 2+ partidos por encima de otros - ruta de confianza a la especialista primaria de ese dominio
- Tie o cross-domain - Confía en Copiar respuestas del Jefe directamente, sugiere 2 especialistas
- No hay coincidencia clara - confiar preguntar a aclarar la cuestión sobre el nivel medio y de conciencia

### Fase 3a: Respuesta Transversal

Si la solicitud es general o cross-domain:
- Respuesta sintetizada a partir de múltiples tradiciones de redacción
- Referencia que especialistas podrían añadir profundidad
- Proporcionar asesoramiento de redacción de textos de forma inmediata

### Fase 3b: Ruta específica del dominio

Si la solicitud se asigna claramente a un dominio:
1. ** Respuesta rápida primero** (3-5 líneas mínimo + ejemplo concreto o referencia marco)
2. **Reino:** Nombre del especialista, explique su valor único, proporcione el comando de activación
   - Ejemplo: "Para los scripts VSL, el método RMBC de Stefan Georgi es el estándar de oro. Activar con `@copy-master:stefan-georgi`"

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
- [ ] Catálogo de Routing consultado con resultados marcados (27 dominios, 32 agentes)
Respuesta rápida proporcionada con un consejo de acción
- [ ] Ruta especializada proporcionada (si domain-specific)
- [ ] Nivel de confianza indicado
