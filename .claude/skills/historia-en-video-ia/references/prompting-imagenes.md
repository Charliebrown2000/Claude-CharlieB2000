# Prompts de imagen: Nano Banana y GPT Image

## Principios que funcionan en ambos modelos

1. **Frases descriptivas, no listas de palabras sueltas.** Ambos modelos razonan
   la escena completa; descríbela como se la describirías a un director de
   fotografía, no como una lista de tags.
2. **Lo más importante va primero.** Los primeros detalles del prompt pesan más
   en el resultado final que los últimos.
3. **Lenguaje de fotografía/cine, no adjetivos vacíos.** "35mm lens, low-angle,
   golden hour side light" da mejor resultado que "epic, amazing, stunning".
4. **Pide en positivo.** "Empty street" funciona mejor que "street with no people".
5. **Consistencia por referencia, no por descripción repetida.** Genera la
   escena más representativa del video primero, apruébala, y adjúntala como
   imagen de referencia en el resto de prompts con una frase como *"keep this
   exact character design and art style"*. Repetir la descripción del personaje
   en cada prompt por separado no garantiza que salga igual dos veces.
6. **Personas reales identificables:** nunca pidas parecido literal. Descríbelas
   de espaldas, en silueta, con el rostro fuera de cuadro o iluminado a
   contraluz.

## Diferencia clave entre los dos modelos

| | Nano Banana (Gemini image) | GPT Image (gpt-image-1) |
|---|---|---|
| Aspecto/formato | Se pide en el texto del prompt: *"Horizontal 16:9 format."* | Se define como parámetro de la API (`size`), no en el texto — ej. `1536x1024` para horizontal. Omite la frase de formato del prompt. |
| Ediciones conversacionales | Muy bueno para pedir cambios puntuales sobre una imagen ya generada: *"make the lighting darker, keep everything else exactly the same"*. | También soporta edición, pero sé igual de explícito sobre qué mantener igual. |
| Texto en la imagen | Evítalo; ponlo en la edición de video, no generado por el modelo. | Igual — evita pedir texto renderizado si luego lo vas a editar aparte. |

## Bloque de estilo de la casa (plantilla)

**Validado contra referencia real de canal el 2026-09-25.** El primer intento de
este bloque describía dos técnicas distintas (fondo "pintado tipo concept art"
+ personaje "plano"), y al compararlo con capturas reales del estilo de
referencia quedó claro que es **una sola técnica aplicada por igual a personaje
y fondo**: ilustración de tinta suelta + acuarela plana, no pintura digital
cinematográfica. El contraste real está en la *complejidad del contenido*
(personaje simple vs. escena llena de objetos/gente), no en dos calidades de
render distintas. Si vuelves a ajustar el estilo con el usuario, actualiza este
bloque en vez de mantener las dos versiones.

Reemplaza los corchetes según la época/proyecto:

**Para Nano Banana:**
```
Style: hand-drawn ink and watercolor sketch illustration. Loose, slightly rough
ink linework with visible pen strokes, the same line quality on both the
character and the background — not clean vector lines, not painterly digital
rendering. Flat to lightly shaded watercolor-style coloring in a muted,
desaturated palette of [COLOR PALETTE], with soft even lighting and no strong
directional shadows. The background is rich in content and detail ([ERA/SETTING])
but drawn economically, without photorealistic texture; a soft vignette darkens
the edges like aged paper. The protagonist has a plain circle head with a thin
black ink outline and cream fill, either fully blank or with simple small dot
eyes and little to no mouth, a thin stick-figure body wearing [PERIOD CLOTHING]
as flat-colored clothing blocks with no shading detail. Distant background
characters are simplified further, sometimes drawn as faint outlines only.
Horizontal 16:9 format.
```

**Para GPT Image** (idéntico, sin la última frase; el 16:9 va en el parámetro `size`):
```
Style: hand-drawn ink and watercolor sketch illustration. Loose, slightly rough
ink linework with visible pen strokes, the same line quality on both the
character and the background — not clean vector lines, not painterly digital
rendering. Flat to lightly shaded watercolor-style coloring in a muted,
desaturated palette of [COLOR PALETTE], with soft even lighting and no strong
directional shadows. The background is rich in content and detail ([ERA/SETTING])
but drawn economically, without photorealistic texture; a soft vignette darkens
the edges like aged paper. The protagonist has a plain circle head with a thin
black ink outline and cream fill, either fully blank or with simple small dot
eyes and little to no mouth, a thin stick-figure body wearing [PERIOD CLOTHING]
as flat-colored clothing blocks with no shading detail. Distant background
characters are simplified further, sometimes drawn as faint outlines only.
```

### Qué evitar (aprendido de la comparación con la referencia)

- Pintura digital cinematográfica, con luz direccional fuerte y sombras marcadas.
- Textura fotorrealista de superficie (trama de tela, grano de piedra, textura de comida).
- Proporciones anatómicamente naturalistas.
- Describir el fondo y el personaje como si usaran dos técnicas distintas — es una sola.

### Ejemplos de sustitución por época

| Proyecto | [ERA/SETTING] | [COLOR PALETTE] | [PERIOD CLOTHING] |
|---|---|---|---|
| Edad Media | a medieval town with timber-framed houses and a public bathhouse | dusty tan, cream, aged parchment beige and warm grey-brown | a basic medieval tunic |
| Antigua Roma | a Roman forum, marketplace or military camp with tents | dusty tan, faded terracotta and warm grey-brown | a simple toga, tunic or Roman soldier's armor |
| Egipto | a Nile riverbank, mudbrick village or temple courtyard | dusty tan, cream and faded gold-sandstone | a linen kilt or dress |
| Imperio Inca | Andean stone terraces, Cusco streets or an adobe village | dusty tan, cream and muted red-brown with faint turquoise accents | a simple unku tunic |

## Cuando el proyecto pide otro estilo (no concept art de vida cotidiana)

Algunos proyectos (por ejemplo, una serie de misterio/documental oscuro en vez
de curiosidades de vida cotidiana) usan un estilo distinto: fotografía
cinematográfica realista en vez de ilustración pintada, sin el protagonista sin
rostro. En ese caso arma un bloque de estilo propio con el usuario antes de
generar prompts — el patrón es el mismo (una frase de estilo fija que se repite
al final de cada prompt), solo cambia el contenido del bloque. Ejemplo de un
proyecto de ese tipo:

```
Style: cinematic documentary still, [PERIOD/LOCATION], shot on 35mm film with
visible grain, low-key lighting, deep shadows, [COLOR GRADE] tones, dust
particles floating in the air, shallow depth of field. Horizontal 16:9 format.
```
