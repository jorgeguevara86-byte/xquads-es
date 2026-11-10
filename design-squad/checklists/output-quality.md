# Design Systems/UX Lista de verificación de calidad de salida

** ID de lista de verificación: ** DESIGN-CL-001
**Referenciado por:** tasks/review.md
**Fuente:** Sistemas de diseño validados y entregables UX para calidad antes de la entrega al usuario.

[[LLM: INSTRUCCIONES DE INICIALIZACIÓN

Esta lista valida los sistemas de diseño y la salida UX específicamente.

ENFOQUE DE EJECUCIÓN:
1. Para cada categoría, verifique cada artículo con el entregable.
2. Marcar elementos como [x] Pasa, [ ] Falla, [N/A] No aplicable
3. Los artículos CRÍTICOS bloquean la entrega;  Los artículos non-critical son de asesoramiento.

Los elementos CRÍTICOS están marcados con el sufijo (CRÍTICO).]]

---

## 1. Accesibilidad (WCAG 2.1 AA)

- [ ] El contraste de color cumple con el mínimo 4.5:1 para el texto normal, 3:1 para el texto grande (CRITICAL)
- [ ] Los elementos interactivos tienen estados de enfoque visibles (CRITICAL)
Los objetivos táctiles son mínimos 44x44px en móvil
- [ ] El contenido es legible sin color como el único indicador
- [ ] Consideraciones de lectores de pantalla documentadas (marcas de la agenda, roles, hitos)
- [ ] La orden de navegación del teclado es lógica

## 2. Consistencia del sistema de diseño

- [ ] Las fichas de diseño se utilizan correctamente - no hay valores codificados por colores, espaciamiento, tipografía (CRITICAL)
- [ ] Componente sigue los patrones de sistema de diseño existentes y las convenciones de nominación (CRITICAL)
- [ ] El espacio utiliza la escala definida (4px/8px o rejilla system-specific)
- Usos de la tipografía system-defined escala y pesos tipo
La iconografía es del icono aprobado con un tamaño consistente
- [ ] Las variaciones estatales se definen: por defecto, buceador, activo, deshabilitado, error, carga

## 3. Diseño responsable

- [ ] El diseño se adapta correctamente a los puntos de ruptura: móvil, tableta, escritorio (CRITICAL)
- [ ] La jerarquía de contenidos se mantiene en tamaños de pantalla
Imágenes y escala de medios proporcionalmente
- [ ] La navegación se adapta apropiadamente para el puntero táctil vs
- No hay desplazamiento horizontal en anchos estándar de mirador

## 4. Interacción de flujo de UX

- [ ] El flujo de usuario es lógico - pasos mínimos para completar la tarea
- [ ] Los estados de error y los estados vacíos están diseñados
- [ ] Se especifican estados de carga y pantallas esqueleto
- [ ] La retroalimentación es inmediata para las acciones del usuario (micro-interactions)
- [ ] Undo/recovery existen caminos para acciones destructivas
- [ ] Casos de bordes tratados: texto largo, datos faltantes, first-time uso

## 5. Calidad visual

La jerarquía visual está clara, el ojo sabe a dónde ir primero.
- [ ] La alineación y el espaciado son consistentes, no "eyeballed"
El uso de color es compatible con el estado de ánimo y la marca
El espacio blanco se utiliza intencionalmente, no como sobra.
- [ ] La composición general se siente equilibrada y profesional

## 6. Documentación &quot; Handoff &quot;

- [ ] Componente API/props se documentan si procede
- [ ] Directrices de uso: cuándo utilizar, cuando NO utilizar
Las decisiones de diseño se anotan con racionalidad
- [ ] Los activos son export-ready o espectro para el desarrollo

---

## PASS/FAIL Criteria

**APROBADO:** Todos los elementos CRÍTICOS [x] y menos de 3 fallas de non-critical .
**REVISIÓN:** Todos los elementos CRÍTICOS [x] pero más de 3 fallas de non-critical .
**FALLO:** Cualquier elemento CRÍTICO sin marcar.
