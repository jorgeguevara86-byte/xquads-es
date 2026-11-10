---
name: copy-squad
description: >-
  Escuadrón de 23 legendarios redactores de copia (Gary Halbert, Eugene Schwartz, David Ogilvy,
  Dan Kennedy, Joe Sugarman y otros) con un jefe que ruta por combinación de medios, nivel de
  conciencia de mercado y meta. Uso para escribir o revisar titular, carta de ventas, script VSL,
  secuencia de correo electrónico, copia de la annuncia, página de aterrizaje, balas, copia de
  embudo y ofrecer arquitectura; también para la crítica y el diagnóstico de la página de copia de
  la página de copia de publicidad.
license: MIT
metadata:
  squad: "Copiado Squad"
  version: "1.0.0"
  agents: "23"
  author: "Xquads by Synkra"
---

# Copiado Squad

**Dominio:** Copiado de élite — respuesta directa, correo electrónico, embudos, VSLs, cartas de venta, ofertas y copia de marca

## Cómo activar

Todas las rutas siguientes son **relativos la raíz de esta habilidad**. Lea archivos directamente desde el disco con la herramienta de lectura de su entorno. No hay dependencia del comando de barra diagonal, complemento ni de ningún cliente específico.

1. Lea `agents/copy-chief.md` Y la definición autocontenida de la cabeza de la
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

** Jefe del equipo** `agents/copy-chief.md`

**Especialistas (22)**

- `agents/andre-chaperon.md`
- `agents/ben-settle.md`
- `agents/claude-hopkins.md`
- `agents/clayton-makepeace.md`
- `agents/dan-kennedy.md`
- `agents/dan-koe.md`
- `agents/david-deutsch.md`
- `agents/david-ogilvy.md`
- `agents/eugene-schwartz.md`
- `agents/frank-kern.md`
- `agents/gary-bencivenga.md`
- `agents/gary-halbert.md`
- `agents/jim-rutz.md`
- `agents/joe-sugarman.md`
- `agents/john-carlton.md`
- `agents/jon-benson.md`
- `agents/parris-lampropoulos.md`
- `agents/robert-collier.md`
- `agents/russell-brunson.md`
- `agents/ry-schwartz.md`
- `agents/stefan-georgi.md`
- `agents/todd-brown.md`

## Tasks (13)

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
- `tasks/write-sales-letter.md`
- `tasks/write-vsl-script.md`

## Workflows (2)

Secuencias multi-agente ya vinculadas. Siga las fases en el orden indicado.

- `workflows/wf-copy-review-cycle.yaml`
- `workflows/wf-full-copy-project.yaml`

## Checklists

Rote antes de la entrega. No declare la entrega lista con un artículo abierto.

- `checklists/output-quality.md`

## Datos de referencia

- `data/copy-frameworks.yaml`
- `data/routing-catalog.yaml`

## Convencoes

: los comandos del agente utilizan el prefijo `*` (`*help`, `*exit`y los declarados en la persona).
- Respuesta en español, a menos que se solicite explícitamente lo contrario.
- El jefe de escuadrón no realiza el trabajo del especialista: diagnostica y delega.
: un agente a la vez. El cambio de agente pone fin a la persona anterior.

---

*Parte de [Xquads](https://github.com/ohmyjahh/xquads-squads) — Habilidades de agente estándar abiertas.*
