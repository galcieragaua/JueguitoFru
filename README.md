# JueguitoFru 🌿

Mini-juego web interactivo ambientado en una **plaza de Buenos Aires de día**
(Juez Tedín, a la vuelta del MALBA / Alcorta), con estética **pixel-art** y a
**pantalla completa**. Controlás al pibe de los rulos, caminás por la vereda hasta
el **banco de cemento** donde está sentado el **FRU MAN** y le preguntás si te vende
un poco de **FRU** 🌿 (una plantita verde con forma de hoja de maple canadiense, pero
verde). Comprás y vendés con **pesos argentinos (ARS)** y la banderita de Argentina.

## 🎮 Jugar online

Una vez activado GitHub Pages (ver abajo), el juego queda en:

> **https://galcieragaua.github.io/JueguitoFru/**

### Activar GitHub Pages (una sola vez)

1. Andá a **Settings → Pages** del repo en GitHub.
2. En **Build and deployment → Source**, elegí **GitHub Actions**.
3. Listo. Cada push a la branch corre el workflow y publica el juego en la URL de arriba.
   (Podés forzar el deploy desde **Actions → Deploy JueguitoFru to GitHub Pages → Run workflow**.)

> Mientras tanto, también podés abrirlo al toque sin configurar nada con
> [htmlpreview](https://htmlpreview.github.io/?https://raw.githubusercontent.com/galcieragaua/JueguitoFru/claude/hopeful-franklin-dqonn/index.html).

## Controles

- **Moverte:** `WASD` o flechas (celular: joystick en pantalla)
- **Hablar / Confirmar:** `E` o `Espacio` (celular: botón `HABLAR`)
- **Pantalla completa:** botón `⛶` arriba a la derecha, o tecla `F`
- Acercate al FRU MAN, hablale y se abre el **puesto de FRU** para comprar/vender.

## Detalles

- **Todo en un solo archivo** (`index.html`), sin dependencias.
- Render **pixel-art adaptativo**: llena toda la pantalla (16:10 de la MacBook 14" incluido).
- **Música:** tu track real `assets/track.mp3` (suena en loop cuando hablás con el FRU MAN).
- **Mumbles** (la voz "blablah" del FRU MAN), + moneditas al comprar/vender (Web Audio API).
- Diálogos en **español rioplatense**.
- Ambiente inspirado en las fotos: loma de pasto, árboles grandes, hiedra, farol verde,
  vereda de cemento, calle (Juez Tedín) y el banco de cemento donde se sienta el FRU MAN.

## Correr localmente

```bash
# servir la carpeta (recomendado, para que cargue el mp3):
python3 -m http.server 8000   # y entrá a http://localhost:8000
```
