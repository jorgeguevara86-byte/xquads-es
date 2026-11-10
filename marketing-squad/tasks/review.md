---
task: review()
responsavel: "@marketing-chief"
responsavel_type: Agent
atomic_layer: Task
elicit: false

Entrada:
  - campo: campaign_assets
    tipo: markdown
    origem: pipeline
    obrigatorio: true
Saida:
  - campo: quality_verdict
    tipo: string
    destino: Console
    persistido: false
Checklist:
  - "[ ] 8 criterios de calidad evaluados" 
  - "[ ] Consistencia entre las 4 disciplinas verificadas" 
  - "[ ] Vered PASS/REVISE emitidas" 
---

# Task: Revisão de Qualidade do Chief

** ID de la lista: **Mand:** `*review` · **Agente:** Jefe de Marketing (Mira)
**Purpose:** Validar la campaña contra el estándar de la Escuadrilla y asegurar la COERENCE entre mensaje, copia, creativo y tráfico.

##Execution — 8 criteria (checklist output-quality.md)
1. ¿El mensaje pasa la prueba de la mancha (5s)?
2. ¿El titular se casa con el nivel de conciencia?
3. ¿Oferta CTA clara e irresistible?
4. Criativo servir a una gran idea e para o pergamino?
5. Optimizado Creativo para Formato de Plataforma?
6. Campaña estructurada por objetivos, con la temperatura pública correcta?
7. Mensaje + copia + creatividad + segmentación contar una historia?
8. ¿Hay una métrica primaria definida?

## Formato de salida
```
 {campanha}
Criterios: {8/8 
Consistencia:
Veredicto: PASS
```

## Condiciones de veto
- REVISIÓN (blocks) si algún criterio CRITICAL falla o si hay incoherencia entre las disciplinas.

## Criterios de finalización
- [ ] 8 criterios evaluados · [ ] Consistencia verificada · [ ]
