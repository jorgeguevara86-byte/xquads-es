---
task: buildMessage()
responsavel: "@donald-miller"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: campaign_brief
    tipo: markdown
    origem: marketing-chief
    obrigatorio: true
Saida:
  - campo: brandscript
    tipo: markdown
    destino: Console
    persistido: false
Checklist:
  - "[ ] Un-liner creado (Problema + Solución + Resultado)" 
  - "[ ] BrandScript SB7 completo" 
  - "[ ] Esqueleto de embudo definido" 
---

# Task: Construir un Mensagem (StoryBrand)

** ID de la lista: **Mand:** `*build-message` · **Agente:** Donald Miller (@donald-miller)
**Purpose:** Define la columna vertebral de la campaña — lo que decimos y a quién— antes de cualquier copia, creatividad o tráfico.

## Fases de Ejecución
1. **BrandScript SB7** — Personaje (cliente=héroe) → Problema (externo/interno/filosófico→ Guía (la marca) → Plan → CTA → Éxito → Fallo evitado.
2. **Uno-liner** — Problema + fórmula de solución + Resultado, corto e inolvidable.
3. ** Prueba de la fuga** — un extraño entiende en 5 segundos: ¿qué ofrece, cómo mejorar mi vida, qué hago para comprar?
4. **Esqueletón de túneles** one-liner → site/wireframe → Carbo digital → secuencia de Nurture → Secuencia de ventas.

## Formato de salida
```
🧭 BRANDSCRIPT — {marca}
Una línea:  {frase}
Hero:      {cliente}   ext/int/filo}
Guía:       {marca}      {passos}
CTA:        {direto}     {transformação}
Funil:      {esqueleto}
```

## Condiciones de veto
- Nunca posicionar la marca como el héroe - el cliente es el héroe, la marca es la guía.
- Si el mensaje confunde, redo: "Si te metes, pierdes".

## Criterios de finalización
Un solo repaso pasa la prueba de la gracia · [ ] BrandScript SB7 complete · [ ] embudo esquemático
