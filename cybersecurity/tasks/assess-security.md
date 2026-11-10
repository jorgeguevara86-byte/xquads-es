---
task: assessSecurity()
responsavel: "@cyber-chief"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: target_description
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: scope_definition
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: security_assessment
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Autorización confirmada y definida" 
  - "[ ] Todos los hallazgos clasificados con las puntuaciones CVSS" 
  - "[ ] Hoja de ruta de rehabilitación generada con prioridades" 
---

# Task: Security Posture Assessment

** ID de la lista:**
**Version:** 1.0.0
**Command:** `*assess-security`
**Agente:** Jefe Cibernéticocyber-chief) rutas a especialistas
**Purpose:** Realizar una evaluación completa de la postura de seguridad de un sistema u organización objetivo.

---

## Inputs

| Entrada | Fuente | Requerido |
|-------|--------|----------|
| `target_description` Silencio Silencio Silencio Silencio Silencio Silencio
| `scope_definition` ← Usuario o compromiso docs TENIDO YES TENIDO
| `authorization_proof` Silencio Silencio Silencio Silencio Silencio Silencio
| `existing_reports` Silencio Anteriores evaluaciones Silencio NO Silencio
| `compliance_requirements` 

## Preconditions

1. Confirmación de la autorización escrita para el alcance de la evaluación
2. La descripción de objetivos incluye rangos de red, aplicaciones o detalles de org
3. Marco ético reconocido - ninguna operación destructiva

## Fases de Ejecución

### Fase 1: Definición de alcance (cyber-chief)

1. Objetivos de evaluación de la claridad (aplicación, riesgo, pre-pentest, incident-driven)
2. Definición in-scope y out-of-scope activos
3. Identificar el tipo de evaluación: externo, interno, híbrido
4. Confirme las reglas de compromiso (ventanas de tiempo, hosts restringidos, contactos de escalada)
5. Ruta sub-tasks a especialistas apropiados sobre la base de su alcance

### Fase 2: Reconnaissance &quot; Data Gathering

1. **Reconocimiento pasivo** — OSINT, registros DNS, transparencia de certificados (cartógrafo)
2. **Escaneo activo** — Escaneo portuario, enumeración de servicios (command-generator para comandos de herramientas)
3. ** Cartografía de aplicaciones** — Puntos finales de aplicaciones web, superficies de API (jim-manico)
4. ** Topología de red** — Identificar segmentos, límites de confianza, puntos de egreso (chris-sanders)
5. Agregar todas las conclusiones en un inventario estructurado

### Fase 3: Análisis &quot; Alcanzar riesgos &quot;

1. Mapa descubrió activos contra bases de datos de vulnerabilidad conocidas
2. Clasificar los hallazgos utilizando CVSS 3.1 puntuación
3. Identificar caminos de ataque y oportunidades de movimiento lateral (peter-kim)
4. Evaluar los controles defensivos en su lugar (chris-sanders)
5. Referencias cruzadas contra los requisitos de cumplimiento (si procede)
6. Priorizar los riesgos: Critical √≥ Alto √ Medium √≥n √≥n Bajo √≥ Informaciónal

### Phase 4: Report Generation

1. Resumen ejecutivo: riesgo de actividad non-technical idioma
2. Conclusiones técnicas - cada vulnerabilidad con evidencia, puntuación CVSS, remediación
3. Mapa de superficie de ataque: representación visual de activos expuestos
4. Hoja de ruta para la rehabilitación: medidas prioritarias con estimaciones de esfuerzos
5. Ganancias rápidas: artículos fijos en 24 a 48 horas
6. Recomendaciones estratégicas long-term mejoras de seguridad

## Formato de salida

```yaml
security_assessment:
  target: "{Nombre de la tienda}" 
  scope: "{árgen de evaluación}" 
  date: "{fecha de evaluación}" 
  assessor: "cyber-chief + specialists"
  executive_summary: "{Examen de riesgo de nivel de negocios}"
  findings:
    - id: "FIND-001"
      title: "{finiendo título}" 
      severity: "CRITICAL TENIDO ALTO ANTERIOR MEDIUM ANTE LAS RESPUESTAS" 
      cvss_score: 0.0
      description: "{detallado descripción}" 
      evidence: "{prueba de encontrarlo}" 
      remediation: "{Recomendación de impuestos}" 
      effort: "QUICK_WIN TEN ANTE SHORT_TERM TEN LONG_TERM" 
  attack_surface:
    external_exposure: "{summary}"
    internal_risks: "{summary}"
  remediation_roadmap:
    immediate: ["{victorias rápidas}" ]
    short_term: ["{1-4 artículos de la semana}" ]
    long_term: ["{Mejoras estratégicas}" ]
```

## Condiciones de veto

- ** NUNCA** realizar evaluación sin autorización confirmada
- ** NUNCA** escanear o enumerar out-of-scope metas
- ** NUNCA** intentar explotación durante una evaluación de postura (que requiere un compromiso de pentaste separado)
* **Nunca** compartir conclusiones con partes no autorizadas
- **Nunca** minimizar los hallazgos críticos para conveniencia

## Criterios de finalización

- [ ] Autorización confirmada y documentada
- [ ] Ámbito claramente definido con in/out límites
- [ ] Reconocimiento pasivo y activo completado
Todos los hallazgos clasificados con las puntuaciones CVSS
- [ ] Hoja de ruta de rehabilitación generada con prioridades
- Resumen ejecutivo escrito en lenguaje empresarial
- [ ] Informe presentado en formato estructurado
