# Lista de verificación de calidad de crecimiento generado por datos

** ID de lista de verificación:**
**Referenciado por:** tasks/review.md
**Fuente:** Validar el análisis de datos y data-driven crecimiento de los productos para la calidad antes de la entrega al usuario.

[[LLM: INSTRUCCIONES DE INICIALIZACIÓN

Esta lista de verificación valida data-driven producción de crecimiento específicamente.

ENFOQUE DE EJECUCIÓN:
1. Para cada categoría, verifique cada artículo con el entregable.
2. Marcar elementos como [x] Pasa, [ ] Falla, [N/A] No aplicable
3. Los artículos CRÍTICOS bloquean la entrega;  Los artículos non-critical son de asesoramiento.

Los elementos CRÍTICOS están marcados con el sufijo (CRÍTICO).]]

---

## 1. Fuentes de datos &quot; Integridad &quot;

- [ ] Todas las fuentes de datos se citan explícitamente con fechas de recreo (CRITICAL)
- [ ] La metodología de recogida de datos se describe o se hace referencia
- [ ] El tamaño de la muestra es adecuado para las conclusiones extraídas (CRITICAL)
- [ ] Limitaciones de datos y sesgos conocidos se revelan
- [ ] Los datos son relevantes para la pregunta que se está haciendo, no tangencial

## 2. Validez estadística

- [ ] Se aplican métodos estadísticos correctos para el tipo de datos y la pregunta (CRITICAL)
- [ ] La correlación no se presenta como causalidad sin justificación
- [ ] intervalos de confianza o márgenes de error se indican cuando corresponda
- [ ] Se identifican los atípicos y se explica su manejo
- [ ] Las comparaciones utilizan las bases de referencia y los períodos de tiempo apropiados

## 3. Insights Actionable

- [ ] Las visiones son específicas y factibles - no "data es interesante" (CRITICAL)
Cada visión se conecta a una decisión o acción de negocios
Las prioridades son claras: qué visión para actuar primero y por qué
- [ ] Se proporcionan estimaciones de impacto: lo que sucede si actúas vs no actúa
- [ ] Gana rápido vs long-term las obras se distinguen

## 4. Visualización &amp; Presentación

- [ ] Las visualizaciones son claras, etiquetadas y no engañosas (CRITICAL)
- [ ] Tipos de gráfico son apropiados para los datos (sin gráficos de tarta para 15 categorías)
Los ejes comienzan a cero o la desviación está justificada y señalada
- El uso de color es accesible y significativo
- [ ] Los principales secuestradores son destacados, no enterrados en datos

## 5. Metrics &quot; KPIs

- [ ] Las métricas se definen con clara formulas/calculations
- [ ] Se distinguen los indicadores principales de los indicadores de retraso
- [ ] Se proporcionan parámetros o metas para contexto
Las relaciones métricas se mapean (¿cómo afecta X a Y?)
- Las métricas de vanidad están insignias o excluidas

## 6. Recomendaciones &quot; Próximos pasos &quot;

- [ ] Las recomendaciones se basan en los datos, no en supuestos (CRITICAL)
- [ ] A/B se incluyen sugerencias de prueba cuando proceda
- [ ] Plan de vigilancia: qué hacer después de la aplicación de los cambios
- [ ] Se identifican lagunas de datos con recomendaciones de recogida
Se calcula que el plazo para el impacto previsto

---

## PASS/FAIL Criteria

**APROBADO:** Todos los elementos CRÍTICOS [x] y menos de 3 fallas de non-critical .
**REVISIÓN:** Todos los elementos CRÍTICOS [x] pero más de 3 fallas de non-critical .
**FALLO:** Cualquier elemento CRÍTICO sin marcar.
