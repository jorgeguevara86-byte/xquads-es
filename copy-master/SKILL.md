---
name: copy-master
description: >-
  Edición Squad Version 2.0 con 33 agentes: los más expertos en escritores clásicos en persuasión,
  negociación, lanzamiento y copia de SaaS (Robert Cialdini, Chris Voss, Oren Klaff, Joanna Wiebe,
  Sabri Suby, Alex Hormozi). Uso cuando la demanda de copia requiere mayor profundidad en
  psicología de persuasión, negociación, cubierta de lanzamiento corto, script webinario o
  copygger
license: MIT
metadata:
  squad: "Copiar Maestro"
  version: "2.0.0"
  agents: "33"
  author: "Xquads by Synkra"
---

# Copiar Maestro

**Dominio:** Elite copywriting 2.0 — respuesta directa, correo electrónico, embudos, VSLs, cartas de venta, ofertas, copia de marca, psicología de persuasión, negociación, lanzamiento, conversión de SaaS

## Cómo activar

Todas las rutas siguientes son **relativos la raíz de esta habilidad**. Lea archivos directamente desde el disco con la herramienta de lectura de su entorno. No hay dependencia del comando de barra diagonal, complemento ni de ningún cliente específico.

1. Lea `agents/copy-master-chief.md` Y la definición autocontenida de la cabeza de la
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

** Jefe del equipo** `agents/copy-master-chief.md`

**Especialistas (32)**

- `agents/alex-hormozi.md`
- `agents/andre-chaperon.md`
- `agents/ben-settle.md`
- `agents/blair-warren.md`
- `agents/chris-voss.md`
- `agents/claude-hopkins.md`
- `agents/clayton-makepeace.md`
- `agents/dan-kennedy.md`
- `agents/dan-koe.md`
- `agents/david-deutsch.md`
- `agents/david-ogilvy.md`
- `agents/eugene-schwartz.md`
- `agents/evaldo-albuquerque.md`
- `agents/frank-kern.md`
- `agents/gary-bencivenga.md`
- `agents/gary-halbert.md`
- `agents/jim-rutz.md`
- `agents/joanna-wiebe.md`
- `agents/joe-sugarman.md`
- `agents/john-caples.md`
- `agents/john-carlton.md`
- `agents/jon-benson.md`
- `agents/oren-klaff.md`
- `agents/parris-lampropoulos.md`
- `agents/robert-cialdini.md`
- `agents/robert-collier.md`
- `agents/rosser-reeves.md`
- `agents/russell-brunson.md`
- `agents/ry-schwartz.md`
- `agents/sabri-suby.md`
- `agents/stefan-georgi.md`
- `agents/todd-brown.md`

## Tasks (15)

- `tasks/analyze-copy.md`
- `tasks/create-funnel-copy.md`
- `tasks/create-offer.md`
- `tasks/critique-copy.md`
- `tasks/diagnose.md`
- `tasks/review.md`
- `tasks/write-ad-copy.md`
- `tasks/write-bullets.md`
- `tasks/write-email-sequence.md`
- `tasks/write-headline.md`
- `tasks/write-landing-page.md`
- `tasks/write-pitch-deck.md`
- `tasks/write-sales-letter.md`
- `tasks/write-vsl-script.md`
- `tasks/write-webinar-script.md`

## Workflows (4)

Secuencias multi-agente ya vinculadas. Siga las fases en el orden indicado.

- `workflows/wf-copy-review-cycle.yaml`
- `workflows/wf-full-copy-project.yaml`
- `workflows/wf-launch-sequence.yaml`
- `workflows/wf-vsl-production.yaml`

## Checklists

Rote antes de la entrega. No declare la entrega lista con un artículo abierto.

- `checklists/output-quality.md`

## Datos de referencia

- `data/books-resources.yaml`
- `data/champion-swipe-files.yaml`
- `data/copy-frameworks.yaml`
- `data/persuasion-psychology.yaml`
- `data/routing-catalog.yaml`

## Convencoes

: los comandos del agente utilizan el prefijo `*` (`*help`, `*exit`y los declarados en la persona).
- Respuesta en español, a menos que se solicite explícitamente lo contrario.
- El jefe de escuadrón no realiza el trabajo del especialista: diagnostica y delega.
: un agente a la vez. El cambio de agente pone fin a la persona anterior.

---

*Parte de [Xquads](https://github.com/ohmyjahh/xquads-squads) — Habilidades de agente estándar abiertas.*
