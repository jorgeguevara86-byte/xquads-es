---
task: designArchitecture()
responsavel: "@david-aaker"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: parent_brand
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: products
    tipo: list
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: "Mapa de arquitectura de marca" 
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Modelo de arquitectura seleccionado con justificación puntuada" 
  - "[ ] Todo el products/services mapeado en la arquitectura" 
  - "[ ] Marco de gobernanza establecido" 
---

# Tarea: Diseño de arquitectura de marca

**ID de tarea:** MARCA-005
**Version:** 1.0.0
**Command:** `*design-architecture`
**Agente:** David Aaker (david-aaker)
**Propósito:** Diseñar la estrategia de arquitectura de marca para organizaciones multi-product o multi-brand .

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
| parent_brand | cadena | Mensaje de usuario | Sí | Nombre de marca principal o principal |
| productos | lista | Mensaje de usuario | Sí | Todos los productos, servicios o sub-brands |
| market_context | cadena | Mensaje de usuario | Sí | Industria y panorama competitivo |
| audience_segments | lista | Mensaje de usuario | No | Diferentes grupos de audiencia atendidos |
| growth_plans | cadena | Mensaje de usuario | No | Nuevos productos previstos o ampliaciones de mercado |
| current_architecture | cadena | Mensaje de usuario | No | Estructura de marca existente, si la hubiera |

---

## Preconditions

- Existen (o están planificados) múltiples productos, servicios o marcas.
- Necesidad de organizarlos en una estructura coherente

---

## Fases de Ejecución

### Fase 1: Selección del modelo de arquitectura
1. Evaluar los 4 modelos de arquitectura de marca:
   - **Branded House:** Una marca maestra, todos los productos se basan en ella
     - Ejemplo: Google (Google Maps, Google Drive, Google Fotos)
     - Mejor cuando: marca matriz sólida, productos relacionados, audiencia compartida
   - **House of Brands:** Marcas independientes, el padre es invisible
     - Ejemplo: P&G (Tide, Pampers, Gillette, todos separados)
     - Mejor cuando: Los productos sirven a audiencias diferentes o podrían entrar en conflicto
   - **Marcas respaldadas:** Submarcas respaldadas por la matriz
     - Ejemplo: Marriott (Courtyard by Marriott, Residence Inn by Marriott)
     - Mejor cuando: Las marcas secundarias necesitan independencia pero se benefician de la credibilidad de los padres
   - **Híbrido:** Combinación de modelos en todo el portafolio
     - Ejemplo: Amazon (Amazon Prime = casa de marca, Ring = respaldada, Whole Foods = casa de marcas)
     - Mejor cuando: La cartera es diversa con diferentes necesidades estratégicas
2. Califica cada modelo según el contexto específico de la marca
3. Recomendar el modelo principal con fundamento.

### Fase 2: Diseño de Arquitectura
1. Asigna cada product/service/sub-brand a la arquitectura elegida
2. Defina la estrategia de nomenclatura:
   - Nombres descriptivos (Google Maps): claros pero menos distintivos
   - Nombres sugerentes (Amazon Prime) — implica beneficio
   - Nombres abstractos (Alexa): distintivos pero requieren inversión
   - Alfanumérico (iPhone 15): versiones y jerarquía
3. Defina la relación visual entre el padre y sub-brands:
   - Reglas de bloqueo de logotipos (cómo aparecen los logotipos juntos)
   - Estrategia de color (paleta compartida versus distinta por sub-brand)
   - Relación tipográfica
4. Defina la relación verbal:
   - Cómo sub-brands hace referencia al padre en la copia
   - Estrategia de lema (compartido vs individual)
   - Reglas de coherencia de voz

### Fase 3: Asignación de roles
1. Asignar un rol estratégico a cada marca del portafolio:
   - **Master Brand:** La principal fuente de capital y confianza
   - **Vaca de ingresos:** Marca establecida que financia el crecimiento
   - **Estrella:** Marca de alto crecimiento que impulsa el futuro
   - **Fighter:** Marca que compite en precio para proteger marcas premium
   - **Flanker:** Marca que se extiende a un mercado adyacente
   - **Silver Bullet:** Marca que realza la imagen de los padres
2. Defina la prioridad de inversión para cada rol de marca.
3. Identificar marcas para cerrar, fusionar o desinvertir
4. Mapear la cobertura de segmentos de audiencia del portafolio

### Fase 4: Migración y Gobernanza
1. Si cambia de la arquitectura actual, defina el plan de migración:
   - Fase 1: Lo que cambia inmediatamente
   - Fase 2: Qué transiciones en 6 a 12 meses
   - Fase 3: ¿Cuál es el estado estacionario final?
2. Definir el marco de gobernanza:
   - Quién aprueba el nuevo sub-brands
   - Criterios para agregar una nueva marca versus extender la existente
   - Reglas de convención de nomenclatura para adiciones futuras
   - Árbol de decisión de jerarquía de marcas
3. Documente las reglas anti-dilution :
   - Número máximo de sub-brands antes de confusión
   - Diferenciación mínima requerida entre sub-brands
   - Cuándo fusionar marcas superpuestas

---

## Formato de salida

```markdown
## Brand Architecture: {Parent Brand}

**Model:** {branded-house / house-of-brands / endorsed / hybrid}
**Total Brands:** {count}
**Architecture Clarity Score:** {X}/10

---

### Architecture Map

{Visual text representation of the brand hierarchy}

### Brand Portfolio

| Brand | Role | Relationship to Parent | Audience | Status |
|-------|------|----------------------|----------|--------|
| {brand} | {role} | {master/endorsed/independent} | {segment} | {active/planned/sunset} |

### Naming Strategy
**Convention:** {descriptive / suggestive / abstract}
**Rules:** {naming guidelines for new additions}

### Visual Relationship
| Element | Parent | Sub-Brand A | Sub-Brand B |
|---------|--------|------------|------------|
| Logo | {rule} | {rule} | {rule} |
| Colors | {rule} | {rule} | {rule} |
| Typography | {rule} | {rule} | {rule} |

### Migration Plan (if applicable)
| Phase | Timeline | Changes |
|-------|----------|---------|

### Governance Rules
- New brand approval: {process}
- Extend vs create decision: {criteria}
- Maximum portfolio size: {N}
- Review cadence: {frequency}

### Portfolio Gaps
{Audience segments or markets not currently covered}
```

---

## Condiciones de veto

- NUNCA diseñe arquitectura sin comprender toda la cartera de productos
- NUNCA elijas un modelo basado en la estética: debe servir a la estrategia empresarial
- NUNCA crees más sub-brands de los que el mercado puede diferenciar
- NUNCA migre todas las marcas a la vez: realice la transición por fases
- NUNCA te saltes la gobernanza: sin reglas, la arquitectura decaerá

---

## Criterios de finalización

- [ ] Modelo de arquitectura seleccionado con justificación puntuada
- [ ] Todo el products/services mapeado en la arquitectura
- [ ] Estrategia de nomenclatura definida con convenciones
- [ ] Relaciones visuales y verbales documentadas
- [ ] Roles estratégicos asignados a cada marca
- [ ] Plan de migración creado (si se cambia la arquitectura)
- [ ] Marco de gobernanza establecido
- [ ] Se identificaron brechas en la cartera
