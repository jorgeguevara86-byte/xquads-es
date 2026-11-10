# Marketing Squad  ⁇ 

**El mejor agente de cada disciplina de marketing, orquestado en una línea de montaje.**

Este equipo reúne a los 4 expertos más completos de los Xquads, bajo un Jefe de Marketing, para llevar a cabo una campaña de vanguardia: **mensagem → copiar → creativo → distribución**.

---

*El equipo*

. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
|------|--------|-----------|--------|-----------|
 *novo* .Diagnoses, rutas, secuencia de campaña y revisa la calidad entre los handoffs.
 brand-squad  one-liner, claridad de suministro, embudo esqueleto
 copy-squad 
 design-squad 
 traffic-masters 

> Por qué estos cuatro?** Miller es la marca más *acionável* (transforma la posición en activos). Schwartz es copia *fundacional* (los niveles de conciencia son el eje de toda la redacción). Generador Visual es el diseño que *produz real* marketing creativo. Sobral es tráfico *full-funnel en español*. Juntos forman una línea de montaje coherente.

---

*Empiezo rápido*

Activar el orquestador y dejarle recorrer:

```
@marketing-squad:marketing-chief
*help
```

O ir directo a un experto:

```
@marketing-squad:donald-miller      # mensagem/posicionamento
@marketing-squad:eugene-schwartz    # copy
@marketing-squad:visual-generator   # Creative visual
@marketing-squad:pedro-sobral       # Tráfico pagado
```

---

# Corrientes de trabajo predefinidas

El quad tiene flujos de trabajo que encadenan las 4 disciplinas automáticamente, con puerta de calidad entre cada fase:

Silencio Comando Silencioso de trabajo Silencioso O que faz Silencio
|---------|----------|-----------|
| `*campaign`  `diagnose → mensagem (Miller) → copy (Schwartz) → criativo (Visual) → tráfego (Sobral) → review`. La línea completa de montaje. .
| `*launch` . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

Cada fase tiene una `checkpoint` (gate/veto): La mala entrada de arriba está prohibida antes de perder dinero de abajo.

---

# How the Chief route

```
Demanda
  . . . . Mensaje indefinido? → Donald Miller (comienza por la columna)
  Entendido.headline/VSL/ads) → Eugene Schwartz
  ├─ Criativo/visual→ Generador visual
  ├─ Tráfego/escala? → Pedro Sobral
  └─ Campanha/lançamento?      → *campaign / *launch (toda secuela)
```

---

## Estrutura

```
marketing-squad/
├── squad.yaml                  # Component manifesto
├── config/config.yaml          # Tiers, agentes, handoffs, roteamento
├── data/routing-catalog.yaml   # map demand → specialist
- Agentes/ marketing-chief + os 4 especialistas
- tareas/ build-message, write-copy, create-creatives, build-traffic, examen
├── workflows/                  # wf-full-campaign, wf-launch
└── checklists/output-quality.md
```

---

# El comando del jefe


|---------|-----------|
| `*help` 
| `*diagnose` 
| `*campaign` 
| `*launch` 
| `*assign {agente}` 
| `*review` 
| `*roster` Silencio Mostra o tiempo Silencio

---

*Marketing Squad v1.0.0 · Xquads · Línea de montaje: mensaje → copy → creativo → traffic*
