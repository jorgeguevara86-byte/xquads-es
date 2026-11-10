---
task: diagnose()
responsavel: "@brand-chief"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: request
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: "Informe de diagnóstico" 
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Solicitud analizada y dominio de marca identificado" 
  - "[ ] Catálogo de enrutamiento consultado con resultados puntuados" 
  - "[ ] Respuesta rápida proporcionada con enrutamiento especializado" 
---

# Tarea: Diagnosticar el desafío de la marca

**ID de tarea:** BRAND-CHIEF-001
**Version:** 1.0.0
**Command:** `*diagnose`
**Orquestador:** Jefe de marca (brand-chief)
**Propósito:** Clasificar los desafíos de la marca, brindar una respuesta rápida y encaminarlo hacia un especialista.

---

## Overview

```
Solicitud de usuario → Analizar palabras clave → Coincidir con el catálogo de enrutamiento → Answer/Route → Salida
     │              │                    │                     │
     ▼              ▼                    ▼                     ▼
  Entrada sin procesar Extraer marca Dominios de puntuación Respuesta rápida +
              tipo de desafío contra ruta especializada de 13 dominios
              + etapa de madurez + enrutamiento de madurez (maturity-aware)
```

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
| solicitud | cadena | Mensaje de usuario | Sí | Descripción brand-related no vacía |
| contexto | objeto | Estado de la sesión | No | Etapa de la empresa, industria, activos de marca existentes |
| madurez | cadena | Mensaje de usuario | No | pre-launch, startup, crecimiento, empresa, lujo |

---

## Preconditions

- Brand Squad está activo con Brand Chief como agente de entrada
- Catálogo de enrutamiento cargado desde data/routing-catalog.yaml
- Los 14 agentes especialistas registrados en config.yaml
- Ruta de madurez de marca disponible para clasificación stage-aware 

---

## Fases de Ejecución

### Fase 1: Analizar solicitud

1. Analizar el desafío de marca del usuario.
2. Extraiga las palabras clave principales y la intención
3. Identificar el dominio de la marca (valor, identidad, posicionamiento, mensajería, arquitectura, naming, etc.)
4. Identifique la etapa de madurez de la marca, si se menciona (pre-launch, inicio, crecimiento, empresa, lujo)
5. Tenga en cuenta si la solicitud implica una tensión conocida (diferenciación versus distinción, emocional versus evidencia)

### Fase 2: Coincidencia contra el catálogo de enrutamiento

| Dominio | Palabras clave | Ruta a |
|--------|----------|----------|
| Valor de marca | valor de marca, valor de marca, lealtad, notoriedad, asociaciones | david-aaker / kevin-keller |
| Identidad de marca | identidad de marca, prisma de identidad, ADN, personalidad, cultura | jean-noel-kapferer / alina-wheeler |
| Posicionamiento | posicionamiento, categoría, enfoque, diferenciación, poseer una palabra | al-ries / marty-neumeier |
| Basado en evidencia | cómo crecen las marcas, disponibilidad mental, activos distintivos, alcance | byron-sharp / kevin-keller |
| Mensajería | StoryBrand, mensajería, one-liner, guión de marca, aclarar mensaje | donald-miller / miller-sticky-brand |
| Identidad Visual | logo, identidad visual, lineamientos de marca, sistema de diseño, puntos de contacto | alina-wheeler / archetype-consultant |
| Cultura de marca | cultura de marca, marca empleadora, marca interna, fusión | denise-yohn / donald-miller |
| Marca de inicio | marca startup, DTC, marca lanzamiento, marca desde el primer día, nueva marca | emily-heyward / marty-neumeier |
| Marca de lujo | lujo, premium, prestigio, estrategia de lujo, anti-laws | jean-noel-kapferer / david-aaker |
| Denominación | naming, nombre de marca, cambio de nombre, generación de nombre, dominio | naming-strategist / domain-scout |
| Arquetipo | arquetipo, personalidad de marca, personaje, Jung, héroe, rebelde | archetype-consultant / jean-noel-kapferer |
| Arquitectura de marca | arquitectura de marca, sub-brands, casa de marca, casa de marcas, portafolio | david-aaker / kevin-keller |
| Debate sobre la diferenciación | diferenciación vs distintividad, zag, diferenciación radical | marty-neumeier / byron-sharp |

**Ruta abreviada de madurez de marca:**
- Prelanzamiento --> emily-heyward, naming-strategist, domain-scout
- Startup --> emily-heyward, marty-neumeier, donald-miller
- Growth --> david-aaker, al-ries, kevin-keller
- Enterprise --> jean-noel-kapferer, denise-yohn, david-aaker
- Luxury --> jean-noel-kapferer, david-aaker, alina-wheeler

**Reglas de puntuación:**
- Contar coincidencias de palabras clave por dominio
- 2+ coincidencias por encima de otras --> ruta al especialista principal de ese dominio
- Etapa de madurez + coincidencia de dominio --> refinar el enrutamiento usando el acceso directo de madurez
- Empate o cross-domain --> Brand Chief responde con multi-framework síntesis
- No hay una coincidencia clara --> pregunte sobre la etapa de madurez de la marca y el desafío principal

### Fase 3a: Respuesta Transversal

Si la solicitud es general o cross-domain:
- Sintetizar la respuesta a partir de múltiples marcos de marca
- Note las tensiones relevantes (diferenciación versus distintividad, emocional versus evidencia)
- Referencia de qué especialistas podrían profundizar más

### Fase 3b: Ruta específica del dominio

Si la solicitud se asigna claramente a un dominio:
1. **Respuesta rápida primero** (mínimo 3-5 líneas + referencia del marco)
2. **Ruta:** Nombre al especialista, explique su marco único, proporcione el comando de activación
   - Ejemplo: "Para el posicionamiento de marca, Al Ries escribió literalmente el libro. Activar con `@brand-squad:al-ries`"

### Fase 4: Evaluación de confianza

| Confianza | Criterios | Acción |
|------------|----------|--------|
| ALTA | Más de 3 coincidencias de palabras clave en un dominio | Ruta con confianza al especialista primario |
| MEDIANO | 1-2 coincidencias o divididas en 2 dominios | Responder + sugerir 2 especialistas |
| BAJO | Ninguna coincidencia clara o muy vaga | Responde directamente, pregunta sobre la etapa de madurez y el desafío |

---

## Formato de salida

```markdown
## Diagnosis
**Category:** {domain | cross-cutting}
**Confidence:** {HIGH | MEDIUM | LOW}
**Brand Maturity:** {pre-launch | startup | growth | enterprise | luxury | unknown}
**Specialist:** {Name} ({agent-id}) | Direct Answer

### Quick Answer
{3-10 line answer with brand framework reference}

### Recommended Next Step
{Route instruction with activation command, or follow-up question}
```

---

## Condiciones de veto

- NUNCA realice rutas sin proporcionar primero una respuesta rápida
- NUNCA enrute cuando la confianza sea BAJA: responda directamente y haga preguntas aclaratorias
- NUNCA cargue un archivo de agente especializado durante el diagnóstico
- NUNCA ignore la tensión entre diferenciación y distintividad cuando ambos dominios coinciden
- NUNCA asumas la etapa de madurez de la marca sin señales explícitas

---

## Criterios de finalización

- [ ] Solicitud analizada y palabras clave extraídas
- [ ] Dominio de marca identificado (o aclaración solicitada)
- [ ] Catálogo de enrutamiento consultado con resultados puntuados
- [ ] Respuesta rápida proporcionada con referencia del marco
- [ ] Ruta especializada proporcionada (si domain-specific)
- [ ] Nivel de confianza indicado
