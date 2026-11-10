---
task: resolveCultureCrisis()
responsavel: "@board-chair"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: crisis_description
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: symptoms
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: culture_resolution
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[] Se aplicaron los tres marcos de diagnóstico" 
  - "[ ] Causa raíz identificada con cadena causal mapeada" 
  - "[ ] Plan de implementación con resultados rápidos y criterios de medición" 
---

# Tarea: Resolución de disfunción de cultura y equipo

**ID de tarea:** BOARD-003
**Version:** 1.0.0
**Command:** `*resolve-culture-crisis`
**Agente:** El presidente de la junta directiva se dirige a Simon Sinek + Brene Brown + Patrick Lencioni
**Propósito:** Diagnosticar y resolver disfunciones de la cultura organizacional o ruptura del equipo.

---

## Inputs

| Entrada | Fuente | Requerido |
|-------|--------|----------|
| `crisis_description` | Mensaje de usuario | SÍ |
| `team_size` | Número de personas afectadas | PREFERIDO |
| `symptoms` | Comportamientos y problemas observables | SÍ |
| `duration` | ¿Cuánto tiempo lleva sucediendo esto? PREFERIDO |
| `previous_interventions` | Lo que ya se ha probado | NO |
| `organizational_context` | Etapa de la empresa, industria, valores | NO |

## Preconditions

1. Se reconoce disfunción cultural o de equipo
2. Se describen síntomas observables (no sólo una sensación vaga)
3. Voluntad de abordar las causas fundamentales, no sólo los síntomas

## Fases de Ejecución

### Fase 1: Diagnosticar la disfunción

**Patrick Lencioni — Evaluación de las cinco disfunciones:**
1. **Ausencia de confianza**: ¿Los miembros del equipo ocultan debilidades y errores?
2. **Miedo al conflicto**: ¿Evitan las conversaciones difíciles?
3. **Falta de compromiso**: ¿no aceptan sus decisiones?
4. **Evitar la responsabilidad**: ¿Evitan criticar a sus compañeros?
5. **Falta de atención a los resultados**: ¿priorizan el estatus individual sobre los objetivos del equipo?
6. Identifique qué disfunción es la raíz principal (caen en cascada desde la confianza hacia abajo)
7. Evaluar la gravedad: alerta temprana, patrón establecido o crisis

**Brene Brown: Evaluación de vulnerabilidad:**
1. ¿Existe seguridad psicológica para ser honesto e imperfecto?
2. ¿La gente se está blindando (perfeccionismo, cinismo, adormecimiento)?
3. ¿Existe una brecha entre los valores adoptados y los valores practicados?
4. ¿Qué historias se cuentan las personas sobre la situación?
5. ¿Está presente la vergüenza? ¿Tiene la gente miedo de ser vista como inadecuada?

**Simon Sinek — Verificación de alineación de propósitos:**
1. ¿El PORQUÉ es claro y compartido en todo el equipo?
2. ¿La organización se ha desviado de su propósito fundacional?
3. ¿La gente está jugando un juego finito (ganar) o un juego infinito (sostener)?
4. ¿Existe alguna causa justa que inspire al equipo?
5. ¿Están los líderes sirviendo al pueblo o la gente está sirviendo a los líderes?

### Fase 2: Identificar la causa raíz

1. Haga una referencia cruzada de los tres marcos de diagnóstico
2. Identifique la raíz más profunda: generalmente la confianza o el propósito, no el síntoma visible.
3. Traza la cadena causal: causa raíz → cascada → síntomas visibles
4. Determine si se trata de un problema de personas, de procesos o de liderazgo.
5. Valorar si el liderazgo es parte de la causa o parte de la solución
6. Identifique la intervención que tendría el mayor apalancamiento

### Fase 3: Intervención de Diseño

**Para déficit de confianza (líder de Lencioni):**
1. Ejercicio de historias personales: generar confianza en vulnerability-based 
2. Perfiles de comportamiento: comprender los estilos de trabajo de cada uno
3. Ejercicio de eficacia del equipo: discusión abierta sobre fortalezas y debilidades
4. El líder va primero: la vulnerabilidad debe venir desde arriba

**Para Déficit de Coraje (plomo marrón):**
1. Nombra la armadura: ¿qué comportamientos defensivos están presentes?
2. Retumbar con la vulnerabilidad: conversaciones facilitadas sobre temas difíciles
3. Aclaración de valores: alinear los valores declarados con el comportamiento real
4. Claro es amable: establezca normas para una retroalimentación directa y compasiva

**Para déficit de propósito (plomo de Sinek):**
1. Redescubra el PORQUÉ: ¿qué inspiró originalmente el team/company?
2. Encuentre la causa justa: ¿por qué vale la pena luchar por la visión de long-term ?
3. Establecer una mentalidad de juego infinito: pasar de "vencer a los competidores" a "promover la causa"
4. Identifique rivales dignos: aprenda de los demás en lugar de intentar destruirlos.

### Fase 4: Plan de implementación

1. Intervenciones en secuencia: abordar primero la causa raíz y luego los efectos posteriores
2. Defina ganancias rápidas: ¿qué se puede mejorar en una semana?
3. Definir cambios estructurales: ¿qué necesita entre 30 y 90 días?
4. Asigne responsabilidades de liderazgo: ¿quién impulsa cada intervención?
5. Establezca criterios de medición: ¿cómo sabrá que está funcionando?
6. Plan check-ins : semanal durante el primer mes, luego bi-weekly
7. Definir los factores desencadenantes de la escalada: ¿qué señales de que la intervención no está funcionando?

## Formato de salida

```yaml
culture_resolution:
  advisors: [simon-sinek, brene-brown, patrick-lencioni]
  diagnosis:
    lencioni_dysfunction: "{disfunción primaria}" 
    brown_vulnerability: "{evaluación de coraje}" 
    sinek_purpose: "{evaluación de alineación}" 
    root_cause: "{raíz más profunda}" 
    causal_chain: "{raíz → cascada → síntomas}" 
    severity: "early_warning | establecido | crisis" 
  intervention:
    primary: "{intervención de mayor apalancamiento}" 
    trust_building: ["{ejercicios específicos}" ]
    courage_building: ["{prácticas específicas}" ]
    purpose_alignment: ["{acciones específicas}" ]
  implementation:
    week_1: ["{victorias rápidas}" ]
    month_1: ["{cambios estructurales}" ]
    month_3: ["{prácticas sostenidas}" ]
    measurement: ["{indicadores de éxito}" ]
    escalation_triggers: ["{señales de advertencia}" ]
```

## Condiciones de veto

- **NUNCA** culpe a las personas; céntrese en los sistemas, los patrones y el liderazgo
- **NUNCA** omita la evaluación de confianza: la confianza es la base de todo
: **NUNCA** recomiendo correcciones surface-level (eventos de formación de equipos) sin abordar la causa raíz
- **NUNCA** ignore el papel del liderazgo en la disfunción
- **NUNCA** apresure el proceso: el cambio cultural requiere tiempo y esfuerzo constante

## Criterios de finalización

- [ ] Se aplicaron los tres marcos de diagnóstico
- [ ] Causa raíz identificada con cadena causal asignada
- [ ] Gravedad evaluada (alerta temprana/establecida/crisis)
- [ ] Intervención diseñada para abordar primero la causa raíz
- [ ] Plan de implementación con resultados rápidos y cambios estructurales
- [ ] Criterios de medición definidos
- [ ] Activadores de escalada establecidos
