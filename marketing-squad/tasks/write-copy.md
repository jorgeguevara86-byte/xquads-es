---
task: writeCopy()
responsavel: "@eugene-schwartz"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: brandscript
    tipo: markdown
    origem: donald-miller
    obrigatorio: true
Saida:
  - campo: campaign_copy
    tipo: markdown
    destino: Console
    persistido: false
Checklist:
  - "[ ] Nivel de conciencia y sofisticación diagnosticada" 
  - "El titular calibrado a nivel de conciencia" 
  - "[ ] Mecanismo definido, balas y CTA" 
---

# Task: Escrever a Copy

** ID de la lista: ** MKT-COPY-001 **Comandante:** `*write-copy` · **Agente:** Eugene Schwartz (@eugene-schwartz)
**Purpose:** Producir la copia de la campaña anclada en el mensaje, calibrada al nivel de conciencia del mercado.

## Fases de Ejecución
1. **Diagnosis** — nivel de conciencia (Sinware → Más Consciente) y etapa de sofisticación del mercado. "El papi no está escrito, se monta."
2. **Headline** — casados en el nivel de conciencia: Inconsciente → história/curiosidade; La mayoría de los conocimientos → oferta/preço/urgência.
3. **Carta &quot; Mecanismo**: los primeros párrafos y el mecanismo único que explica por qué funciona.
4. **Cuenta** — página de ventas / VSL / copia de anuncio / e-mails como los medios; balas de fascinación; prueba.
5. **Oferta &quot; CTA**: oferta irresistible y clara llamada.

## Formato de salida
```
✍️ COPY — {peça}
Conciencia: {nível}  {estágio}
Headline:  {headline}
Big Idea: {idea central}
Lead:      {abertura}
Mecanismo: ¿por qué funciona?
Corpo:     {texto}
CTA:       {chamada}
```

## Condiciones de veto
- Nunca escriba sin definir el nivel de conciencia del mercado.
- Nunca entrega sin una oferta clara y un CTA.

## Criterios de finalización
- [ ] El titular alineado a la conciencia · [ ] Mecanismo/prova regalos · [ ] oferta clara + CTA
