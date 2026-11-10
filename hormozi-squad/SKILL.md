---
name: hormozi-squad
description: >-
  16 agente Squad implementando marcos Alex Hormozi (100M Ofertas, 100M Líderes). Uso para oferta
  irresistible arquitectura, precios, generación de plomo, cierre de venta, ganchos, retención,
  modelos de negocio, planificación de lanzamiento, diseño de talleres y auditoría de negocios
  completa. Trucos: oferta, gran oferta de slam, precios, generación de plomo, LTV, CAC, escala,
  cierre, retención, modelo de negocios, Hormozi.
license: MIT
metadata:
  squad: "Hormozi Squad"
  version: "1.0.0"
  agents: "16"
  author: "Xquads by Synkra"
---

# Hormozi Squad

**Dominio:** Escalada de negocios usando los marcos de Alex Hormozi — ofertas, leads, precios, ventas, retención y crecimiento

## Cómo activar

Todas las rutas siguientes son **relativos la raíz de esta habilidad**. Lea archivos directamente desde el disco con la herramienta de lectura de su entorno. No hay dependencia del comando de barra diagonal, complemento ni de ningún cliente específico.

1. Lea `agents/hormozi-chief.md` Y la definición autocontenida de la cabeza de la
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

** Jefe del equipo** `agents/hormozi-chief.md`

**Especialistas (15)**

- `agents/hormozi-ads.md`
- `agents/hormozi-advisor.md`
- `agents/hormozi-audit.md`
- `agents/hormozi-closer.md`
- `agents/hormozi-content.md`
- `agents/hormozi-copy.md`
- `agents/hormozi-hooks.md`
- `agents/hormozi-launch.md`
- `agents/hormozi-leads.md`
- `agents/hormozi-models.md`
- `agents/hormozi-offers.md`
- `agents/hormozi-pricing.md`
- `agents/hormozi-retention.md`
- `agents/hormozi-scale.md`
- `agents/hormozi-workshop.md`

## Tasks (10)

- `tasks/audit-business.md`
- `tasks/close-sale.md`
- `tasks/create-hooks.md`
- `tasks/create-offer.md`
- `tasks/design-workshop.md`
- `tasks/diagnose.md`
- `tasks/generate-leads.md`
- `tasks/plan-launch.md`
- `tasks/review.md`
- `tasks/set-pricing.md`

## Workflows (2)

Secuencias multi-agente ya vinculadas. Siga las fases en el orden indicado.

- `workflows/wf-business-turnaround.yaml`
- `workflows/wf-offer-creation.yaml`

## Checklists

Rote antes de la entrega. No declare la entrega lista con un artículo abierto.

- `checklists/output-quality.md`

## Datos de referencia

- `data/hormozi-frameworks.yaml`
- `data/routing-catalog.yaml`

## Convencoes

: los comandos del agente utilizan el prefijo `*` (`*help`, `*exit`y los declarados en la persona).
- Respuesta en español, a menos que se solicite explícitamente lo contrario.
- El jefe de escuadrón no realiza el trabajo del especialista: diagnostica y delega.
: un agente a la vez. El cambio de agente pone fin a la persona anterior.

---

*Parte de [Xquads](https://github.com/ohmyjahh/xquads-squads) — Habilidades de agente estándar abiertas.*
