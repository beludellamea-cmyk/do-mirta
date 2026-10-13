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
| `video-mirta.mp4` | **Falta agregarlo** (ver abajo). |

## Cómo incorporar el video de Doña Mirta

1. Dejá tu video con el nombre exacto **`video-mirta.mp4`** en esta misma carpeta (`ra`), junto a `index.html`.
   - En GitHub: carpeta `ra` → Add file → Upload files → arrastrá el video → Commit changes.
   - Si querés otro nombre, cambialo en `lente-dia.json` (`contenido.archivo`).
2. Formato recomendado: MP4 con video H.264 y audio AAC, de hasta 20 MB (GitHub no deja subir archivos de más de 25 MB desde el navegador).
3. Sirve horizontal, vertical o cuadrado. Con `"ajuste": "adaptar"` (lo normal) el video conserva su proporción y queda centrado en la ventana de la lámina. Otras opciones: `"cover"` llena toda la ventana recortando los bordes y `"contain"` la llena sin recortar.
4. Hasta que subas el video, al enfocar la lámina aparece un cartel que dice «Falta el video de Doña Mirta»: así sabés que el reconocimiento ya funciona.

## Cómo probarlo

1. Imprimí `lamina-mirta-A4.pdf` en A4, mejor a color y en papel mate (el brillante refleja la luz).
2. Abrí la página en el celular (tiene que estar en **https**, por ejemplo GitHub Pages).
3. Tocá **Abrir cámara** y permití el acceso.
4. Enfocá la lámina completa, con buena luz y sin reflejos. Mantenela a unos 25–40 cm.
5. Cuando la reconoce, el video aparece sobre la imagen de Doña Mirta. Si sale mudo, tocá **Activar sonido**.
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
| El video sale mudo | Tocá **Activar sonido** y subí el volumen del celular. |
| Aparece «Falta el video» | Subí `video-mirta.mp4` a esta carpeta. |
| Aparece un cartel «Error: …» | Copiá el texto exacto y pasalo junto con el modelo de celular y el navegador. |

## Qué se comprobó y qué no

- Se probó el reconocimiento con 40 fotos simuladas de la lámina (giradas, inclinadas, borrosas, con ruido, ocupando de 40 % a 88 % de la altura del cuadro): las 40 se reconocieron, con un error menor a 1,5 píxeles. En 6 cuadros sin la lámina no hubo falsos positivos.
- Se probó el flujo completo con una cámara simulada de celular: botones, permisos, aparición y desaparición del video, sonido.
- **No se probó con un celular real ni con una lámina impresa**: eso hay que verificarlo con papel y cámara.

Instructivo N.° 42 · IA al Colorado · Auxiliar en IA 2026 · Prof. Ariel Cóceres.
