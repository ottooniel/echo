# build&play: juego arcade en 32 KB

Reto online de Open2 / Build & Pitch. Hay que hacer el juego arcade más cool y difícil, escrito a mano, sin librerías y sin assets. Gana el más votado ($50 USD).

Fuente de las reglas: https://www.open2.io/build-and-pitch/play

## Fechas (hora de Guatemala)

| Fecha | Qué pasa |
|---|---|
| 4 nov | Abren los envíos |
| **13 nov, 23:59** | **Cierran los envíos (fecha límite dura)** |
| 14 nov | Abre la votación |
| 20 nov, 23:59 | Cierra la votación |
| 21 nov | Ganador en Build & Pitch |

Envío: https://app.open2.io/play (requiere cuenta de Open2). Un juego por cuenta.

## Reglas duras (no negociables)

1. **32 KB en total, sin comprimir.** Es todo lo que el navegador descarga para jugar. Cuenta el build final, así que se puede minificar. Meta interna: **máximo 32.000 bytes** para tener margen.
2. **Cero librerías, frameworks o motores.** Ni Phaser, ni Three.js, ni React, ni nada de npm en el runtime. Solo lo que trae el navegador (Canvas 2D, Web Audio, DOM).
3. **Cero assets.** Nada de imágenes, audio ni fuentes. Todo se dibuja con código y todo suena con código.
   - Sin `@font-face`, sin Google Fonts. Usar solo fuentes del sistema (`monospace`, `sans-serif`).
   - Sin favicon externo: usar `<link rel="icon" href="data:,">`.
   - Sin sprites ni SVG externos. Los gráficos se dibujan con primitivas de canvas.
   - Sonido con osciladores de Web Audio (`OscillatorNode`, `GainNode`, ruido generado en un buffer).
4. **Repo público nuevo en GitHub, creado durante el reto.** Más un link para jugarlo (GitHub Pages, Vercel o itch.io).
5. **Original.** Nada de clones ni personajes de otros juegos.
6. **Un juego por persona.**

## Stack y estructura

- Un único `index.html` con `<style>` y `<script>` inline. Sin build, sin dependencias. Es lo más fácil de pesar y de publicar en GitHub Pages.
- Si el código crece, se puede separar en `index.html`, `style.css` y `game.js`, pero el total sigue siendo el que cuenta.
- JavaScript vanilla, `<canvas>` 2D, `requestAnimationFrame` con timestep fijo, Web Audio para sonido.
- Controles que funcionen en teclado y en táctil (mucha gente votará desde el celular).

## Presupuesto de bytes (referencia)

| Parte | Meta |
|---|---|
| HTML + CSS | 1.5 KB |
| Núcleo (loop, input, colisiones, partículas) | 8 KB |
| Lógica del juego y dificultad | 12 KB |
| Audio (sintetizador de efectos y música) | 4 KB |
| Margen | 4.5 KB |

## Medir el peso (obligatorio después de cada cambio)

PowerShell, desde la raíz del repo:

```powershell
(Get-ChildItem -Recurse -File -Include *.html,*.css,*.js | Where-Object { $_.FullName -notmatch '\\(node_modules|\.git)\\' } | Measure-Object Length -Sum).Sum
```

El resultado son bytes. Debe ser menor que 32768. Si pasa de 32000, avisar y recortar antes de seguir agregando cosas.

## Concepto del juego

- **Nombre:** ECHO
- **Idea en una línea:** Arcade de supervivencia en una arena: cada ronda graba tu recorrido y lo convierte en un eco que repite ese camino en las rondas siguientes.
- **Controles:** En ratón, el punto sigue al puntero con velocidad máxima limitada. En táctil, un joystick flotante: el arrastre desde el contacto inicial define el movimiento para que el dedo no tape el punto. Alternativa de teclado: flechas o WASD. Arena lógica fija, igual en celular y escritorio.
- **Qué lo hace difícil:** No hay enemigos extra. Solo se acumulan ecos (un path por ronda completada) y orbes (`3 + floor(ronda/2)`). La ronda 1 no tiene ecos y enseña sola; desde la 3 se siente tensa; alrededor de la 8, casi imposible.
- **Qué lo hace "cool" (identidad visual y sonora):** Paleta negro / blanco / cuatro neones (un color por eco, opacidad por antigüedad pero nunca bajo 0.5) / amarillo en orbes. Estela, bloom (`shadowBlur`), orbes que pulsan, partículas, screen shake al morir, flash al completar ronda. Sonido sintético: blip ascendente al recoger, arpegio al completar ronda, ráfaga de ruido al morir; drones graves por eco si caben en el presupuesto. Texto solo `monospace` del sistema, dibujado en canvas.
- **Condición de derrota / puntaje:** Tocar un eco (después de 1.5 s de gracia) o salir de la arena. Puntaje: rondas completadas, orbes como desempate. Mejor marca en `localStorage` dentro de `try/catch`.

## Cómo debe trabajar el agente

- **Planear antes de programar.** Para cada tarea nueva, proponer un plan corto y esperar aprobación antes de escribir código.
- **Pasos pequeños.** Un cambio por vez, probado en el navegador antes del siguiente.
- **El peso manda.** Después de cada cambio, reportar el tamaño total en bytes. Preferir código compacto y reutilizable sobre código largo.
- **Nada de dependencias.** No instalar paquetes ni agregar `<script src>` o `<link>` externos. Si algo parece necesitar una librería, escribir la versión mínima a mano.
- **Nada de recursos externos.** Ninguna petición de red durante el juego (fuentes, CDN, analytics).
- **Dificultad progresiva.** El juego debe ser difícil pero justo: la dificultad sube de forma gradual y la muerte debe sentirse como culpa del jugador.
- **Game feel.** Priorizar screen shake, partículas, flashes y sonido con síntesis. Es lo que más hace ver cool a un juego pequeño.
- **Reportar ambigüedades.** Si una regla del reto no queda clara, decirlo en lugar de asumir.
- **Commits frecuentes y descriptivos** en español.

## Checklist de entrega (antes del 13 nov, 23:59)

- [ ] Repo público creado durante el reto
- [ ] Juego publicado y jugable en una URL (GitHub Pages / Vercel / itch.io)
- [ ] Peso total menor que 32768 bytes (medido sobre el build final)
- [ ] Sin librerías, sin imágenes, sin audio, sin fuentes cargadas
- [ ] Probado en escritorio y en celular
- [ ] Enviado en https://app.open2.io/play con el link del repo y el link para jugar
