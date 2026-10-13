# Vereda de El Colorado: Doña Mirta y Don Ramón

Página lista para publicar: `index.html` (un solo archivo; three.js y el SDK de ElevenLabs se cargan por CDN).
La página individual de Mirta (`../index.html`) queda intacta.

## Qué es
Una vereda de El Colorado, Formosa, al atardecer: sillas, plantas, lapacho y una mesa con tereré. Doña Mirta (curiosa y exagerada) y Don Ramón (tranquilo, bromista, escéptico, pero que también quiere enterarse de todo) te escuchan y conversan entre ellos. Todo el barrio y sus anécdotas son ficticios.

## Agentes de ElevenLabs
| Personaje | Agent ID | Voz |
|---|---|---|
| Doña Mirta | `agent_6601m4h8e93nf5ptap3xaxs29bke` | `m7yTemJqdIqrcNleANfX` (sin cambios) |
| Don Ramón | `agent_3201m4v9b5kcfzzvxn7gxw1b3epq` | `htFfPSZGJwjBv1CL0aMD` (Antonio, velocidad 0.88) |

Ambos agentes son públicos (sin autenticación). Para probar otros: `?mirta=AGENT_ID&ramon=AGENT_ID`.

## Cómo respeta los turnos
- Se abren dos sesiones de voz, pero **solo se escucha a quien le toca hablar**. Si el otro habla solo (por ejemplo, el «¿estás ahí todavía?» que ElevenLabs dispara tras unos segundos de silencio), se lo silencia y no cuenta como turno. Esos avisos, además, ya no se confunden con tu voz.
- Cuando uno termina de hablar y su audio dejó de sonar, la página le pasa lo que dijo al otro con `sendUserMessage` y recién ahí contesta el otro. Si algo todavía suena, espera.
- Después del saludo conversan entre ellos unas rondas (`RONDAS_MAX = 4`, editable al inicio del script) y le dejan la palabra al visitante.
- Tu micrófono se abre solo cuando ninguno habla, y se cierra apenas empieza a hablar alguno. Si hablás mientras uno habla, tocá «Quiero hablar» para interrumpirlo.
- Lo que le decís a uno se lo cuenta la página al otro en su próximo turno. No se usan actualizaciones de contexto mientras alguien habla, porque cortaban la frase.
- Recomendación: usá auriculares. Sin auriculares, el micrófono puede captar a los personajes por el parlante.

## Historia: «La camioneta misteriosa»
Botón «Historia» (siete momentos). Mirta ve una camioneta frente a la casa de Eusebio e imagina una gran novedad; Ramón propone explicaciones cotidianas; al final bajan un ventilador. Con voz en vivo los agentes improvisan siguiendo una indicación de dirección por momento. Sin créditos o con `?sinvoz` corre una versión con voz del navegador.

## Uso
1. Publicá esta carpeta (`index.html`) en cualquier hosting estático con HTTPS (el micrófono lo exige).
2. Abrila, tocá «Empezar» y aceptá el micrófono.
3. Usá auriculares: si no, cada personaje puede escuchar al otro por los parlantes.
4. También podés escribir en el panel derecho.

## Limitaciones
- Las habilidades «Humano digitales» y «Escenario multiagente 2.0» no estaban disponibles en la sesión; se siguió el instructivo 42 a mano.
- La voz de Ramón es una voz del espacio de trabajo (Antonio, de timbre algo joven). Se puede cambiar por una más grave en ElevenLabs.
- La conversación en vivo con voces reales no pudo probarse desde el entorno de desarrollo (sin créditos): se probó la escena 3D, la historia sin voz y la lógica de turnos con un SDK simulado.
