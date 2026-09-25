# Prompts de movimiento (imagen a video): Veo / Kling

Estos prompts se usan **solo** para las escenas marcadas en el paso 3 del flujo
como "video generado" — el resto se anima con Ken Burns (zoom/paneo lento) sobre
la imagen fija, que es más barato y suficiente para la mayoría de escenas.

## Principios

1. **No describas otra vez la imagen.** El modelo ya la ve (image-to-video); el
   prompt dice únicamente qué se mueve y cómo se mueve la cámara.
2. **Un solo movimiento de cámara, en su propia frase.** Ej. *"The camera slowly
   pushes in."* Si no lo indicas, el modelo elige uno por su cuenta y puede no
   coincidir con lo que quieres.
3. **2–3 detalles de movimiento concretos, con verbos de fuerza** (sway, drift,
   flicker, ripple, burst) en vez de movimientos vagos — lo vago produce
   resultados "flotantes" y poco realistas.
4. **Movimiento lento por defecto.** En este género da tensión y además reduce
   las deformaciones que genera el movimiento rápido.
5. **Solo sonido ambiente.** La narración y la música se añaden después en la
   edición: pide *"no dialogue, no music"*.
6. **Formato:** Veo genera en 16:9 por defecto — no hace falta forzar nada en el
   texto para el formato horizontal de este canal (a diferencia de un short
   vertical, donde sí habría que pedir el parámetro de formato vertical aparte).

## Cierre fijo (se agrega al final de cada prompt)

```
Keep the exact visual style, colors and detail of the source image. Slow,
subtle, realistic motion. No text, no dialogue, no music.
```

## Plantilla

```
The camera [UN SOLO MOVIMIENTO, ej. "slowly pushes in toward X"]. [DETALLE DE
MOVIMIENTO 1]. [DETALLE DE MOVIMIENTO 2, opcional]. Ambient sound: [SONIDOS DE
AMBIENTE]. [CIERRE FIJO]
```

**Ejemplo aplicado** (protagonista entrando a una casa de baños medieval):
```
The camera slowly pushes in through the doorway. Steam drifts and swirls around
the protagonist as they step inside. Warm light flickers softly on the wooden
tubs in the background. Ambient sound: water dripping, low murmurs, a wooden
door creaking shut. Keep the exact visual style, colors and detail of the
source image. Slow, subtle, realistic motion. No text, no dialogue, no music.
```

## Solución de problemas comunes

- **Caras o manos deformadas:** baja la intensidad del movimiento — agrega
  *"almost still, only the light and steam move"*.
- **Un objeto cambia de forma entre fotogramas:** añade *"[el objeto] remains
  perfectly still and unchanged"*.
- **La cámara hace un movimiento distinto al pedido:** repite el movimiento de
  cámara al inicio y al final del prompt.
- **Escenas de mucho impacto (giros, revelaciones):** genera 2–3 variantes y
  quédate con la mejor — son las que más vale la pena regenerar varias veces.
