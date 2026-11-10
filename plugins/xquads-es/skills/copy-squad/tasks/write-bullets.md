---
task: writeBullets()
responsavel: "@gary-bencivenga"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: product
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: content_source
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: bullet_package
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[] Contenido fuente minada para todo material de bala" 
  - "[ ] Solicitado número de balas escritas usando fórmulas variadas" 
  - "[ ] 3-5 balas asesinas identificadas para multi-use" 
---

# Task: Write Bullet Points

** ID de la lista:** COPY-010
**Version:** 1.0.0
**Command:** `*write-bullets`
Gary Bencivengagary-bencivenga)
**Purpose:** Escribir curiosity-driven puntos de bala (fascinaciones) que venden sin revelar la respuesta.

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
Silencioso Silencio Silencio Silencio Silencio Silencio Silencio Silencio Product/service con contenido o características de bala Silencio
| content_source TENEDA TENCIÓN ANTERIOR ANTERIOR Sí ANTERIMA Material crudo para transformarse en balas (características, capítulos, lecciones, resultados) TENCIÓN
Silencio Silencio Silencio Silencio Silencio Silencio Silencio sales-page, email, VSL, ad, order-form |
Silencio audiencia Silencio cadena Silencio Usuario prompt Silencio No Silencio Lector de blanco para calibrar el idioma TEN
| num_bullets TENEDAD NVI TENIDO ANTERIOR NO TENIDO DEFaults to 20 TEN
Silencio estilo Silencio enum Silencio Usuario prompt Silencio No TENIDO fascinación, beneficio, prueba, híbrido — defaults to fascination TEN

---

## Preconditions

- Contenido fuente disponible (lista de características, tabla de contenidos, esquemas de lecciones o datos de resultados)
- Contexto para la colocación definida (losbultos para una página de ventas difieren de las balas de correo electrónico)

---

## Fases de Ejecución

### Fase 1: Minería Fuente
1. Extraer cada reclamación única, característica, beneficio o hecho del contenido fuente
2. Identificar qué hechos son más sorprendentes, contraintuitivos o valiosos
3. Ranke por "¿Alguien pagaría dinero sólo para saber esto?" factor
4. Grupo por tema para secciones de bala organizadas
5. Meta al menos 2x el recuento de bala solicitado como materia prima

## Fase 2: Escribir la bala
1. Escribe balas usando fórmulas de fascinación comprobadas:
   El secreto: "El secreto de cerca guardaba {outcome}..."
   - La contraintuitiva: - ¿Por qué? {opposite}..."
   - **El número específico: * "{Exact number] ways to {outcome} sin {sacrifice}..."
   - La pregunta: "¿Estás haciendo esto? ${cost} error con tu {thing}?"
   - El Prohibido: {authorities} No quiero que sepas {topic}..."
   - El examen: {person} logrado { Resultado específico} en {timeframe}..."
   - El Si-Entonces: {situation}Aquí está. {solution}..."
   - El aviso: {action} hasta que usted {precaution}..."
2. Aplicar la regla de especificidad de Bencivenga: balas vagas son balas muertas
3. Cada bala debe crear un bucle abierto que el lector necesita cerrar
4. Estructura de la frase Vary - nunca utilizar la misma fórmula consecutivamente
5. Entorpecer o enfatizar la frase más importante en balas más largas

### Fase 3: Selección y Ordenación
1. Partitura de cada bala en intensidad de curiosidad (1-5)
2. Seleccione las balas superiores (por cuenta solicitada)
3. Ordene estratégicamente:
   - Comienza fuerte (primero 2 balas)
   - Suplente entre balas emocionales y lógicas
   - Fin fuerte (salvo una bala poderosa por última vez)
4. Grupo en secciones temáticas si para una página de ventas larga
5. Marca 3-5 "balas asesinas" que podrían ser titulares independientes

---

## Formato de salida

```markdown
## Bullet Package: {Product Name}

**Context:** {where bullets will appear}
**Style:** {fascination / benefit / proof / hybrid}
**Total Bullets:** {count}

---

### Top Bullets (Killer Headlines)
{3-5 strongest bullets marked with a star}

### Bullet Section 1: {Theme}
- {bullet}
- {bullet}
- {bullet}

### Bullet Section 2: {Theme}
- {bullet}
- {bullet}
- {bullet}

### Bullet Section 3-N: ...

---

### Usage Notes
- **Best for headline conversion:** {bullet #}
- **Best for email subject line:** {bullet #}
- **Best for ad hook:** {bullet #}
- **Ordering recommendation:** {advice for placement}
```

---

## Condiciones de veto

- Nunca escriba una bala que revele la respuesta - la brecha de curiosidades es el mecanismo de venta
- Nunca use lenguaje vago (" resultados sorprendentes", "secretos poderosos") - la especificidad es obligatoria
- Nunca repetir la misma fórmula más de dos veces en un set
- Nunca escriben balas más cortas que 8 palabras - carecen de suficiente intriga
- Nunca incluye balas que prometen algo que el producto no entrega

---

## Criterios de finalización

- [] Contenido fuente minada para todo material de bala posible
- [ ] Pedido número de balas escritas usando fórmulas variadas
Cada bala crea una verdadera brecha de curiosidad
- Toros marcados y ordenados estratégicamente
- [ ] 3-5 balas asesinas identificadas para multi-use
- [ ] Sección temática organizada si es aplicable
- [ ] Notas de uso previstas cross-context aplicación
