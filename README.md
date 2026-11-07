# ECHO

Un arcade de supervivencia donde **tu peor enemigo eres tú mismo**: cada ronda graba tu recorrido y lo convierte en un eco mortal que te persigue en las siguientes.

Hecho para el reto **build&play** de [Open2 / Build & Pitch](https://www.open2.io/build-and-pitch/play): un juego arcade difícil en **32 KB**, sin librerías y sin assets.

**Jugar:** https://ottooniel.github.io/build-and-play/

## Cómo se juega

1. Recoge todos los orbes amarillos para completar la ronda.
2. Al terminar, tu recorrido se vuelve un **eco**: un fantasma que repite exactamente tu camino en cada ronda siguiente.
3. Tocar un eco (pasados 1.5 s de gracia al empezar la ronda) o salir de la arena termina la partida.
4. Los orbes aparecen sobre las rutas de tus ecos anteriores, así que siempre tendrás que cruzarte con tu pasado.
5. Cada ronda hay más orbes y más ecos. La ronda 1 enseña sola; a partir de la 3 aprieta.

Puntaje: rondas completadas, con los orbes como desempate. El mejor puntaje se guarda en tu navegador.

## Controles

| Dispositivo | Cómo |
|---|---|
| Ratón | El punto sigue al puntero |
| Teclado | WASD o flechas |
| Celular | Joystick flotante: arrastra desde donde toques |
| `M` | Silenciar o activar el sonido |
| `C` o tocar "compartir" | Compartir tu puntaje al terminar una partida |

## Cumple las reglas del reto

| Regla | Cómo se cumple |
|---|---|
| 32 KB en total | Un único `index.html` de ~26 KB, sin comprimir |
| Sin librerías ni motores | JavaScript puro, sin dependencias |
| Cero assets | Todo se dibuja con Canvas 2D y todo suena con Web Audio; la tipografía es `monospace` del sistema |
| Repo nuevo y público | Creado durante el reto (6 nov 2026) |
| Original | Mecánica propia: los ecos son grabaciones de tu propio recorrido |
| Un juego por persona | Este |

El juego no hace ninguna petición de red.

## Detalles técnicos

- Simulación con paso fijo a 60 Hz, independiente de la tasa de refresco. Por eso el replay de los ecos es determinista.
- Los efectos visuales (estela, partículas, shake, brillo) y el audio se disparan solo desde el render, nunca desde la simulación.
- Sonidos sintetizados con osciladores y ruido. Cada eco activo suma un drone grave cuyo tono depende de su posición.

## Ejecutar en local

Abre `index.html` en cualquier navegador moderno. No hay build ni dependencias.

Para medir el peso (PowerShell, desde la raíz del repo):

```powershell
(Get-Item index.html).Length
```

## Cómo se hizo

Desarrollado por fases (bucle y controles, ecos y colisiones, efectos, audio, pantallas) con ayuda de IA en Cursor. Las reglas y el contexto del proyecto están en [`AGENTS.md`](AGENTS.md).
