---
task: planLaunch()
responsavel: "@hormozi-launch"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: product
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: offer
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: launchPlan
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Modelo de lanzamiento seleccionado con racional" 
  - "[ ] Línea de tiempo con todas las fases" 
  - "[ ] Modelo de ingresos calculado con escenarios" 
---

# Task: Plan Launch

** ID de usuario: **HORMOZI-006
**Version:** 1.0.0
**Command:** `*plan-launch`
* Agente*hormozi-launch)
**Purpose:** Diseñar una estrategia de lanzamiento de productos que maximice los ingresos en un plazo comprimido.

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
Silencioso producto Silencioso cadena Silencioso de usuario inducido por Silencio
Silencio oferta Silencioso objeto Silencioso insolente Silencio Silencio Oferta completa (precio, bonos, garantía) Silencio
| audience_size Silencio número Silencio invocar usuario sí Silencio audiencia total accesible (lista de correo, seguidores, etc.) Silencio
| launch_type TEN enum TENIDO Usuario prompt TEN No TENENCIAS, internas, colaboraciones, pagadas — defaults to internal TEN
Silencioso tiempoline Silencio cadena Silencio Usuario prompt Silencio No ← Fecha de lanzamiento deseada o ventana Silencio
Silencio presupuesto Silencio número Silencio Usuario prompt Silencio No Silencio Presupuesto de lanzamiento disponible Silencio

---

## Preconditions

- Oferta totalmente diseñada (idealmente a través de create-offer.md)
- Existe audiencia para lanzarse a (lista, siguiente, comunidad o presupuesto ad)
- Producto listo o estará listo para la fecha de lanzamiento

---

## Fases de Ejecución

### Fase 1: Lanzamiento de la Arquitectura
1. Seleccione el modelo de lanzamiento:
   - Seed Launch: Pequeña audiencia, oferta de pruebas, recoger testimonios
   - Lanzamiento interno: lista de correo electrónico y audiencia existente
   - Lanzamiento de la asociación: socios y socios de JV
   - Lanzamiento de pagos: Acondicionado con secuencias de retargeting
2. Definir el plazo de lanzamiento:
   - Pre-lanzamiento: 7-14 días de calentamiento y anticipación
   - Lanzamiento: 3-7 días cart-open ventana
   - Post-lanzamiento: 3-5 días de follow-up y a bordo
3. Establecer el objetivo de ingresos basado en el tamaño de la audiencia y la conversión prevista
4. Cálculo de las tasas de tráfico y conversión necesarias al revés de la meta de ingresos

## Fase 2: Pre-Launch Sequence
1. Diseño de pre-launch (contenido)value-first, construye anticipación:
   - Día 1-3: Contenido de sensibilización sobre problemas
   - Día 4-7: Contenido educativo de la solución
   - Día 8-10: Proof y contenido de pruebas sociales
   - Día 11-14: Anticipación y construcción de camareros
2. Crear el pre-launch secuencia de correo electrónico
3. Diseño del calendario de contenido de redes sociales
4. Construir el camarero o early-bird mecanismo
5. Crear el arco narrativo de "lanzamiento"

## Fase 3: Plan de Ejecución de la Iniciación
1. Carrito Plan de día abierto:
   - Secuencia de correo electrónico (anuncio abierto + 2 follow-ups)
   - Puestos de los medios sociales (reunión + behind-the-scenes)
   - Lista de verificación en vivo de la página de ventas
2. Plan de Mid-cart:
   - Estudio de caso o correo testimonial
   - Preguntas frecuentes sobre las principales objeciones
   - Recordatorio de bonos
3. Carrito Plano de cierre:
   - 48 horas de advertencia email
   - Correo electrónico de advertencia de 24 horas
   - Correo electrónico de horas finales (3 horas, 1 hora, cierre)
   - Intensificación de la frecuencia en la sociedad
4. Definir el mecanismo de escasez (cuantidad, tiempo, vencimiento de bonificación)

### Phase 4: Post-Launch
1. Gracias y plan de a bordo para los compradores
2. Mensajería "Puerta cerrada" para non-buyers
3. Estrategia de reunión de resultados (para futuros lanzamientos)
4. Métulas de datos: ingresos, tasa de conversión, rendimiento de correo electrónico
5. Plan de transición permanente (si es aplicable)

---

## Formato de salida

```markdown
## Launch Plan: {Product Name}

**Launch Type:** {type}
**Timeline:** {dates}
**Revenue Target:** ${X}
**Audience Size:** {N}
**Required Conversion Rate:** {X}%

---

### Launch Calendar

| Phase | Days | Key Actions |
|-------|------|-------------|
| Pre-Launch | Day 1-14 | {summary} |
| Cart Open | Day 15-17 | {summary} |
| Mid-Cart | Day 18-19 | {summary} |
| Cart Close | Day 20-21 | {summary} |
| Post-Launch | Day 22-26 | {summary} |

### Pre-Launch Content Plan
| Day | Content | Channel | Goal |
|-----|---------|---------|------|

### Email Sequence
| Day | Email | Subject Line | Purpose |
|-----|-------|-------------|---------|

### Cart Open Checklist
- [ ] {item}

### Revenue Model

| Metric | Target | Conservative | Aggressive |
|--------|--------|-------------|------------|
| Traffic | {N} | {N} | {N} |
| Conversion | {X}% | {X}% | {X}% |
| Revenue | ${X} | ${X} | ${X} |

### Post-Launch Plan
{Onboarding, follow-up, and evergreen transition}
```

---

## Condiciones de veto

- Nunca lanzamiento sin un pre-launch secuencia — lanzamientos fríos infravalorados
- Nunca corra un open-ended lanzamiento - carro debe cerrar para crear urgencia
- Nunca lanzamiento sin un follow-up Plan de non-buyers
- NUNCA saltar el modelo de ingresos - lanzar sin objetivos es adivinar
- Nunca prometes resultados que no puedes demostrar con pruebas

---

## Criterios de finalización

- [ ] Modelo de lanzamiento seleccionado con racional
- [ ] Línea de tiempo con todas las fases
- [ ] Plan de contenido pre-lanzamiento creado
- [ ] secuencia de correo electrónico delineada para todas las fases
- [ ] Carrito open/mid/close planes de ejecución definidos
- [ ] Modelo de ingresos calculado con escenarios
- [ ] Plan de poslanzamiento incluido
- [ ] Mecanismo de escasez definido
