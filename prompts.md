# Biblioteca de prompts — Laboratorio 06

## Plantilla de Registro
**Herramienta:** (Claude / ChatGPT / Gemini / Copilot)
**Prompt:**
> (Escribe aquí el prompt)
**Resultado (resumen):** ...
**Observaciones:** ...

### Comparación y diferencias observadas (Prompt vago vs. Prompt estructurado)

1. **Extensión y Estructura:**
   * **Prompt vago:** Generó un texto genérico, sin límite claro de longitud ni división de secciones definida.
   * **Prompt estructurado:** Cumplió estrictamente con la estructura solicitada (asunto, saludo, máximo 2 párrafos de cuerpo y despedida) sin exceder la restricción de 120 palabras[cite: 1].

2. **Tono y Adaptación de Rol:**
   * **Prompt vago:** Usó un tono neutro y plano, como una plantilla genérica[cite: 1].
   * **Prompt estructurado:** Asumió el rol de estudiante universitario con un tono formal, respetuoso y adecuado para dirigirse a un docente[cite: 1].

3. **Precisión y Contexto:**
   * **Prompt vago:** No especificó el nombre del curso, la razón ni cuántos días se solicitaban de prórroga[cite: 1].
   * **Prompt estructurado:** Incluyó datos exactos como el curso (*Diseño de Interfaces*), la justificación (integrantes del equipo enfermos) y propuso una fecha concreta con los 3 días de plazo[cite: 1].
   

   ---

## FASE 2 — Zero-shot y few-pero

### Paso 2.1 — Clasificación con zero-pero
**Herramienta:** ChatGPT / Claude / Gemini / Copilot
**Prompt:**
> Clasifica cada comentario como POSITIVO, NEGATIVO o NEUTRO.
> 1. "La app se cierra cada vez que intento pagar."
> 2. "Llegó el pedido, nada que destacar."
> 3. "Me encantó lo rápido que cargan las pantallas."
> 4. "Está bien, aunque el botón de ayuda es difícil de encontrar."

**Resultado (resumen):**
1. NEGATIVO
2. NEUTRO
3. POSITIVO
4. NEUTRO

---

### Observaciones — Análisis de la respuesta (Few-shot)

* **¿Respetó el formato?** 
  Sí. A diferencia de la prueba zero-shot que solo entregó etiquetas sueltas, la técnica few-shot logró que la IA respondiera exactamente con la estructura solicitada: `Categoría | Tema`.

* **¿Identificó el tema?** 
  Sí. La IA analizó el contexto de cada texto y extrajo el tema principal (asociando el primer comentario a *pago / funcionamiento* y el segundo a *interfaz / usabilidad*)[cite: 1].

* **¿Usó la categoría MIXTO?** 
  Sí. Gracias a los ejemplos previos, la IA aprendió el criterio de clasificación y asignó correctamente la etiqueta `MIXTO` al comentario que expresaba una opinión tanto positiva como negativa[cite: 1].
  

  Resume el texto delimitado por <texto></texto> en 3 viñetas de máximo 20 palabras cada una.
Luego escribe una sola oración con la idea principal.

<texto>
(El despertar de la naturaleza en la primavera es uno de los espectáculos más hermosos y fascinantes que podemos presenciar en nuestro planeta. Después del frío invierno, donde muchos árboles pierden sus hojas y los animales se resguardan en sus madrigueras, la tierra comienza a transformarse de manera radical y silenciosa. Los rayos del sol se vuelven más cálidos y duraderos, derritiendo los últimos restos de nieve en las cimas de las montañas y calentando la superficie del suelo.
Las primeras señales de vida aparecen en los campos y en los jardines urbanos. Pequeños brotes verdes rompen la dura corteza de la tierra, buscando ansiosamente la luz del sol. Las ramas de los árboles, que parecían inertes y secas durante los meses anteriores, se llenan de yemas diminutas que pronto se convierten en hojas tiernas y flores coloridas. El aire se llena de fragancias dulces y frescas, mientras el viento suave mece las plantas con una delicadeza única.
Los animales también participan en esta gran fiesta de la vida. Las aves regresan de sus migraciones hacia el sur, cantando alegres melodías al amanecer para reclamar sus territorios y encontrar pareja. Las abejas y otros insectos revolotean de flor en flor, cumpliendo su labor esencial en la polinización. Todo el ecosistema se sincroniza en un equilibrio perfecto que nos recuerda la resiliencia y la capacidad de renovación del mundo natural. Observar este proceso nos ofrece una profunda sensación de paz y esperanza para el futuro.
Si necesitas que el texto trate sobre otro tema específico (como la tecnología, el espacio o un relato de ficción), dime cuál prefieres y lo reescribiré con mucho gusto.)
</texto>


---

## FASE 5 — Evaluación e iteración de prompts

### Paso 5.1 — Rúbrica de evaluación

| Criterio   | Descripción                                   | Puntaje (1-5) |
| ---------- | --------------------------------------------- | :-----------: |
| Relevancia | Responde exactamente a lo solicitado          |       5       |
| Precisión  | La información es objetiva y sin errores       |       5       |
| Formato    | Respeta la estructura y limites de extensión  |       5       |
| Tono       | Es adecuado para el público objetivo           |       5       |

---

### Paso 5.2 — Iteraciones (Mejora progresiva de un prompt)

| Versión | Cambio realizado en el prompt                     | Puntaje total |
| ------- | ------------------------------------------------- | :-----------: |
| v1      | Prompt inicial vago y sin estructura              |     12/20     |
| v2      | Se agregó rol del estudiante y contexto del curso |     16/20     |
| v3      | Se especificó formato (tabla/JSON) y límite de palabras | 20/20 |

**Observaciones:**
La evaluación mediante rúbrica permite identificar fallas específicas en la respuesta. Iterar el prompt agregando restricciones y contexto de forma gradual eleva la calidad del resultado de 12 a 20 puntos.


---

## FASE 6 — Biblioteca de prompts y publicación

### Plantillas Reutilizables

#### 1. Redacción de Correo Formal
> Actúa como {{rol}}.
> Contexto: {{situación}}.
> Redacta un correo dirigido a {{destinatario}} para {{objetivo}}.
> Formato: asunto, saludo, cuerpo en máximo {{n}} párrafos y despedida.
> Restricciones: máximo {{palabras}} palabras, tono {{tono}}.

#### 2. Resumen Técnico con Delimitadores
> Actúa como un experto en {{área}}.
> Resume el texto delimitado por <texto></texto> en {{cantidad_puntos}} viñetas de máximo {{palabras_por_punto}} palabras cada una.
> Extrae la idea central en una oración.
>
> <texto>
> {{texto_a_resumir}}
> </texto>

#### 3. Extracción de Datos Estructurados
> Extrae los siguientes campos del texto adjunto: {{campos_a_extraer}}.
> Formato de salida: Genera una tabla Markdown seguida de un bloque JSON válido.
> Si algún campo no está disponible, asigna el valor "no especificado".
>
> Texto:
> """
> {{texto_fuente}}
> """

---

## CONCLUSIONES GENERALES

1. **Estructura y Precisión:** Incluir los 5 componentes clave (rol, contexto, tarea, formato y restricciones) elimina ambigüedades y genera respuestas útiles al primer intento.
2. **Estrategias Avanzadas:** El uso de delimitadores (`<texto>`, `"""`), ejemplos (*few-shot*) y la instrucción de *pensar paso a paso* permiten extraer datos estructurados en JSON y realizar cálculos sin errores.
3. **Optimización Progresiva:** La evaluación iterativa de prompts mediante rúbricas permite refinar las instrucciones hasta obtener resultados con la calidad requerida en entornos académicos y profesionales.