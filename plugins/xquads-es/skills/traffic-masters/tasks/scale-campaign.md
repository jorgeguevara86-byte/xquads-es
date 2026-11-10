---
task: scaleCampaign()
responsavel: "@scale-optimizer"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: platform
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: campaign_data
    tipo: object
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: scalingPlan
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Evaluación de escalabilidad completada con calificaciones de riesgo" 
  - "[ ] Método de escalado seleccionado con racional" 
  - "[ ] Monitorear las barreras definidas con umbrales" 
---

# Task: Scale Campaign

** ID de la lista:** TRAFFIC-003
**Version:** 1.0.0
**Command:** `*scale-campaign`
**Agente:** Optimizador de escala (scale-optimizer) o Depesh Mandalia (depesh-mandalia)
**Purpose:** Escala campañas ganadoras de uso rentable del método BPM (Budget, Performance, Metrics).

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
Silencio, sopa, tiktok Silencio, tube, tiktok Silencio
| campaign_data TENCIÓN ANTERIOR ANTERIOR ANTERIOR Sí ANTERIGEN métricas actuales: pasar, CPA, ROAS, CTR, CVR, pasar diariamente ANTERI
| target_spend Silencio número Silencio Usuario prompt Silencio Sí Silencio Desired daily or monthly spend target Silencio
| current_spend Silencio número Silencio Sugerencia de usuario Silencio Silencio actual diario o mensual gastar Silencio
| max_cpa Silencio número Silencio Usuario prompt Silencio No Silencio Maximum acceptable CPA Silencio
| min_roas Silencio número Silencio Usuario prompt Silencio No Silencio mínima aceptable ROAS Silencio
TENIDO TIEMPO TENIDO TENIDO ANTERIOR NO TENENCIA Qué rápido a escala (aggresivo, moderado, conservador) TEN

---

## Preconditions

- La campaña ha demostrado su rendimiento en el nivel actual de gasto (mínimo 7 días de datos)
- El seguimiento es preciso y los eventos de conversión incendian correctamente
- La página de aterrizaje puede manejar el aumento del volumen de tráfico

---

## Fases de Ejecución

## Fase 1: Evaluación de la escalabilidad
1. Evaluar la preparación de escalada de la campaña:
   - ¿Es el público lo suficientemente grande para apoyar el gasto del objetivo?
   - ¿La creatividad muestra señales de fatiga (dedicando CTR)?
   - ¿Es estable el CPA o tendencia hacia arriba?
   - ¿Cuál es la frecuencia actual (el archivo 2.5 es una advertencia)?
2. Calcular el techo de escalada: tamaño de la audiencia / (capt de frecuencia x CPM) = gasto máximo diario
3. Evaluar la profundidad creativa: ¿cuántas anuncios ganadores están activos?
4. Compruebe la capacidad de backend: puede el negocio manejar 2x-5x la corriente lead/sale ¿volumen?

## Fase 2: Selección de Estrategias de Escalada
1. Elija el método de escalado basado en la brecha entre el gasto actual y el destino:
   - ** Escalada vertical (según se indica 2x):** Aumentar el presupuesto de las campañas existentes
     - 20% de aumento presupuestario cada 48-72 horas
     - Monitor para picos de CPA después de cada aumento
     - Reiniciar si el CPA aumenta más del 30% durante 48 horas
   - ** Escalada horizontal (2x-5x):** Duplicar a nuevos públicos
     - Duplicar los anuncios ganadores a nuevos segmentos de audiencia
     - Duplicar anuncios ganadores a nuevas campañas con diferentes objetivos
     - Prueba audiencias de aspecto a porcentajes crecientes
   - ** Escalada Diagonal (5x+):** Ampliar a nuevas plataformas y ángulos
     - Creativos ganadores de Puerto a nuevas plataformas
     - Prueba nuevos ángulos creativos contra audiencias probadas
     - Construir nuevos embudos para la nueva temperatura de tráfico
2. Definir el calendario de escala con los hitos presupuestarios
3. Establecer criterios de matar para cada fase de escalado

### Fase 3: Escala Creativa
1. Identificar los elementos creativos que impulsan el rendimiento:
   - ¿Qué ganchos funcionan mejor?
   - ¿Qué formatos convierte mejor?
   - ¿Qué audiencia responde a qué creativos?
2. Planifique el oleoducto creativo de la iteración:
   - Variación 1: Mismo gancho, diferente visual
   - Variación 2: El mismo gancho visual y diferente
   - Variación 3: Mismo mensaje, diferente formato (imagen a vídeo, etc.)
3. Establecer el calendario creativo de refrescos:
   - Pequeños públicos: Nuevo creativo cada 5-7 días
   - Grandes audiencias: Nuevo creativo cada 14-21 días
4. Construir un "banco creativo" de 5-10 anuncios listos para desplegar cuando golpes de fatiga

### Fase 4: Monitoreo y vigilancia
1. Definir métricas y umbrales de monitoreo diario:
   - umbral de CPA: Max X% por encima del objetivo antes de pausar
   - umbral ROAS: Min X:1 antes de pausing
   - umbral de frecuencia: Max X antes de la actualización creativa
   - Paso de paso: Profundización diaria prevista de tolerancia a la varianza
2. Crear el protocolo de escalada:
   - PAP 20-30%: Reducir el 20% del presupuesto, monitor 48h
   - PAP 30-50%: Pausa, diagnóstico, fijación antes de reanudar
   - CPA pico 50%+: Matar el conjunto de anuncios, lanzar nueva prueba
3. Establecer puestos de control semanales con respecto a la base de referencia
4. Definir el hito "el éxito escalador" — ¿cuándo se alcanza la escala?

---

## Formato de salida

```markdown
## Scaling Plan: {Campaign Name}

**Platform:** {platform}
**Current Spend:** ${X}/day
**Target Spend:** ${Y}/day
**Scale Factor:** {X}x
**Method:** {vertical / horizontal / diagonal}
**Timeline:** {X weeks}

---

### Scalability Assessment

| Factor | Status | Risk |
|--------|--------|------|
| Audience Size | {adequate/limited} | {low/med/high} |
| Creative Depth | {N winning ads} | {low/med/high} |
| CPA Stability | {stable/rising} | {low/med/high} |
| Frequency | {current} | {low/med/high} |
| Backend Capacity | {ready/concern} | {low/med/high} |

### Scaling Schedule

| Week | Daily Budget | Method | New Elements |
|------|-------------|--------|-------------|

### Creative Pipeline

| Priority | Creative | Format | Audience | Status |
|----------|---------|--------|----------|--------|

### Guardrails

| Metric | Threshold | Action if Breached |
|--------|-----------|-------------------|

### Kill Criteria
{When to stop scaling and reassess}

### Success Milestone
{Definition of scaling success}
```

---

## Condiciones de veto

- NUNCA escala una campaña con menos de 7 días de datos estables
- Nunca aumentar el presupuesto más del 20% en un solo día (scaling vertical)
- NUNCA escala sin un oleoducto creativo listo - usted golpeará fatiga
- NUNCA ignora la frecuencia - escalar en público fatigado quema dinero
- NUNCA escala si el seguimiento es inconfiable - no puede optimizar lo que no puede medir

---

## Criterios de finalización

- [ ] Evaluación de escalabilidad completada con calificaciones de riesgo
- [ ] Método de escalado seleccionado con racional
- [ ] Calendario del presupuesto programado semana a semana
- [ ] Construido con tracción creativa 5-10 ready-to-deploy anuncios
- [ ] Monitorear las barreras definidas con umbrales
- [ ] Criterios de asesinato establecidos
- [ ] El hito definido
