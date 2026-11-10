---
task: diagnose()
responsavel: "@marketing-chief"
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
  - "[ ] Objetivo y disciplina(s) identificados" 
  - "[ ] nivel de conocimiento del mercado de valor (Schwartz)" 
  - "[ ] Especialista(s) roteado(s) com o brief" 
---

# Task: Diagnosticar Demanda de Marketing

** ID de la lista: ** MKT-CHIEF-001
**Version:** 1.0.0
**Command:** `*diagnose`
**Orquestador:** Jefe de Marketing (Mira)
**Purpose:**Ordenar cualquier demanda de marketing, identificar la disciplina(s) y la ruta al experto adecuado, o disparar un flujo de trabajo cuando sea una campaña completa.

---

## Inputs

Silencioso campo Silencio Tipo Silencio Fuente Silencio Requerido
|-------|------|--------|----------|
Silencio Silencio Silencio Silencio Silencio Silencio Silencio Silencio

## Fases de Ejecución

1. **Parse** — extracto de la demanda: objetivo, oferta, público, medios de comunicación y plazo.
2. ** Etapa**: a mensagem/posicionamento Si NO, empieza con Donald Miller.
3. **Conciencia** — evalúa el nivel de conciencia del mercado (Sinware → Most Aware), que guía la copia y la creatividad.
4. **Rotear** — cruzar com `discipline_routing` / `objective_routing`:
   - Mensagem/funil → `donald-miller`
   - Copia (cabeza, página de ventas, VSL, anuncios, e-mail) → `eugene-schwartz`
   - Criativo/visual → `visual-generator`
   - Tráfego/lançamento → `pedro-sobral`
   - Campaña completa → disparar `*campaign`; lanzamiento → `*launch`
5. **Briefar** — entregar al especialista: público, nivel de conciencia, oferta, métrica primaria, restricciones.

## Formato de salida

```


Objetivo:            {objetivo}
Disciplina(s): {brand ¦ copia Silencio visual Silencio imprevisto traffic ¦ campanha}
Nivel de conciencia:{Unware → La mayoría de los conocimientos}
Especialista(s): @{agent(s)}
Metrícula primaria:    {métrica}


```

## Condiciones de veto

- Nunca se copian las rutas antes de establecer el nivel de conciencia del mercado.
- Nunca saltes el mensaje cuando el posicionamiento sigue confundido.

## Criterios de finalización

- [ ] Disciplina(s) y experto(s) identificados con alta confianza
- Nivel de conciencia evaluado
- [ ] Breve  encargo ao especialista (ou workflow disparado)
