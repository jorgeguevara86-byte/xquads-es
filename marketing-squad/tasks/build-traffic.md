---
task: buildTraffic()
responsavel: "@pedro-sobral"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: creative_assets
    tipo: markdown
    origem: visual-generator
    obrigatorio: true
Saida:
  - campo: media_plan
    tipo: markdown
    destino: Console
    persistido: false
Checklist:
  - "[ ] Estructura de la campaña por objetivo" 
  - "[ ] Públicos definidos por temperatura" 
  - "Presupuesto (CBO/ABO) y plan de prueba" 
---

# Task: Mount Traffic

** ID de usuario: **Mand:** `*build-traffic` · **Agente:** Pedro Sobral (@pedro-sobral)
**Purpose:** Distribuir y escalar la campaña a través del tráfico pagado (enfoque Meta Ads), recibir copia + oferta creativa +.

## Fases de Ejecución
1. **Objetivo** — elegir el tipo de campaña entre los 3 elementos esenciales: audiencia, leads o ventas ("90% de resultados").
2. **Public** — segmentación de temperatura: frío (en inglés)topo/captação), cálido y cálido (retargeting/conversão).
3. **Structure** — 4-8 conjuntos de anuncios; CBO vs ABO según la fase; "creativo es el nuevo público".
4. **Test** - plan de prueba criativos/hooks; criterios de medición y corte.
5. ** Escala / Lanzamiento** — horizontal vs escala vertical; si se lanzan, campañas de onda.

## Formato de salida
```
 {campanha}
Objetivo: {audiencia
Estructura: {campas / conjuntos de anuncios / CBO-ABO}
Público: {frío / caliente / caliente}
Creativos: {variaciones para probar}
Presupuesto:   {distribuição}
Prueba: {plan + criterio de corte}
```

## Condiciones de veto
- Nunca se levante sin un propósito claro o con un público mal segmentado.
- Nunca suba antes de validar al ganador creativo.

## Criterios de finalización
Estructura por objetivo · [ ] Public by temperature · [ ] Presupuesto + plan de prueba
