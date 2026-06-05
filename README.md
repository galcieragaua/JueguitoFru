# JueguitoFru 🌿

Mini-juego web interactivo ambientado en una **terraza nocturna de Buenos Aires**.
Controlás al pibe de los rulos, caminás hasta el **banco de cemento** donde está
sentado el **FRU MAN** y le preguntás si te vende un poco de **FRU** 🌿 (una plantita
verde con forma de hoja de maple canadiense, pero verde). Comprás y vendés con
**pesos argentinos (ARS)** y la banderita de Argentina.

Inspirado en las fotos: el personaje principal (rulos), el FRU MAN (campera naranja)
y el ambiente (azotea de noche con skyline porteño, cantero de cemento y la planta).

## Cómo jugar

Abrí `index.html` en cualquier navegador moderno. No necesita servidor ni instalar nada.

- **Moverte:** `WASD` o flechas (en celular, joystick en pantalla)
- **Hablar / Confirmar:** `E` o `Espacio` (en celular, botón `HABLAR`)
- Acercate al FRU MAN, hablale y se abre el **puesto de FRU** para comprar/vender.

## Detalles

- **Todo en un solo archivo** (`index.html`), sin dependencias.
- Gráficos dibujados con Canvas 2D (personajes, skyline, cantero, hoja FRU).
- **Audio procedural** con Web Audio API:
  - Música lofi de fondo que arranca al hablar con el FRU MAN.
  - *Mumbles* (la voz "blablah" del FRU MAN cuando habla).
  - Sonidos de moneditas al comprar/vender.
- Diálogos en **español rioplatense**.
- Querés el track real de fondo? Poné tu mp3 en `assets/track.mp3` (ver `assets/README.md`).

## Correr localmente

```bash
# simplemente abrí el archivo
xdg-open index.html      # Linux
open index.html          # macOS
# o serví la carpeta:
python3 -m http.server 8000   # y entrá a http://localhost:8000
```
