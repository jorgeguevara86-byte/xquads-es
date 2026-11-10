# Lista de verificación: Calidad de la ruta — Jefe de Xquads

Puerta de calidad meta-orquestradorA diferencia de los otros equipos, aquí **não si evalúas entregable** avalia-se o **roteamento**. Rotar antes de considerar un enrutamiento completado.

---

## 1. Diagnóstico

- [ ] La demanda real fue extraída (que necesita EXIST al final), no sólo la etiqueta que el usuario utilizó
- [ ] El dominio vino de `routing-catalog.yaml` — no inventado equipo
- [ ] Se calculó la confianza y **declarada en voz alta** con motivo de 1 línea
- [ ] Si hubo un vínculo entre los dominios, el `tie_breakers` se aplicó
Si la confianza se ha hecho.*exatamente a** cuestión de la inequívoca
- [ ] Caso especial comprobado: código → `/raxos`; sin equipo → `/squad`

## 2. Briefing de Handoff

- [ ] Se ajusta en 500 fichas
- [ ] `Contexto conhecido` tiene **só** lo que el usuario dijo
- Toda inferencia está dentro. `Premissas assumidas`, marcado `[ASSUMIDO]`
- [ ] `Fora de escopo` (requiere cuando la demanda es ambigua)
- [ ] `Objetivo final` describe un artefacto concreto, no una intención vaga
- O*especialista final no fue pre-elegido** — esa decisión es del jefe del equipo

#3. Activación

- El jefe del Escuadrón era...*efetivamente activado**, no sólo recomendado
- El comando de activación coincide con el del catálogo.
- Sólo...*um** Cabeza activada a la vez
El Jefe de Xquads dejó de conducir después de la transferencia.
- No hay comentarios sobre el trabajo del jefe del equipo

#4. Cadena multiescuadrada (cuando sea aplicable)

- [ ] La cadena entera fue anunciada al usuario antes de que empezara
La cárcel vino de `multi_squad_chains` - no inventado
- [ ] La cadena es realmente necesaria (usuario pidió resultado de negocio, no un entregable aislado)
- [ ] Enlaces ejecutados ♪*em secuencia**, nunca en paralelo
- [ ] Salida do elo N virou `Contexto conhecido` do elo N+1
- [ ] Máximo 5 enlaces respetados
La cadena era interrumpida, el usuario podía detener

##5. Limits (violación = falla de la puerta)

No se ha hecho ningún trabajo de ejecución ni se ha borrado ni "sólo por el bien"
- No hay línea de código escrita
- [ ] No se produce copia, diseño, análisis o estrategia
Más de una cuestión de inequívoca*não** Se hizo
- [ ] Respuesta completa en inglés (es)

---

## Veredito


|---|---|

**CONCERNS** . . Correcta de enrutamiento, pero incompleta información o confianza no declarada.
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

** El FAIL en cualquier artículo de la sección 5 es automático** — no importa lo bueno que fuera el resto.
