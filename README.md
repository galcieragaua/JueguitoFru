# JueguitoFru 🌿 (3D)

Juego web **3D** ambientado en una plaza de Buenos Aires. Controlás al pibe de los
rulos en **primera persona**, caminás hasta el **banco de cemento** donde está el
**FRU MAN** y le preguntás si te vende un poco de **FRU** 🌿. Pagás en **pesos
argentinos (ARS)** 🇦🇷. Hecho con **Three.js**, árboles frondosos (miles de hojas
instanciadas), sombras suaves y bloom para una vibe casi ray-traced.

## 🎮 Jugar

Abrí el link de GitHub Pages (cuando esté activado), o serví la carpeta local.
Necesita internet para cargar Three.js desde el CDN.

### Controles
- **Click** en la pantalla → mirar (primera persona, mouse look)
- **WASD / flechas** → moverte · **Shift** → correr
- **E / Espacio** → hablar con el FRU MAN / confirmar
- **V** → cambiar entre 1ª y 3ª persona
- **F** → pantalla completa · **Esc** → soltar el mouse
- 📱 joystick + arrastrar para mirar + botón HABLAR

## Cara realista (opcional)

Los personajes usan una cara estilizada por defecto. Si querés la **cara real**
foto-realista, subí un **primer plano de frente** como archivo en:

```
assets/face.jpg
```

El juego la detecta y la mapea como textura sobre la cara automáticamente.
> Importante: tiene que ser un **archivo** (`assets/face.jpg`), no una imagen
> pegada en el chat.

## Detalles
- Música: tu track real `assets/track.mp3` (arranca al hablar con el FRU MAN).
- Mumbles del FRU MAN + moneditas al comprar/vender (Web Audio API).
- Compra/venta de FRU en ARS con banderita argentina.
- Todo en un solo `index.html` (Three.js por CDN).

## Local
```bash
python3 -m http.server 8000   # http://localhost:8000
```
