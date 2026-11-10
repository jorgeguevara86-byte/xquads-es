---
task: auditBrand()
responsavel: "@brand-chief"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: brand
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: industry
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: "Informe de salud de la marca" 
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Valor de marca obtenido en 5 pilares de Aaker" 
  - "[ ] Identidad evaluada en 6 facetas de Kapferer" 
  - "[ ] Recomendaciones priorizadas con enrutamiento especializado" 
---

# Tarea: Auditar marca

**ID de tarea:** MARCA-001
**Version:** 1.0.0
**Command:** `*audit-brand`
**Agente:** Jefe de marca (brand-chief) o David Aaker (david-aaker)
**Propósito:** Auditoría integral de salud de marca que evalúa el valor, el posicionamiento, la identidad y la percepción del mercado.

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
| marca | cadena | Mensaje de usuario | Sí | Nombre de la marca y breve descripción |
| industria | cadena | Mensaje de usuario | Sí | Contexto de la industria y el mercado |
| brand_assets | lista | Mensaje de usuario | No | Logotipo, sitio web, perfiles sociales, materiales de marketing |
| competidores | lista | Mensaje de usuario | No | Competidores clave para el contexto de posicionamiento |
| audiencia | cadena | Mensaje de usuario | No | Descripción del público objetivo |
| brand_age | cadena | Mensaje de usuario | No | ¿Cuánto tiempo existe la marca?
| known_issues | cadena | Mensaje de usuario | No | Desafíos de la marca autoidentificada |

---

## Preconditions

- La marca existe con cierta presencia en el mercado (aunque sea mínima)
- Al menos recursos de marca básicos disponibles para revisión

---

## Fases de Ejecución

### Fase 1: Evaluación del valor de la marca (modelo de Aaker)
1. Evaluar los 5 pilares del valor de marca:
   - **Conocimiento de marca:** Nivel de reconocimiento y recuerdo en el mercado objetivo
   - **Calidad percibida:** Cómo califica la audiencia la calidad frente a la competencia
   - **Asociaciones de marca:** Lo que les viene a la mente cuando la gente escucha el nombre de la marca.
   - **Lealtad de marca:** Tasa de compra repetida, promoción, resistencia al cambio
   - **Activos Propietarios:** Marcas, patentes, canales de distribución
2. Califique cada pilar (1-10)
3. Identificar los pilares más fuertes y más débiles
4. Comparación con la competencia cuando hay datos disponibles

### Fase 2: Evaluación de identidad (Prisma de Kapferer)
1. Evaluar las 6 facetas de la identidad de marca:
   - **Físico:** Elementos visuales, logo, colores, packaging, diseño de producto.
   - **Personalidad:** Rasgos de carácter, voz, tono, cualidades humanas.
   - **Cultura:** Valores, historia de origen, sistema de creencias
   - **Relación:** Cómo se relaciona la marca con sus clientes
   - **Reflexión:** Cómo se ven los clientes a través de la marca
   - **Autoimagen:** Cómo se sienten internamente los clientes al usar la marca
2. Identificar inconsistencias entre facetas.
3. Evaluar la alineación entre la identidad interna y la percepción externa.
4. Tenga en cuenta cualquier faceta que no esté definida o sea contradictoria

### Fase 3: Análisis de posicionamiento
1. Evaluar el posicionamiento actual:
   - ¿En qué categoría compite la marca?
   - ¿Cuál es el principal punto de diferenciación?
   - ¿El posicionamiento es claro, creíble y convincente?
2. Mapear el panorama competitivo:
   - ¿Dónde se posiciona cada competidor?
   - ¿Dónde están las posiciones abiertas (espacios en blanco)?
   - ¿La marca se encuentra en una posición concurrida o no concurrida?
3. Pruebe la claridad del posicionamiento: ¿Alguien puede describir qué hace que esta marca sea diferente en una oración?

### Fase 4: Punto de contacto y auditoría de coherencia
1. Revise la coherencia de la marca en todos los puntos de contacto:
   - Identidad visual: uso del logo, colores, tipografía.
   - Identidad verbal: mensajes, tono, frases clave
   - Presencia digital: sitio web, redes sociales, correo electrónico
   - Experiencia del cliente: soporte, onboarding, packaging
2. Identificar inconsistencias y brechas
3. Califique la coherencia general de la marca (1-10)
4. Proporcionar una lista de arreglos priorizados

---

## Formato de salida

```markdown
## Brand Audit: {Brand Name}

**Industry:** {industry}
**Brand Age:** {age}
**Overall Brand Health Score:** {X}/100
**Verdict:** {Critical / Needs Work / Healthy / Strong / Premium}

---

### Brand Equity Scorecard (Aaker)

| Pillar | Score | Strengths | Gaps |
|--------|-------|-----------|------|
| Awareness | X/10 | {note} | {note} |
| Perceived Quality | X/10 | {note} | {note} |
| Associations | X/10 | {note} | {note} |
| Loyalty | X/10 | {note} | {note} |
| Proprietary Assets | X/10 | {note} | {note} |

### Identity Prism (Kapferer)

| Facet | Current State | Consistency | Issue |
|-------|--------------|-------------|-------|
| Physique | {description} | {aligned/misaligned} | {note} |
| Personality | {description} | {aligned/misaligned} | {note} |
| Culture | {description} | {aligned/misaligned} | {note} |
| Relationship | {description} | {aligned/misaligned} | {note} |
| Reflection | {description} | {aligned/misaligned} | {note} |
| Self-image | {description} | {aligned/misaligned} | {note} |

### Positioning Map
**Current Position:** {description}
**Differentiation:** {clear/unclear}
**White Space Opportunities:** {identified gaps}
**Competitive Overlap:** {where you collide with competitors}

### Consistency Score
**Overall Coherence:** {X}/10
**Strongest Touchpoint:** {touchpoint}
**Weakest Touchpoint:** {touchpoint}

### Prioritized Recommendations
| Priority | Area | Issue | Recommended Fix | Agent |
|----------|------|-------|-----------------|-------|
| 1 | {area} | {issue} | {fix} | {specialist} |

### What to Protect
{Elements that are working well and must be preserved}
```

---

## Condiciones de veto

- NUNCA realice una auditoría sin revisar los activos reales de la marca: la teoría sin observación es adivinar
- NUNCA califique sin proporcionar evidencia específica para cada calificación
- NUNCA ignore el contexto de la competencia: la fortaleza de la marca siempre es relativa
- NUNCA proporcione solo críticas: identifique y proteja lo que funciona
- NUNCA recomiendes cambiar todo de una vez: prioriza sin piedad

---

## Criterios de finalización

- [ ] Valor de marca obtenido en 5 pilares de Aaker
- [ ] Identidad evaluada en 6 facetas de Kapferer
- [ ] Posicionamiento analizado con contexto competitivo
- [ ] Coherencia del punto de contacto auditada
- [ ] Puntuación de salud general calculada
- [ ] Recomendaciones priorizadas con enrutamiento especializado
- [ ] Fortalezas identificadas y marcadas para protección
