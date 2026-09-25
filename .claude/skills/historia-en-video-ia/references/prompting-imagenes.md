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

Reemplaza los corchetes según la época/proyecto. Esta es la plantilla por
defecto de "historia-en-video-ia" (protagonista sin rostro + fondo detallado):

**Para Nano Banana:**
```
Style: hand-painted digital concept art, richly detailed [ERA/SETTING] background
with [COLOR PALETTE] tones and soft painterly brushwork. The protagonist is a
minimalist faceless character: a plain white circle head with a thin black
outline and no facial features (only simple drawn eyebrows and mouth if showing
strong emotion), simple stick-figure body in [PERIOD CLOTHING]. Strong contrast
between the simple character and the richly detailed environment. Horizontal
16:9 format.
```

**Para GPT Image** (idéntico, sin la última frase; el 16:9 va en el parámetro `size`):
```
Style: hand-painted digital concept art, richly detailed [ERA/SETTING] background
with [COLOR PALETTE] tones and soft painterly brushwork. The protagonist is a
minimalist faceless character: a plain white circle head with a thin black
outline and no facial features (only simple drawn eyebrows and mouth if showing
strong emotion), simple stick-figure body in [PERIOD CLOTHING]. Strong contrast
between the simple character and the richly detailed environment.
```

### Ejemplos de sustitución por época

| Proyecto | [ERA/SETTING] | [COLOR PALETTE] | [PERIOD CLOTHING] |
|---|---|---|---|
| Edad Media | medieval town, timber-framed houses, public bathhouse | warm sepia and ochre | a basic medieval tunic |
| Antigua Roma | Roman forum, marketplace, villa interior | warm amber and terracotta | a simple toga or tunic |
| Egipto | Nile riverbank, mudbrick village, temple courtyard | warm gold and sandstone | linen kilt or dress |
| Imperio Inca | Andean stone terraces, Cusco streets, adobe village | earthy red-brown and turquoise accents | a simple unku tunic |

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
