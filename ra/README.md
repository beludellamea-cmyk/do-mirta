# Lente DIA · Doña Mirta (Paso 3 del Instructivo 42)

Realidad aumentada con una lámina impresa: al enfocarla con el celular, aparece el video de Doña Mirta hablando encima de la imagen.
**Personaje ficticio creado con inteligencia artificial.** Todo el barrio y sus anécdotas son inventados.

## Archivos

| Archivo | Para qué sirve |
|---|---|
| `index.html` | La Lente DIA: cámara, reconocimiento de la lámina y video. Es un solo archivo, sin librerías externas. |
| `lente-dia.json` | Proyecto: lámina, textos, video, región donde aparece, botones y ajustes. |
| `lamina-mirta-A4.png` | Lámina para imprimir (A4, 2480 × 3508 px, 300 ppp). |
| `lamina-mirta-A4.pdf` | La misma lámina en PDF A4. |
| `marcador.jpg` | La misma lámina en menor tamaño: es lo que la página usa para reconocerla. |
| `video-mirta.mp4` | Video de Doña Mirta hablando (MP4 H.264 + AAC, 38,7 s, con su audio original). |

## El video

`video-mirta.mp4` ya está en esta carpeta y se conecta en `lente-dia.json` (`contenido.archivo`). Para cambiarlo, reemplazá el archivo (o el nombre en el JSON).

- Formato: MP4 con video H.264 y audio AAC. Evitá HEVC/H.265 (el formato por defecto de algunos celulares): muchos navegadores no lo reproducen.
- Con `"ajuste": "adaptar"` (lo normal) el video conserva su proporción y queda centrado sobre la ilustración de la lámina. Otras opciones: `"cover"` llena toda la ventana recortando los bordes y `"contain"` la llena sin recortar.
- El sonido empieza apagado porque los navegadores no permiten reproducir con sonido sin un toque. Tocá **Activar sonido** (o **Reproducir video**) para escuchar a Doña Mirta con su voz original.
- Si el navegador bloquea la reproducción (por ejemplo, un iPhone con ahorro de batería), aparece el botón **Reproducir video**.

## Cómo probarlo

1. Imprimí `lamina-mirta-A4.pdf` en A4, mejor a color y en papel mate (el brillante refleja la luz).
2. Abrí la página en el celular (tiene que estar en **https**, por ejemplo GitHub Pages).
3. Tocá **Abrir cámara** y permití el acceso.
4. Enfocá la lámina completa, con buena luz y sin reflejos. Mantenela a unos 25–40 cm.
5. Cuando la reconoce, el video aparece sobre la imagen de Doña Mirta. Si sale mudo, tocá **Activar sonido**. Si no arranca, tocá **Reproducir video**.
6. Para grabar una demostración, usá otro dispositivo y filmá el celular enfocando la lámina.

Para ver datos técnicos (cuadros por segundo, puntos reconocidos), agregá `?debug` al final de la dirección.

## Cómo está hecha la lámina

Funciona como marcador porque tiene mucho detalle y contraste: una ilustración detallada de Doña Mirta, guardas de triángulos en los bordes y un fondo de flores, hojas, rombos y espirales repartidos sin repetirse. No tiene fondos lisos ni degradés. Incluye los textos «Doña Mirta», «IA al Colorado», «Enfocá con Lente DIA» y «Personaje ficticio creado con inteligencia artificial».

## Cómo funciona (para quien quiera mirar el código)

El reconocimiento está escrito en el propio `index.html`: detecta puntos de interés (FAST), les calcula descriptores binarios, los compara con los de la lámina y calcula la perspectiva con RANSAC. Con esa perspectiva coloca el video sobre la lámina. No usa servicios externos: la cámara se procesa dentro del celular y no se envía a ningún lado.

## Si algo falla

| Problema | Qué hacer |
|---|---|
| La cámara no abre | La página tiene que estar en https. Revisá el permiso de cámara en el candado de la barra de direcciones. |
| No reconoce la lámina | Más luz, sin reflejos, la lámina entera en pantalla y bien plana. Probá con papel mate. |
| El video sale mudo | Tocá **Activar sonido** y subí el volumen del celular (y fijate que el celular no esté en silencio). |
| El video no arranca | Tocá **Reproducir video**. |
| Aparece «Falta el video» o «no pudo reproducir» | Revisá que `video-mirta.mp4` esté en esta carpeta y sea H.264. |
| Aparece un cartel «Error: …» | Copiá el texto exacto y pasalo junto con el modelo de celular y el navegador. |

## Qué se comprobó y qué no

- Se probó el reconocimiento con 40 fotos simuladas de la lámina (giradas, inclinadas, borrosas, con ruido, ocupando de 40 % a 88 % de la altura del cuadro): las 40 se reconocieron, con un error menor a 1,5 píxeles. En 6 cuadros sin la lámina no hubo falsos positivos.
- Se probó el flujo completo con una cámara simulada de celular: botones, permisos, aparición y desaparición del video, sonido.
- **No se probó con un celular real ni con una lámina impresa**: eso hay que verificarlo con papel y cámara.

Instructivo N.° 42 · IA al Colorado · Auxiliar en IA 2026 · Prof. Ariel Cóceres.
