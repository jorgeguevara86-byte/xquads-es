# Task: Diagnosis (Top Triage)

**Agente:** xquads-chief
**Comando:** `*diagnose`
**Atención:** bloque de diagnóstico con equipo recomendado (NO activo)
** Duración:**

---

## Objetivo

Transformar una demanda en lenguaje natural en la identificación precisa de **qual Squad resuelve**. Esta tarea NO activa a nadie — solo diagnostica. Para diagnosticar y activar, usar `route.md`.

---

## Passo 1 — Extrair a demanda real

Lea la solicitud y la respuesta del usuario internamente:

Silencio Pergunta Silencioso Por quê viv
|---|---|
¿Qué necesita existir al final? El artefacto concreto revela la equipo
. . es esto un "cómo hago X" o un "debo hacer X"? . . "Devo" → advisory-board / c-level |
¿Hay algo o es desde cero? Auditoría vs creando cambios en la tarea, no en la equipo?
? Ha roto métrica involucrado? Metric → data-squad entra en la cadena

** Anti-standard:** no acepte la etiqueta que el usuario dio. "Necesito una copia para mi aterrizaje" puede ser un problema de oferta (hormozi), no texto.

---

Paso 2 - Ordenar el dominio

Carregue `data/routing-catalog.yaml` e faça match de keywords contra a demanda.

- El partido en es tiene un peso mayor que EN (el usuario habla español).
- Dime cuántos dominios coinciden.
  - **1 dominio** → alta confianza de salida
  - **2+ dominios** → aplicar `tie_breakers`
  - **0 dominios** → check `external_targets`, entonces considerar `/squad`

---

# Paso 3 - Calcular confianza


|---|---|




. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .



Base: 40. Algunos os ajustes. Trave entre 0 e 100.

**Faixas:**
- **. 80 (ALTA)** → ruta directa
- **50-79 (MEDIA)** → router declarando la suposición supuesta
- ** Se entiende por una cuestión de inequívoca, tomada de `tie_breakers`

---

Paso 4 - Detectando la cárcel multi-squad

Compare la demanda con `multi_squad_chains`Es la cárcel cuando:

- El usuario pidió un **resultado negocio** y no un entregable (por ejemplo, "aplauso mi curso")
- El artefacto final depende de 2+ dominios en secuencia
- Hay una cadena en el catálogo con trigger_keywords Tocando

. . . **No inventes cadena.** Si el usuario pidió un titular, quiere un titular — no una versión completa. Cadena sólo cuando la solicitud de alcance realmente requiere.

Si el alcance es la campaña pero pequeña, prefiere **marketing-squad** (ya integrada) a la cadena completa.

---

## Paso 5 — Casos especiales (ver la lista de casos anteriores)


|---|---|---|
 escrever/alterar **código** | `/raxos` SDC Obligatorio. Nunca implemento. .
 `claude-code-mastery` 
 `/squad` 
 `route.md`  re-diagnostique lo que ya se ha decidido

---

Paso 6 - Emitir el diagnóstico

```
🎯 Diagnóstico
Demanda: {1 frase — lo que necesita ser al final}
Dominio: {dominio de catálogo}
Squad:      {squad} → {chefe}
Confianza:  {n}% — {motivación en 1 línea}
Cadena: {no
Activación: habilidad `{squad}` → `agents/{chefe}.md`
```

Si la confianza se hizo 50, ponlo en su lugar **uma** Pregunta:

```
Necesito un detalle para golpear al equipo:
{Pregunta de tie_breaker}

a) {opción A} → {seudible A}
b) {Opción B} → {Squad B}
```

---

## Checkpoint


|---|---|
*ou** Cuestión única emitida

. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
