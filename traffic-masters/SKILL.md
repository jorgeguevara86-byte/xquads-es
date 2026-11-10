---
name: traffic-masters
description: >-
  Escuadrón de 16 expertos en tráfico pagado (Pedro Sobral, Kasim Aslam, Molly Pittman, Depesh
  Mandalia, Ralph Burns, Tom Breeze, Nicholas Kusmich) que cubre Meta Ads, Google Ads, YouTube
  Ads, compras de medios, análisis creativos, escala y seguimiento. Uso para montar estrategia de
  campaña pagada, cuenta de publicidad de auditoría, crear creativos, gestionar orcamento, TriAS
  seguimiento de tráfico de campaña y PC
license: MIT
metadata:
  squad: "Maestros de Tráfico"
  version: "1.0.0"
  agents: "16"
  author: "Xquads by Synkra"
---

# Maestros de Tráfico

**Dominio:** Adquisición de tráfico de pago en todas las principales plataformas: compra de medios, creativo, analítico y escalado

## Cómo activar

Todas las rutas siguientes son **relativos la raíz de esta habilidad**. Lea archivos directamente desde el disco con la herramienta de lectura de su entorno. No hay dependencia del comando de barra diagonal, complemento ni de ningún cliente específico.

1. Lea `agents/traffic-chief.md` Y la definición autocontenida de la cabeza de la
   : personalidad, principios, lógica de enrutamiento y límites. Adoptala.
2. Carregue `data/routing-catalog.yaml` como contexto de roteamento. Nao exiba o conteudo,
   simplemente absorberlo.
3. Salude con el `greeting` de la persona y espere la demanda.
4. Al dirigirse a un especialista, lea `agents/<especialista>.md` y asuma
   esa persona, manteniendo el informe que preparó el jefe.
5. Permanece en el equipo hasta recibir `*exit`.

## Ejecutando una tarea

Las tareas en `tasks/` son scripts ejecutables con entradas, pasos y formato de salida definidos. Lea el archivo completo antes de comenzar y siga los pasos en orden. Las tareas marcadas con `elicit: true` requieren una respuesta del usuario en cada punto de obtención; no asuma respuestas ni se salte pasos.

## Agentes

** Jefe del equipo** `agents/traffic-chief.md`

**Especialistas (15)**

- `agents/ad-midas.md`
- `agents/ads-analyst.md`
- `agents/creative-analyst.md`
- `agents/depesh-mandalia.md`
- `agents/fiscal.md`
- `agents/kasim-aslam.md`
- `agents/media-buyer.md`
- `agents/molly-pittman.md`
- `agents/nicholas-kusmich.md`
- `agents/pedro-sobral.md`
- `agents/performance-analyst.md`
- `agents/pixel-specialist.md`
- `agents/ralph-burns.md`
- `agents/scale-optimizer.md`
- `agents/tom-breeze.md`

## Tasks (9)

- `tasks/analyze-performance.md`
- `tasks/audit-ad-account.md`
- `tasks/create-ad-creative.md`
- `tasks/create-ad-strategy.md`
- `tasks/diagnose.md`
- `tasks/manage-budget.md`
- `tasks/review.md`
- `tasks/scale-campaign.md`
- `tasks/setup-tracking.md`

## Workflows (2)

Secuencias multi-agente ya vinculadas. Siga las fases en el orden indicado.

- `workflows/wf-account-audit.yaml`
- `workflows/wf-campaign-launch.yaml`

## Checklists

Rote antes de la entrega. No declare la entrega lista con un artículo abierto.

- `checklists/output-quality.md`

## Datos de referencia

- `data/platform-benchmarks.yaml`
- `data/routing-catalog.yaml`

## Convencoes

: los comandos del agente utilizan el prefijo `*` (`*help`, `*exit`y los declarados en la persona).
- Respuesta en español, a menos que se solicite explícitamente lo contrario.
- El jefe de escuadrón no realiza el trabajo del especialista: diagnostica y delega.
: un agente a la vez. El cambio de agente pone fin a la persona anterior.

---

*Parte de [Xquads](https://github.com/ohmyjahh/xquads-squads) — Habilidades de agente estándar abiertas.*
