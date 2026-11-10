---
task: createCreatives()
responsavel: "@visual-generator"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: campaign_copy
    tipo: markdown
    origem: eugene-schwartz
    obrigatorio: true
Saida:
  - campo: creative_assets
    tipo: markdown
    destino: Console
    persistido: false
Checklist:
  - "[ ] Aspiraciones de IA estructuradas por activos" 
  - "[ ] Creativos optimizados para plataformas" 
  - "[ ] Visual servir a una gran idea da copia" 
---

# Task: Create Visual Assets

** ID de la lista: **Mand:** `*create-creatives` · **Ejecutor:** Generador visual (@visual-generator)
**Purpose:** Transformar la Idea Grande de Copia en activos de marketing visual — la mirada sirve para la venta, no decora.

## Fases de Ejecución
1. **Dirección**: Extraiga la Gran Idea y el tono de la copia; defina estilo/paleta/identidade.
2. **Assets** — anuncio creativo, miniaturas, banners, iconos, ilustraciones, activos sociales.
3. **Insinuaciones de la AI** - incitaciones estructuradas (Midjourney/DALL-E/Flux): tema, estilo, composición, iluminación, paleta, parámetros.
4. **Optimización por plataforma** — formatos y proporciones por canal (Feed 1:1/4:5, Stories/Reels 9:16, YouTube 16:9, etc.).

## Formato de salida
```
🎨 CRIATIVOS — {campanha}
Gran Idea: {idea servida}
Estilo:     {estilo/paleta}
Assets:     {lista}
Prompts IA: {prompts por asset}
Formatos: {por plataforma}
```

## Condiciones de veto
- Nunca crear un look decorativo desconectado copy/Big Idea.
- Nunca lo entregas fuera de la formato/proporção desde la plataforma de destino.

## Criterios de finalización
[ ] Prompts Estructurados · [ ] Formatos de plataforma · [ ] Visual sirve Big Idea
