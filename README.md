# Doña Mirta — Charla desde la ventana

Humano digital de una vecina formoseña **ficticia** que conversa desde la ventana de su casa en el barrio imaginario El Lapacho. Basado en el instructivo «Cómo crear un humano digital con Claude (el caso San Martín)», del Proyecto DIA.

- **Voz y cerebro:** agente de ElevenLabs `agent_6601m4h8e93nf5ptap3xaxs29bke`, con base de conocimiento propia.
- **Cuerpo:** figura 3D hecha en código con Three.js 0.160: ruleros, anteojos de carey con cadenita, vestido floreado, mate, ventilador, plantas, cortina y lapacho.
- **Boca:** formas para A, E, I, O, U, M/B/P, F, L, K y S, que se mueven con la alineación letra por letra que manda ElevenLabs y con el volumen real de la voz.

## Publicar en GitHub Pages

1. En github.com: **+ → New repository**, por ejemplo `dona-mirta`, en **Public**.
2. **Add file → Upload files**: arrastrá `index.html` y `README.md`, y tocá **Commit changes**.
3. **Settings → Pages → Deploy from a branch**: rama `main`, carpeta `/ (root)` y **Save**.
4. Esperá uno o dos minutos. La dirección será `https://TU_USUARIO.github.io/dona-mirta/`.

> No funciona abriendo el archivo con doble clic (`file://`) ni como artifact de Claude: el navegador bloquea la conexión con ElevenLabs. Tiene que estar publicado en una dirección `https://`.

## Ajustes útiles

- **Otro agente sin tocar el código:** `index.html?agente=TU_ID`.
- **Boca adelantada o atrasada:** cambiá `LIP_OFFSET_MS` al principio del script. Si la boca se adelanta, subilo (por ejemplo, `80`); si se atrasa, bajalo (`-80`).
- **Modelo realista opcional:** subí `mirta.glb` junto al `index.html`. La página lo carga en lugar de la figura en código y mueve sus formas de boca si se llaman `viseme_aa`, `viseme_E`, `viseme_I`, `viseme_O`, `viseme_U`, `viseme_PP` o `viseme_FF`, más `eyeBlinkLeft` y `eyeBlinkRight` para parpadear.
- **Demostración sin conexión:** el botón «Escucharla sin conectarse» usa la voz del dispositivo y no gasta créditos. En Windows puede hacer falta instalar una voz en español.

## Seguridad y costos

- En ElevenLabs, el agente tiene que estar en modo público (pestaña **Security**, autenticación desactivada).
- Cada minuto de conversación consume créditos. Para limitar quién puede usarlo, agregá `TU_USUARIO.github.io` a la lista de dominios permitidos del agente.

## Consideraciones éticas

Doña Mirta es una recreación humorística y la página lo dice. Solo chismea de vecinos inventados, nunca de personas reales. Admite ser una IA si se lo preguntan, no pide datos personales y deriva con cariño a un adulto de confianza si alguien cuenta que está mal. La voz de quien habla viaja a ElevenLabs; quien prefiera puede escribirle en lugar de hablar.

## Lente DIA: Doña Mirta en realidad aumentada

- **Abrir el lente:** https://beludellamea-cmyk.github.io/do-mirta/ra/
- Imprimí la lámina desde el propio lente y permití la cámara.
- Al reconocer la lámina, el lente muestra **el mismo avatar 3D interactivo** de la página principal (no un MP4).
- Tocá **Hablar** para iniciar la conversación con el agente existente de ElevenLabs. Podés terminarla o abrir **Escribir** para mandar mensajes durante la charla.
- La versión 3D que muestra el lente se carga desde \`../index.html?modo=lente\` y utiliza mensajería entre marcos del mismo origen para sincronizar voz, estados y transcripciones.
- **Alternativa:** si el navegador no admite cámara + micrófono al mismo tiempo, o falla WebGL, usá el enlace **Conversar sin lente** y abrí la experiencia interactiva a pantalla completa.
- El navegador debe permitir acceso a cámara y micrófono sobre HTTPS; cada minuto conectado puede consumir créditos de ElevenLabs.

La configuración del lente vive en \`ra/lente-dia.json\`. La lámina y su marcador existente se mantienen sin cambios. El motor de seguimiento visual y el avatar 3D consumen recursos: se recomienda un celular moderno y buena iluminación.
