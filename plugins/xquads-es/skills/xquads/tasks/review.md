# Task: Review (Revisión de la carga y la validación de la entrega)

**Agente:** xquads-chief
**Comando:** `*review`
**Resultado:**Veredicto de recaída + siguiente paso (cerrar o cadena)
** Duración:**

---

## Objetivo

Cuando el Escuadrón devuelve la entrega, el Jefe de Xquads valida **uma Lo único**: el enrutamiento era correcto y la demanda original fue contestada.*não** evalúa la calidad técnica de entregable - esto es del jefe de la brigada, que tiene la `output-quality.md` El suyo.

---

Paso 1 - Comproba contra la demanda original


|---|---|
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
 `Fora de escopo` ¿Se declaró en la sesión informativa?
 `[ASSUMIDO]` - ¿Lo confirmaron?
¿Se ha perdido alguna parte de la solicitud original sin justificación?

---

Paso 2 - Veredicto de rutina


|---|---|---|
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

---

## Paso 3 — Registro de aprendizaje (sólo en ROOT ERROR)

Error de ruta es información. Registro en una línea lo que engañó el diagnóstico:

```
[ROOT] "{demanda}" → routed by {wrong square}, correcto era {squad right}.
Signo engañoso: {palabra o premisa que indujo error}.
```

Usa esto para ajustar el `tie_breakers` Do `routing-catalog.yaml` No reescribir el catálogo por un caso aislado.

---

Paso 4 - Cerca o cadena

- **Cadeia terminó** → entregó el consolidado y cerrado. No hay resumen ceremonial.
- **Hay un enlace cercano** → montar la nueva sesión informativa con la salida actual como `Contexto conhecido` Y activa al próximo jefe.
- ** El usuario quiere detenerse** → parar. No forzar el resto de la cadena.

---

## Checkpoint


|---|---|



