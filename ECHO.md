# ECHO — Sesión de Claude Code: auditoría, mejoras y tráiler

## Contexto
- **Juego:** ECHO, arcade de supervivencia. El recorrido de cada ronda se convierte en un "eco" que repite ese camino en todas las rondas siguientes. En NORMAL e INFIERNO el eco lo recorre de ida y vuelta sin parar (ping-pong); en FÁCIL lo recorre una vez y desaparece.
- **Modos:** FÁCIL (tecla `1`), NORMAL (tecla `2`, por defecto) e INFIERNO (tecla `3`), elegibles en el título. `Esc` vuelve al título.
- **Repo:** https://github.com/ottooniel/echo (público)
- **Juego jugable (GitHub Pages):** https://ottooniel.github.io/echo/
- **Hecho con:** Cursor. Pesa menos de 32 KB (30.380 bytes al congelarlo), sin librerías y sin assets externos.
- **Reto:** Open2 — Build & Pitch. **Cierre de envíos: 13 nov 2026.**
- **Objetivo final:** publicar en LinkedIn el juego + un tráiler hecho con Claude + Higgsfield (MCP).

## Reglas de la sesión
1. No reescribas el juego. Audita y mejora de forma incremental.
2. Antes de cambiar algo, explica qué y por qué. Después de cambiarlo, verifica que el juego sigue corriendo.
3. Commits pequeños y descriptivos, uno por mejora.
4. Si algo es ambiguo, elige la opción más simple y repórtala al final. No te detengas a preguntar por detalles menores.
5. **Respeta la identidad técnica del proyecto:** sin librerías, sin assets externos (imágenes, fuentes, audio en archivos). Todo se genera por código (por ejemplo, sonido con Web Audio). Cualquier mejora debe mantener el peso total del juego muy bajo; reporta el tamaño antes y después. Tope interno: 32.000 bytes, sin paso de build ni minificación.
6. El juego se publica en GitHub Pages desde el repo: cada push a la rama publicada actualiza https://ottooniel.github.io/echo/. Verifica que el juego sigue cargando en esa URL después de cada tanda de cambios, y no subas nada roto a la rama publicada.
7. Tiempo máximo para mejoras: **1 día**. Después se congela el juego (feature freeze) para grabar el gameplay del tráiler.

## Fase 1 — Auditoría (solo lectura, no modificar nada)
Escanea el repo completo y entrégame un informe con:
- **Arquitectura:** estructura de carpetas, loop principal, cómo se genera y reproduce el "eco".
- **Bugs y riesgos:** colisiones, desincronización del eco, memory leaks, casos borde (ronda 1, muerte instantánea, reinicio, ventana en segundo plano).
- **Game feel:** juice, feedback visual y sonoro, dificultad y curva de progresión, claridad de la mecánica del eco en los primeros 10 segundos.
- **Rendimiento:** FPS, tamaño del historial de recorrido, coste por ronda.
- **Presentación para el reto:** pantalla de título, onboarding, pantalla de game over, README del repo.
- **Lista priorizada** de mejoras con esfuerzo (S/M/L) e impacto (alto/medio/bajo). Máximo 10 ítems.

Detente al terminar el informe y espera mi aprobación.

## Fase 2 — Mejoras (tras mi aprobación)
Implementa solo los ítems aprobados, en este orden:
1. Bugs que rompan la partida.
2. Claridad de la mecánica del eco (que se entienda sin explicación).
3. Game feel (partículas, screen shake, sonido, transiciones).
4. Pulido de pantalla de título y game over.
5. README del repo con GIF/captura, link a la versión jugable, cómo jugar, créditos y el dato de "menos de 32 KB" sin dependencias.

Al terminar: resumen de lo hecho, lo que quedó fuera y cómo ejecutar el juego.

## Fase 3 — Material para el tráiler (juego ya congelado)
Prepara lo que necesitará el tráiler:
- Lista de **momentos clave a grabar** (primer eco apareciendo, persecución, casi-muerte, ronda con varios ecos, game over).
- Un **modo de captura** opcional (sin HUD de debug, resolución fija, semilla fija para repetir tomas).
- **Paleta de colores, tipografía y tono visual** del juego, en un bloque que pueda pegar como referencia de estilo para la generación.

## Fase 4 — Tráiler con Higgsfield (MCP)
1. Consulta mi saldo de créditos y la vigencia de la ventana de 3 días. Si la ventana vence pronto, prioriza esto.
2. Prueba primero en baja resolución/duración antes de lanzar tomas caras.
3. Estructura (30–45 s): gancho → mundo/ambiente → mecánica del eco → clímax → título "ECHO" + llamada a la acción.
4. **Mezcla gameplay real con tomas generadas.** Las tomas de IA solo para intro, ambiente y momentos épicos. No debe parecer que el juego no existe.
5. Mantén consistencia visual entre tomas (misma paleta y referencias de estilo).
6. Presupuesto orientativo de 100 USD: ~50 video, ~20 imágenes/assets, ~15 audio y música, ~15 reserva para regenerar.
7. Antes de gastar, muéstrame la lista de tomas con costo estimado y espera mi aprobación.
8. Al final, pasa el tráiler por el predictor de viralidad.

## Fase 5 — Post de LinkedIn
Redacta un post en español con esta estructura:
- **Gancho:** hice un juego para el reto de Open2 y le hice el tráiler con IA en 72 horas.
- **Video:** el tráiler de ECHO.
- **Proceso:** Cursor para el juego, Claude (auditoría y mejoras) y Higgsfield vía MCP para el tráiler. Indicar claramente que el tráiler está hecho con IA.
- **Cierre:** link para jugar (https://ottooniel.github.io/echo/), link al repo (https://github.com/ottooniel/echo) y una pregunta para generar comentarios.
- Destaca el dato técnico: el juego pesa menos de 32 KB, sin librerías ni assets. Es un gancho fuerte para LinkedIn.

Entrega 2 versiones (una corta, una más narrativa).

## Calendario sugerido
| Fecha | Qué |
|---|---|
| Lun 9 nov | Fase 1 (auditoría) y empezar Fase 2 |
| Mar 10 nov | Terminar Fase 2, feature freeze, Fase 3 |
| Mié 11 nov | Fase 4 (tráiler) |
| Jue 12 nov | Ajustes del tráiler, Fase 5, envío al reto |
| Vie 13 nov | Margen de seguridad (cierre de envíos) |

## Prompt para pegar al iniciar la sesión
> Lee este archivo completo. Empieza por la Fase 1 y detente al entregar el informe de auditoría. No modifiques nada todavía.