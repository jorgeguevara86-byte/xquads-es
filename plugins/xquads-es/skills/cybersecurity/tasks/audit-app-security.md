---
task: auditAppSecurity()
responsavel: "@jim-manico"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: application_url
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: tech_stack
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: app_security_audit
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Modelo de amenaza creado con análisis de STRIDE" 
  - "[ ] Todas las categorías de OWASP 10 mejores probados" 
  - "[ ] Plan de rehabilitación con code-level Ejemplos de solución" 
---

# Task: OWASP Application Security Audit

** ID de la lista:**
**Version:** 1.0.0
**Command:** `*audit-app-security`
* Agente* Jim Manico (Jim Manico)jim-manico)
**Fuente:** Realizar un examen amplio de la seguridad de la aplicación basado en la metodología OWASP.

---

## Inputs

| Entrada | Fuente | Requerido |
|-------|--------|----------|
| `application_url` Silencio Silencio Silencio Silencio Silencio Silencio
| `source_code_access` 
| `tech_stack` TENCIÓN Usuario o auto-detected Silencio , . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
| `authentication_type` Silencioso descripción de usuario Silencio Silencio
| `api_documentation` | OpenAPI/Swagger | NO |
| `previous_audit` TENIDO RESPUESTAS ANTERIOR ANTERIOR ANTERIOR ANTERIOR ANTERIOR ANTERIOR ANTERIOR ANTERIOR ANTERIOR ANTERIOR ANTERIOR ANTERIOR ANTERIOR ANTE

## Preconditions

1. La aplicación es accesible para pruebas (URL o entorno local)
2. Autorización para probar la aplicación se confirma
3. Se identifican las pilas de tecnología (idioma, marco, base de datos, proveedor de austeridad)
4. Prueba de las credenciales de la cuenta proporcionadas (si las zonas autenticadas tienen alcance)

## Fases de Ejecución

### Fase 1: Modelo de amenaza

1. Identificar la arquitectura de aplicaciones — frontend, backend, database, third-party servicios
2. Corrientes de datos de mapa —rutas de entrada de usuarios, llamadas API, almacenamiento de datos, integraciones externas
3. Identificar límites de confianza — capas de austeridad, niveles de privilegios, segmentos de red
4. Crear modelo de amenaza utilizando la metodología STRIDE:
   - **S**poofing - debilidades de autenticación
   - **T**ampering - riesgos de integridad de datos
   - **R**epudiation - lagunas en la logística y la auditoría
   - **I**nformation Divulgación: riesgos de exposición de datos
   - **D**enial de los vectores de agotamiento de los recursos
   - **E**levation de Privilege - autorización de caminos de derivación
5. Priorizar las amenazas por probabilidad e impacto

## Fase 2: Revisión del Código (si hay fuente disponible)

1. Revisión de la aplicación de la autenticación: contraseña, gestión de sesiones, MFA
2. Analizar la lógica de autorización RBAC/ABAC cumplimiento, cheques IDOR
3. Inspeccionar la validación de entrada - sanitización, consultas parametizadas, codificación de salida
4. Compruebe el uso criptográfico — selección de algoritmos, gestión clave, configuración TLS
5. Revisión de la manipulación de errores — fuga de información, trazas de pilas, puntos finales de depuración
6. Evaluar la seguridad de la dependencia: bibliotecas vulnerables conocidas ( auditación de las npm, Snyk)
7. Controle los encabezados de seguridad — CSP, HSTS, X-Frame-Options, CORS policy

## Fase 3: Vulnerabilidad Escaneando

1. Ejecute el escáner automatizado contra las 10 categorías OWASP Top:
   - A01: Control de Acceso Roto
   - A02: Fallos críptos
   - A03: Inyección (SQL, NoSQL, Comando, LDAP)
   - A04: Diseño Inseguro
   - A05: Misconfiguración de seguridad
   - A06: Componentes vulnerables
   - A07: Fallos de autenticación
   - A08: Faltas de integridad de datos
   - A09: Fallos de vigilancia
   - A10: SSRF
2. Verificación manual de los resultados automatizados (eliminar falsos positivos)
3. Prueba de fallas lógicas de negocio no atrapados por escáneres
4. Pruebas de seguridad de la API - rotas object-level auth, asignación masiva, tasa límite

## Fase 4: Plan de rehabilitación

1. Mapa de cada hallazgo a la categoría OWASP y identificador CWE
2. Proporcionar datos específicos code-level - recomendaciones de solución
3. Referencia de Hojas de Cheat OWASP para cada remediación
4. Priorizar las correcciones: Crítico (para ahora) √Īo Alto (este sprint) √ Medium (la siguiente sprint) √ Bajo (atrasolog)
5. Proporcionar ejemplos de código seguro en la pila de tecnología de la aplicación
6. Recomendar bibliotecas de seguridad y middleware

## Formato de salida

```yaml
app_security_audit:
  application: "{app name/url}"
  auditor: "jim-manico"
  methodology: "ASVS OWASP + Top 10" 
  tech_stack: "{Elegitimación de pila}" 
  threat_model:
    architecture: "{description}"
    trust_boundaries: ["{ lista de destinatarios}" ]
    stride_findings: ["{ lista de la lista de la lista}" ]
  findings:
    - id: "APP-001"
      owasp_category: "A01 — Control de acceso roto" 
      cwe: "CWE-284"
      title: "{finding}"
      severity: "CRITICAL TENIDO ALTO ANTERIOR MEDIUM ANTE LAS" 
      location: "{file:line or endpoint}" 
      description: "{detallado descripción}" 
      remediation: "{específica fijación con ejemplo de código}" 
      cheat_sheet: "{WowASP tramposa URL}" 
  remediation_plan:
    critical: ["{Imediatamente arreglados}" ]
    high: ["{Este sprint}" ]
    medium: ["{Siguiente sprint}" ]
    low: ["{backlog}"]
```

## Condiciones de veto

* * * * * * * Testar áreas autenticadas sin credenciales de prueba adecuadas
- ** NUNCA** intentar ataques destructivos contra sistemas de producción
- **Nunca** ignorar los hallazgos sólo porque son calificados como LOW
- ############################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################### security-by-obscurity como una reparación
- ** NUNCA** saltar la verificación manual de los resultados del escáner automatizado

## Criterios de finalización

Modelo de amenaza creado con análisis de STRIDE
- [ ] Revisión del código completada (si hay fuente disponible)
[ ] Todas las categorías OWASP 10 mejores probados
- Los falsos positivos eliminados mediante la verificación manual
- Cada hallazgo se ha asignado a la categoría OWASP y CWE
- Plan de rehabilitación con code-level Ejemplos de solución
- [ ] Referencias seguras de codificación proporcionadas para cada hallazgo
