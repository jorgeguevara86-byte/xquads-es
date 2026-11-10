---
task: createHooks()
responsavel: "@hormozi-hooks"
responsavel_type: Agent
atomic_layer: Task
elicit: true

Entrada:
  - campo: topic
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true
  - campo: platform
    tipo: string
    origem: "Entrada del usuario" 
    obrigatorio: true

Saida:
  - campo: hookPackage
    tipo: string
    destino: Console
    persistido: false

Checklist:
  - "[ ] Ganchos escritos en al menos 4 categorías" 
  - "[ ] Respetaciones de las limitaciones de la plataforma" 
  - "[ ] Todos los ganchos marcados en 3 dimensiones" 
---

# Task: Create Hooks

** ID de usuario: **HORMOZI-005
**Version:** 1.0.0
**Command:** `*create-hooks`
**Agente:** Hormozi Hooks (hormozi-hooks)
**Purpose:** Crear attention-grabbing ganchos para contenido, anuncios y material de ventas.

---

## Inputs

| Campo | Tipo | Fuente | Requerido | Validación |
|-------|------|--------|----------|------------|
← Tema TENED TENIDO TENIDO ANTERIOR ANTERIOR SI TENIDO Asunto de los ganchos TENIDO
Silencio, plataforma, instagram, facebook, linkedin, email, ad latitud, infórmate, infórmate, ayud, ayudamiento, ayudamiento, ayudamiento, ayudamiento
Silenciosamente en la audiencia Silencio Silencio intuitiva Silencio Silencio Quién los ganchos deben detener Silencio
| content_goal Silencio enum Silencio Usuario prompt Silencio Sí Silencio educar, vender, entretener, build-authority, generate-leads |
TENCIÓN TENEDAD NÚMERO TENIDO NO TENIDO RESPUESTO ANTERIOR Por defecto 20 ganchos TENIDO

---

## Preconditions

- Plataforma seleccionada con comprensión de las limitaciones de formato
- Audiencia definida con suficiente especificidad para escribir para ellos

---

## Fases de Ejecución

### Phase 1: Hook Category Mapping
1. Seleccione de las 7 categorías de ganchos (Marco Hormozi):
   *Contrarian:* Reto a una creencia comúnmente sostenida
   **Curiosidad Gap:** Crear una brecha de información que deben cerrar
   - **Result/Proof:** Liderazgo con un resultado específico e impresionante
   Abrir con un momento dramático de una historia real
   - **Pregunta:** Hacer una pregunta que obligue self-reflection
   **Reclamación de la familia:** Hacer una declaración específica y provocativa
   - **Pattern Interrupt:** Rompe el patrón de desplazamiento esperado con algo inesperado
2. Asignar ganchos a través de categorías (al menos 3 de cada categoría utilizada)
3. Categoría de partidos a normas de plataforma:
   - YouTube: Los ganchos de Curiosidad y Resultado dominan
   - TikTok: Interrupción de Patrón y Contraria realizan lo mejor
   - LinkedIn: Ganchos de Reclamación Bold y de Resultado impulsan el compromiso
   - Temas de correo electrónico: Ganancia de gachas Curiosidad y Ganancia de ganchos Pregunta
   - Anuncios: Ganchos de Resultado y Reclamación Bold paran el pergamino

## Fase 2: Escribir gancho
1. Escriba cada gancho siguiente restricciones de la plataforma:
   - YouTube: Bajo 10 palabras para miniatura, bajo 15 segundos hablados
   - TikTok/Reels: Bajo 3 segundos (8-12 palabras max)
   - LinkedIn: Primera línea antes de "ver más" (bajo 150 chars)
   - Correo electrónico: Bajo 50 caracteres para línea de asunto
   - Anuncios: Bajo 125 caracteres para gancho de texto primario
2. Aplicar la regla de especificidad: reemplazar palabras vagas con números, nombres o detalles
3. Aplicar la prueba "¿debería dejar de desplazarme?" a cada gancho
4. Crear 2-3 variaciones por idea de gancho núcleo (ángulos reframados)

### Fase 3: Scoring and Packaging
1. Puntuación de cada gancho en 3 dimensiones (1-5):
   - ¿Alguien dejaría de desplazarse?
   - Relevancia: ¿Es relevante para el público objetivo?
   - Payoff Potential: ¿Puede el contenido cumplir con la promesa de este gancho?
2. Rancho por puntuación total
3. Grupo en "listo para usar" y "necesidades de contenido construidas alrededor de él"
4. Sugerir ideas de contenido para los 5 ganchos superiores
5. Proporción de A/B pares de pruebas

---

## Formato de salida

```markdown
## Hook Package: {Topic}

**Platform:** {platform}
**Audience:** {audience}
**Total Hooks:** {count}

---

### Top 10 Hooks (Ranked)

| Rank | Hook | Category | Stop | Relevance | Payoff | Total |
|------|------|----------|------|-----------|--------|-------|

### All Hooks by Category

#### Contrarian
1. {hook}
2. {hook}

#### Curiosity Gap
1. {hook}
2. {hook}

#### Result/Proof
...

### Content Ideas for Top 5
| Hook | Content Idea | Format |
|------|-------------|--------|

### A/B Testing Pairs
| Pair | Hook A | Hook B | What We're Testing |
|------|--------|--------|-------------------|
```

---

## Condiciones de veto

- NUNCA escribe ganchos que el contenido no puede entregar en - clickbait destruye confianza
- NUNCA escribe ganchos vagos ("Esto cambió todo") - la especificidad es obligatoria
- Nunca ignore las restricciones de la plataforma - un gancho de YouTube difiere de un gancho TikTok
- Nunca enviar ganchos sin puntuación - ganchos sin rascar son inutilizables
- Nunca use la misma fórmula para más de 3 ganchos consecutivos

---

## Criterios de finalización

- [ ] ganchos escritos en al menos 4 categorías
- [ ] Respetaciones de las restricciones de la plataforma
- Todos los ganchos anotados en 3 dimensiones
- [ ] Top 10 clasificado con racional
[ ] Contenido de ideas proporcionados para el top 5
- [ ] A/B pares de pruebas sugeridos
- Regla de especificación aplicada a cada gancho
