# Lista de verificación de calidad de resultados de asesores estratégicos

**ID de lista de verificación:** ADVISORY-CL-001
**Referenciado por:** tasks/review.md
**Propósito:** Validar la calidad de los entregables de asesoramiento estratégico antes de entregarlos al usuario.

[[LLM: INSTRUCCIONES DE INICIALIZACIÓN

Esta lista de verificación valida específicamente los resultados del asesoramiento estratégico.

ENFOQUE DE EJECUCIÓN:
1. Para cada categoría, verifique cada artículo con el entregable.
2. Marcar elementos como [x] Pasa, [ ] Falla, [N/A] No aplicable
3. Los artículos CRÍTICOS bloquean la entrega;  Los artículos non-critical son de asesoramiento.

Los elementos CRÍTICOS están marcados con el sufijo (CRÍTICO).]]

---

## 1. Análisis multiperspectiva

- [ ] Se consideran múltiples perspectivas o escenarios, no solo un camino (CRÍTICO)
- [ ] Se representan puntos de vista disidentes, no solo sesgos de confirmación
- [ ] Se exploran los efectos de segundo orden (¿qué sucede después del primer movimiento?)
- [ ] Se hace referencia a precedentes históricos o analogías cuando sea relevante
- [ ] El impacto de las partes interesadas se evalúa en todas las partes afectadas

## 2. Identificación de riesgos

- [ ] Los riesgos clave se identifican y categorizan explícitamente (CRÍTICO)
- [ ] Se estima la probabilidad y el impacto de cada riesgo
- [ ] Se proponen estrategias de mitigación o planes de contingencia
- [ ] El peor de los casos se aborda honestamente, no se minimiza
- [ ] La irreversibilidad de las decisiones se marca cuando corresponde

## 3. Supuestos y evidencia

- [ ] Los supuestos subyacentes a la recomendación se establecen explícitamente (CRÍTICO)
- [ ] La evidencia o los datos respaldan el análisis, no solo la opinión
- [ ] Las lagunas de información se reconocen, no se pasan por alto
- [ ] Se identifican fuentes de incertidumbre
- [ ] Se declara nivel de confianza en la recomendación

## 4. Recomendaciones prácticas

- [ ] Las recomendaciones son específicas y prácticas, no tópicos vagos (CRÍTICO)
: [] Los próximos pasos claros se definen con propietarios y cronogramas
- [ ] Se proporcionan criterios de decisión: ¿cómo sabrá el usuario si esto está funcionando?
- [ ] Se identifican los desencadenantes o hitos de Go/no-go 
- [ ] Se estiman los requisitos de recursos (tiempo, dinero, personas)

## 5. Coherencia estratégica

- [ ] Las recomendaciones se alinean con los objetivos y limitaciones establecidos
- [ ] Las compensaciones se hacen explícitas: ¿a qué estás renunciando?
- [ ] Se distinguen las implicaciones a corto plazo frente a long-term 
- [ ] Se consideran dinámicas competitivas
- [ ] El asesoramiento se calibra según la etapa y los recursos del usuario.

## 6. Calidad de la comunicación

- [ ] El análisis está estructurado de forma lógica y fácil de seguir
- [ ] El resumen ejecutivo captura la esencia en 3-5 oraciones
- [ ] La jerga está minimizada o definida
- [ ] La conclusión es definitiva, no "depende" sin resolución

---

## PASS/FAIL Criteria

**APROBADO:** Todos los elementos CRÍTICOS [x] y menos de 3 fallas de non-critical .
**REVISIÓN:** Todos los elementos CRÍTICOS [x] pero más de 3 fallas de non-critical .
**FALLO:** Cualquier elemento CRÍTICO sin marcar.
