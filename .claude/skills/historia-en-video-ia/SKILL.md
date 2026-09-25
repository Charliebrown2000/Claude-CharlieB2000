---
name: historia-en-video-ia
description: >-
  Produce videos narrados de historia y curiosidades (vida cotidiana en Roma, Egipto, la Edad Media, los Incas, etc.) generados casi enteramente con IA para YouTube, TikTok e Instagram Reels, al estilo de canales como "Te lo Cuento" o "El DoQmentalista": guion verificado con fuentes, desglose en escenas, prompts de imagen para Nano Banana y GPT Image, y prompts de movimiento para Veo/Kling. Usa esta skill siempre que el usuario pida ideas de videos de historia, misterio o curiosidades para redes sociales, quiera desarrollar el guion de un video narrado histórico, pida prompts de imagen o de video para una escena histórica o de época, o mencione formatos como "así vivían", "no sobrevivirías", protagonista sin rostro, canales de curiosidades/documentales con IA — incluso si no lo pide explícitamente como "skill" o no menciona estas palabras exactas.
---

# Historia en video con IA

Método para llevar una idea de video histórico desde el concepto hasta los prompts
de imagen y video listos para generar, trabajando **por partes y con aprobación del
usuario en cada etapa** — igual que se negocia un guion con un editor real, no todo
de una sola vez.

## Por qué importa cada paso

Este género vive de dos cosas que son fáciles de perder si se apura el proceso:
**precisión histórica** (la audiencia de este nicho detecta errores rápido y los
comenta) y **consistencia visual** (un protagonista que cambia de diseño entre
escena y escena rompe la inmersión). Los pasos de abajo existen para proteger esas
dos cosas, no como burocracia.

## Flujo de trabajo

### 0. Verificar los hechos antes de escribir una sola línea

Antes de proponer un guion, busca el tema (WebSearch/WebFetch) y confirma los datos
concretos: fechas, nombres, lugares, cifras. Este género mezcla hechos reales con
dramatización, así que:

- Todo dato verificable debe ser correcto y citable.
- Lo que es interpretación o teoría se dice como tal ("se cree que…", "los
  arqueólogos interpretan…"), nunca como hecho.
- Personas reales identificables (arqueólogos, figuras históricas con retrato
  conocido) se representan de espaldas, en silueta o con el rostro fuera de
  cuadro — nunca se les da un parecido literal generado por IA.

### 1. Definir formato y duración con el usuario

Pregunta si no está claro, pero el valor por defecto de este canal es:

- **Formato:** horizontal 16:9 (también el nativo de Veo, así que no hay que forzar nada).
- **Duración:** media, 5–8 minutos, salvo que el usuario pida un short/reel corto
  (45–60 s) — en ese caso baja la cantidad de escenas y sube el ritmo de corte.

### 2. Guion por bloques (estructura de "desafíos")

Divide la historia en bloques narrativos cortos, cada uno con un texto de
capítulo en pantalla (ej. "Primer desafío: encontrar dónde bañarse"). Estructura
típica para formato medio:

| Bloque | % del video | Contenido |
|---|---|---|
| Gancho | ~5% | Afirmación o pregunta fuerte que desmiente un mito o promete un dato sorprendente |
| Desarrollo (2–3 bloques) | ~70% | Cada bloque es un "desafío" o etapa de la vida cotidiana que se explora |
| Giro | ~15% | El dato que cambia la perspectiva, o por qué terminó esa costumbre |
| Cierre | ~10% | Frase de cierre corta + gancho hacia el siguiente video |

Presenta el guion en una tabla (bloque, tiempo, narración, qué se ve) y **espera
aprobación antes de pasar a las escenas** — es más barato corregir texto que
regenerar imágenes.

### 3. Desglose en escenas

Una escena por cada 15–25 segundos de narración en formato medio (o 4–8 s en
formato corto). Numera las escenas y anota, junto a cada una, si será:

- **Imagen fija animada** (Ken Burns: zoom/paneo lento) — la mayoría de las escenas.
- **Video generado** (Veo/Kling) — resérvalo para 2–3 momentos de mayor impacto
  emocional del video; es más caro y lento de producir que animar una imagen fija.

### 4. Prompts de imagen

Lee `references/prompting-imagenes.md` para las reglas de Nano Banana y GPT Image,
y el bloque de estilo visual de la casa (protagonista sin rostro + fondo pintado
detallado). Genera primero la escena más representativa, que el usuario apruebe,
y úsala como **imagen de referencia** para las demás escenas del mismo video —
así el personaje no cambia de diseño a mitad de historia.

### 5. Prompts de movimiento

Solo para las escenas marcadas como video generado en el paso 3. Lee
`references/prompting-movimiento.md` para las convenciones de Veo/Kling: un
movimiento de cámara por escena, 2–3 detalles de movimiento concretos, sonido
ambiente, sin diálogo ni música.

### 6. Cierre de producción

Al final del video (o cuando el usuario lo pida), resume en una tabla: qué
escenas quedaron como imagen fija, cuáles como video generado, y qué falta
(voz narrada, música, subtítulos, edición) — eso queda fuera de esta skill, se
hace en las herramientas de audio/edición que use el usuario.

## Canal del usuario

**"La Edad Media sin filtro"** — nombre confirmado por el usuario el
2026-09-25. Primer proyecto activo: vida cotidiana en la Edad Media, con el
piloto "Así se bañaba la gente en la Edad Media (y no era lo que crees)" ya en
producción (ver el guion de 15 escenas que el usuario tiene en local). Si el
usuario abre un proyecto de otra época (Roma, Egipto, Incas), pregunta si va
en este mismo canal o si es uno nuevo — no asumas.

## Canal de referencia

[Te lo Cuento Roma](https://www.youtube.com/@TeloCuentoRoma) es la referencia
visual y narrativa oficial de este proyecto: guion de vida cotidiana en la
antigüedad, títulos que comparan con hoy, y la ilustración de tinta suelta +
acuarela plana descrita abajo. El canal en sí es inaccesible desde este
entorno (YouTube bloqueado), así que el estilo quedó **extraído y validado a
mano contra capturas de pantalla que el usuario compartió** el 2026-09-25, no
contra un scraping del canal. Si el usuario comparte más capturas o cambia de
referencia, actualiza el bloque de estilo de abajo y
`references/prompting-imagenes.md` en vez de mantener dos fuentes de verdad.

## Identidad visual de la casa (adaptable por proyecto)

El formato por defecto es una **ilustración de tinta suelta + acuarela plana**
(línea de pluma visible, coloreado plano y desaturado, viñeta suave de papel
envejecido) aplicada **por igual al personaje y al fondo** — no son dos
técnicas distintas. El protagonista es un círculo simple con contorno fino de
tinta, casi siempre sin rasgos o con puntos simples como ojos, sobre un fondo
del mismo trazo que puede tener mucho contenido (edificios, objetos, gente)
pero sin textura fotorrealista. El contraste real está en la complejidad del
contenido, no en la calidad del render. Ver el bloque de estilo completo y
qué evitar en `references/prompting-imagenes.md`.

Esto se adapta a cualquier época cambiando solo la paleta de color, la
vestimenta y la arquitectura del fondo (ver la tabla de ejemplos en
`references/prompting-imagenes.md`). Si el proyecto pide otro estilo (por
ejemplo, uno más cinematográfico y oscuro tipo documental de misterio en vez de
concept art de vida cotidiana), pregunta al usuario y define un bloque de
estilo distinto antes de generar prompts — no asumas que todos los proyectos
usan el mismo look.
