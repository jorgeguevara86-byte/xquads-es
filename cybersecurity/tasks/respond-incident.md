---
task: respondIncident()
responsavel: "@omar-santos"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: incident_description
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: affected_systems
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: incident_report
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Incident clasificado con severidad y cronología establecida" 
  - "[ ] Acciones de retención ejecutadas y verificadas" 
  - "[ ] Las lecciones aprendidas documentadas con mejoras factibles" 
---

# Task: Incident Response Playbook

** ID de la lista:**
**Version:** 1.0.0
**Command:** `*respond-incident`
*Agente* Omar Santos (*omar-santos)
**Fuente:** Ejecute una respuesta estructurada de incidentes después del marco NIST 800-61.

---

## Inputs

| Entrada | Fuente | Requerido |
|-------|--------|----------|
| `incident_description` | User/alert sistema TEN TERRITORIO TERRITORIO
| `affected_systems` TENIDO Usuario o monitoreo TENIDO ANTERIOR ANTERIOR
| `incident_severity` Silencio inicial Silencio Silencio Silencio Silencio Silencio
| `timeline_so_far` Silencioso descripción de usuario Silencio
| `available_logs` 
| `contacts_list` Silenciosos contactos de escalada Silencio NO TEN

## Preconditions

1. Se ha informado o detectado incidentes
2. Clasificación inicial de la gravedad (P1-P4)
3. Los sistemas o alcances afectados se identifican al menos parcialmente
4. El demandado tiene acceso a los sistemas y registros pertinentes

## Fases de Ejecución

### Fase 1: Preparación

1. Confirmación de funciones de equipo de respuesta a incidentes y canales de comunicación
2. Verificar el acceso a las herramientas necesarias — SIEM, agregadores de registros, herramientas forenses
3. Establecer un canal de comunicación seguro (out-of-band si se sospecha que se ha comprometido)
4. Revisar los libros de texto existentes de IR para tipos de incidentes similares
5. Preparar procedimientos de recopilación de pruebas: cadena de custodia, herramientas de imagen
6. Confirmación de los requisitos de notificación de cumplimiento y cumplimiento

### Fase 2: Identificación &quot; Triage

1. Recopilar los indicadores iniciales de compromiso (COI) — IPs, hashes, domains, user accounts
2. Determinar el tipo de incidente — malware, phishing, acceso no autorizado, violación de datos, amenaza de intrusión
3. Establecer el plazo —cuando comenzó, cuando se detectó, lo que pasó entre
4. Evaluar el radio de explosión - qué sistemas, datos y usuarios se ven afectados
5. Clasificación de la gravedad basada en el impacto:
   * * * * Crítica* - Exfiltración de datos activos, propagación de ransomware, sistema crítico hacia abajo
   **P2 High** — Compromiso confirmado, movimiento lateral detectado, datos sensibles en riesgo
   **P3 Medium** — Confirmación de la actividad sospechosa, alcance limitado, no pérdida de datos aún
   **P4 Low** — Violación de políticas, ataque fallido, alerta informativa
6. Activar el nivel adecuado de respuesta basado en la gravedad

### Phase 3: Containment

1. **Contención a corto plazo** — Sistemas afectados aislados, bloques maliciosos IPs/domains, cuentas comprometidas deshabilitadas
2. **Reservación de la evidencia** — Capturar los vertederos de memoria, imágenes de disco, instantáneas de registro antes de cambios
3. **Contención de red** — Redes afectadas por el segmento, actualización de las reglas del cortafuegos, permiten una mejor vigilancia
4. **Contención confidencial**: Reasentar las credenciales comprometidas, revocar las fichas, la fuerza re-authentication
5. **Comunicación** - Notificar a los interesados por gravedad (véase el documento inglés).P1/P2: notificación inmediata de los ejecutivos)
6. Verificar la eficacia de la contención: confirmar el acceso de los atacantes se ha reducido

### Fase 4: Erradicación

1. Identificar la causa raíz — vulnerabilidad explotada, vector de phishing, configuración errónea
2. Eliminar malware, backdoors y mecanismos de acceso no autorizados
3. Vuelta vulnerabilidades explotadas
4. Reconstruir sistemas comprometidos de known-good Bases de referencia
5. Escaneo para los indicadores residuales de compromiso
6. Verificar la erradicación — no confirmar la presencia de atacantes que aún no haya existido

### Fase 5: Recuperación

1. Restaurar los sistemas afectados de copias de seguridad limpias
2. Sistemas de reintroducción gradual a la producción con mayor vigilancia
3. Validar la integridad del sistema: sumas de comprobación, comparaciones de referencia
4. Monitoreo re-compromise indicadores (mínimo 72 horas mejorada de vigilancia)
5. Confirme todos los servicios restaurados y funcionando normalmente
6. Actualización de las reglas de detección basadas en COIs detectadas

### Fase 6: Lecciones Aprendidas

1. Conducta post-incident examen dentro de 5 días hábiles
2. Documento cronológico completo de incidentes con decisiones y resultados
3. Identificar lo que funcionó bien y lo que necesita mejora
4. Actualizar los libros de texto de IR basados en las lecciones aprendidas
5. Recomendar mejoras de seguridad para evitar la recurrencia
6. Crear paquetes de COI para compartir información sobre amenazas (si procede)

## Formato de salida

```yaml
incident_report:
  incident_id: "IR-{YYYY}-{NNN}"
  responder: "omar-santos"
  severity: "P1 Silencio P2 Silencio P3 Silencio P4" 
  type: "{tipo de accidente}" 
  status: "ACTIVE TENED ANTE LAS RESPECTO ANTE LAS RESPUESTAS ANTERIORADAS" 
  timeline:
    detected: "{timestamp}"
    contained: "{timestamp}"
    eradicated: "{timestamp}"
    recovered: "{timestamp}"
  affected_systems: ["{Siga la lista del sistema}" ]
  iocs:
    - type: "IP Silencio Silencio Silencio Silencio Silencio Silencio Silencio Silencio USUARIO" 
      value: "{indicator}"
      context: "{donde se observase}" 
  root_cause: "{Análisis de causa de raíz}"
  remediation_actions: ["{acciones tomadas}" ]
  lessons_learned:
    what_worked: ["{positives}"]
    improvements: ["{áreas para mejorar}" ]
    recommendations: ["{recidivantes}" ]
```

## Condiciones de veto

- **Nunca** saltar la preservación de evidencia antes de las acciones de contención
- ** NUNCA** restaurar sistemas sin verificar la integridad de la copia de seguridad
** NUNCA** declara cerrado el incidente sin un período de vigilancia mejorado
- **Nunca** compartir COI o detalles de incidentes sin autorización
** NUNCA** culpar a los individuos: centrarse en las mejoras de procesos y sistemas

## Criterios de finalización

- [ ] Incident clasificado con gravedad y tipo
- [ ] Línea de tiempo establecida de detección a estado actual
- [ ] Acciones de retención ejecutadas y verificadas
- Causa de raíz identificada
Erradicación confirmada sin compromiso residual
- [ ] Sistemas restaurados con mayor vigilancia activa
- [ ] Las lecciones aprendidas documentadas con mejoras factibles
