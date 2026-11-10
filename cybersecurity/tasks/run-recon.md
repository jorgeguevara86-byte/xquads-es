---
task: runRecon()
responsavel: "@cartographer"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: target
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: target_type
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: recon_report
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Reconocimiento pasivo y activo completado" 
  - "[ ] Directorio y enumeración de servicios completados" 
  - "[ ] superficie de ataque mapeado con high-value metas identificadas" 
---

# Task: Reconnaissance &quot; Enumeration

** ID de la lista:**
**Version:** 1.0.0
**Command:** `*run-recon`
**Agente:** Cartógrafo (cartógrafo) + Dirber (dirber)
**Fuente:** Realizar un reconocimiento sistemático y una enumeración de objetivos autorizados.

---

## Inputs

| Entrada | Fuente | Requerido |
|-------|--------|----------|
| `target` Silencio vocacional voca miento voca 
| `target_type` TENIDO Dominio, IP, range, webapp ANTE SI TENIDO
| `authorization` Silencio Silencio Silencio Silencio Silencio Silencio
| `depth` TENIDOS, estándar, profundo TENIDO NO (por defecto: estándar) TENIDO
| `stealth_required` ← Boolean TEN NO (por defecto: falso) TENIDO
| `known_information` 

## Preconditions

1. La meta está dentro del ámbito autorizado
2. Autorización confirmada para el escaneo activo
3. Tipo de destino identificado (dominio, rango de IP, aplicación web)
4. Conectividad de la red para determinar la meta verificada

## Fases de Ejecución

### Fase 1: Reconocimiento pasivo (cartógrafo)

1. **DNS Intelligence** — DNS records (A, AAAA, MX, NS, TXT, CNAME, SOA), zone transfers
2. **WHOIS &quot; Registro**: Registro de dominios, registrador, servidores de nombres, creation/expiry
3. ** Transparencia significativa** — Certificados SSL, subdominios a través de los registros de TC (crt.sh)
4. **OSINT Collection** — Google dorking, Shodan consultas, Censys, bases de datos de brecha pública
5. **Email Harvesting** — Recopilar patrones de correo electrónico, validar direcciones (si en su alcance)
6. **Finificación de tecnología** — Detección de estilo Wappalyzer, cabeceras HTTP, meta tags
7. **Reconocimiento de los medios sociales** — enumeración de empleados de LinkedIn, GitHub repos (si tiene alcance)
8. Compilar resultados pasivos en inventario estructurado

### Fase 2: Reconocimiento activo (cartógrafo)

1. **Host Discovery** — barrido de Ping, escaneo ARP (redes locales), descubrimiento de TCP SYN
2. **Escaneamiento de porte** — Escaneo completo TCP, puertos UDP superiores, detección de la versión de servicio
3. ** Fingerprinting de servicio** — Apropiación de banner, identificación de protocolo
4. **OS Detection** TCP/IP apilar huellas dactilares, análisis TTL
5. **SSL/TLS Análisis** — Detalles del certificado, suites del cifrado, versiones de protocolo, vulnerabilidades
6. ** Topología de la red** — Análisis de la tracción, el análisis de la urbe, firewall/WAF detección
7. Si se requiere el robo: reducir la tasa de escaneo, utilizar escáneres SYN, aleatorizar el orden portuario

### Fase 3: Enumeración (dirber)

1. **Enumeración del directorio web** — Rutas comunes, archivos de copia de seguridad, paneles de administración
2. **Descubrimiento histórico de la organización de acogida** — Subdominio brute-force, enumeración de los vhost
3. **API Endpoint Discovery** — Rutas comunes de API, puntos finales de la versión, URLs de documentación
4. **Enumeración del usuario** — Formularios de inicio de sesión, registro, restablecimiento de contraseñas (timing/response diferencias)
5. **Escaneamiento de extensión de archivo** — Tipos de archivo sensibles (.bak, .sql, .env, .git, .DS_Store)
6. **Detección de CMS** — WordPress, Drupal, Joomla plugins/themes enumeración
7. **Descubrimiento del parámetro** — Oculto GET/POST parámetros, parámetros de depuración

### Fase 4: Correlación &quot; Reporting

1. Conclusiones pasivos y activos de referencia cruzada - validar OSINT con resultados de exploración
2. Identificar superficie de ataque — servicios expuestos, puntos finales interesantes, puntos de entrada potenciales
3. Relaciones de mapas: subdominio a IP, servicio a tecnología, usuario a función
4. Alto alcance high-value objetivos — paneles de administración, portales de API, sistemas heredados, dev/staging
5. Generar documento de perfil objetivo con vectores de ataque prioritarios
6. Recomendar los siguientes pasos: exploración de la vulnerabilidad, áreas específicas de enfoque de la pentesta

## Formato de salida

```yaml
recon_report:
  target: "{target}"
  recon_agent: "cartógrafo + dirber" 
  depth: "shallow TEN SON TEN ANTE" 
  stealth_mode: false
  passive_findings:
    dns_records: ["{records}"]
    subdomains: ["{lista de subdominios}" ]
    technologies: ["{Equipo tecnológico}" ]
    emails: ["{Emails dañados}" ]
  active_findings:
    hosts: ["{Asfitriones activos}" ]
    open_ports: ["{puerto: cartografías de servicios}" ]
    os_detection: ["{OS huellas dactilares}" ]
    ssl_issues: ["{Exámenes de la TLS}" ]
  enumeration:
    directories: ["{ruidos descubiertos}" ]
    api_endpoints: ["{Pasos de la API}" ]
    interesting_files: ["{según archivos sensibles}" ]
  attack_surface:
    high_value_targets: ["{Objetivos prioritarios}" ]
    potential_vectors: ["{ruidos de ataque}" ]
    recommended_next_steps: ["{actions}"]
```

## Condiciones de veto

- ** NUNCA** objetivos de escaneo sin autorización
- ** NUNCA** realizar escaneos activos cuando sólo se autorizó el reconocimiento pasivo
- ** NUNCA** intento de explotar vulnerabilidades descubiertas durante el reconocimiento
* * * * * * enumerar usuarios para fines de relleno credencial
- ** NUNCA** ignorar los requisitos de robo cuando se especifica

## Criterios de finalización

- [ ] Reconocimiento pasivo completado con conclusiones estructuradas
- [ ] Escaneo activo ejecutado dentro del alcance autorizado
- [ ] Listado de directorios y servicios completados
- [ ] Encontraron correlacionados y cross-referenced
- [ ] Ataque superficie mapeada con high-value metas identificadas
- [ ] Siguientes pasos recomendados para una nueva evaluación
