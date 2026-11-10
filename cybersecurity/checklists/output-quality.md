Lista de verificación de calidad de salida de seguridad

** ID de lista de verificación:**
**Referenciado por:** tasks/review.md
**Purpose:** Validar los entregables de seguridad cibernética para la calidad antes de la entrega al usuario.

[[LLM: INSTRUCCIONES DE INICIALIZACIÓN

Esta lista de verificación valida la salida de ciberseguridad específicamente.

ENFOQUE DE EJECUCIÓN:
1. Para cada categoría, verifique cada artículo con el entregable.
2. Marcar elementos como [x] Pasa, [ ] Falla, [N/A] No aplicable
3. Los artículos CRÍTICOS bloquean la entrega;  Los artículos non-critical son de asesoramiento.

Los elementos CRÍTICOS están marcados con el sufijo (CRÍTICO).]]

---

## 1. Autorización &quot; Ámbito &quot;

- [ ] Los límites de autorización son verificados y respetados (CRITICAL)
- [ ] Se declara explícitamente el alcance de la evaluación (CRITICAL)
- Fuera.of-scope los artículos se documentan y no se prueban
- [ ] Se reconocen las limitaciones legales y de cumplimiento
- [ ] Las reglas de compromiso de la participación (RoE) siguieron

## 2. Findings Classification

- [ ] Cada hallazgo tiene una calificación de gravedad: Crítico, Alto, Medio, Bajo, Informativo (CRITICAL)
- [ ] Las calificaciones de la Severidad usan CVSS o puntuación estandarizada equivalente
- [ ] MITRE ATT plagaCK IDs de técnica mapeados cuando corresponda
- [ ] CWE/CVE referencias incluidas para vulnerabilidades conocidas
- Se identifican y filtran falsos positivos

## 3. Evidencia &quot; Reproducibilidad &quot;

- Cada hallazgo incluye evidencia: registros, capturas de pantalla, pasos de PoC (CRITICAL)
- [ ] Las conclusiones son reproducibles por un tercero después de la documentación
- [ ] Los vectores de ataque son claramente descritos
- [ ] El impacto se indica en términos de negocio, no sólo términos técnicos
- Afectado assets/components se identifican específicamente

## 4. Remediation

- [ ] Cada hallazgo tiene una recomendación de remediación factible (CRITICAL)
La rehabilitación se prioriza por la gravedad y la explotación
- [ ] Mitigaciones a corto plazo distinguidas de long-term soluciones
- [ ] Los pasos de la rehabilitación son específicos, no genéricos ("parar sus sistemas")
Controles compensatorios sugeridos donde no es posible la solución inmediata

## 5. Reporting &quot; Confidentiality

- [ ] No hay datos confidenciales expuestos en el informe (creenciales, PII, IP interna en texto claro) (CRITICAL)
- [ ] El resumen ejecutivo está presente y comprensible non-technical interesados
- [ ] El detalle técnico es suficiente para que el equipo de ingeniería actúe
- [ ] El informe sigue una estructura marco reconocida (OWASP, NIST, PTES)
- [ ] Classification/confidentiality marcado aplicado

## 6. Completeness

- [Todos] in-scope assets/surfaces se prorratearon
- [ ] La metodología está documentada
- [ ] Herramientas y versiones utilizadas se enumeran
- [ ] Limitaciones y cavernas se revelan
- [ ] Recomendaciones para futuras evaluaciones incluidas

---

## PASS/FAIL Criteria

**APROBADO:** Todos los elementos CRÍTICOS [x] y menos de 3 fallas de non-critical .
**REVISIÓN:** Todos los elementos CRÍTICOS [x] pero más de 3 fallas de non-critical .
**FALLO:** Cualquier elemento CRÍTICO sin marcar.
