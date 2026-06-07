# JueguitoFru 🌿

Mini-juego web **3D** ambientado en una calle arbolada de **Buenos Aires en otoño**
(inspirada en Juez Tedín, a la vuelta del MALBA / Alcorta). Controlás al pibe de los
rulos en **primera o tercera persona**, caminás por la vereda hasta el **banco de
cemento** donde está sentado el **FRU MAN** y le preguntás si te vende un poco de
**FRU** 🌿. Comprás y vendés con **pesos argentinos (ARS)** 🇦🇷, suena un track de
fondo y el FRU MAN "habla" con *mumbles*. Todo en **español rioplatense**.

> **Jugar:** https://galcieragaua.github.io/JueguitoFru/
> (Servido por GitHub Pages desde la branch del repo. Necesita internet para cargar
> Three.js desde el CDN. **No funciona por htmlpreview** porque ese proxy no ejecuta
> módulos ES — usá el link de Pages.)

---

## 🎮 Cómo se juega

1. Pantalla de inicio → **Entrar**.
2. **Click** en la pantalla para capturar el mouse (primera persona).
3. Caminá hasta el banco; cuando estás cerca aparece el cartel **“E · preguntá por FRU”**.
4. Apretás **E**, arranca la charla (con música + mumbles) y se abre el **Puesto de FRU**.
5. Comprás/vendés FRU en ARS. Al cerrar, la música se pausa (y retoma desde donde quedó la próxima vez).

### Controles
| Acción | Tecla / gesto |
|---|---|
| Mirar | Mouse (con click para *pointer lock*) · arrastrar en celular |
| Moverse | `WASD` / Flechas · joystick en celular |
| Correr | `Shift` |
| Hablar / Confirmar | `E` o `Espacio` · botón `HABLAR` en celular |
| Cambiar cámara 1ª/3ª | `V` · botón `👁` |
| Pantalla completa | `F` · botón `⛶` |
| Soltar el mouse | `Esc` |

---

## 🧱 Estado actual (qué está hecho)

**Motor y render**
- Three.js **r0.160** cargado por **importmap** desde jsDelivr (sin build, sin dependencias instaladas).
- `WebGLRenderer` con sombras `PCFSoft`, **tone mapping ACES Filmic**, color space sRGB.
- **Postproceso**: `EffectComposer` + `UnrealBloomPass` (glow en farolitos/hojas → vibe cinematográfica).
- Cielo: domo con degradé de **atardecer otoñal**. **Niebla** exponencial para cerrar el fondo.
- Luces: `HemisphereLight` (cielo/suelo) + `DirectionalLight` (sol cálido con sombras) + `AmbientLight`.

**Escena (calle porteña otoñal)**
- **Terreno**: colina ascendente con **vértices desplazados** (no es un plano infinito), pasto con textura procedural.
- Secuencia fiel a las fotos: **colina/parque → hiedra → vereda (con el banco) → escalón/cordón → calle → vereda de enfrente → edificio**.
- **Árboles** otoñales: tronco + **ramas que se bifurcan recursivamente** + copa en **capas de hojas instanciadas** (`InstancedMesh`) tintadas con paleta de amarillos/ocres/verde. Los grandes **arquean sobre la calle**.
- **Banco de cemento** (losa + 2 patas) con el FRU MAN sentado; **brote de FRU** (hojas de maple verde) al lado.
- **Edificio “3198”** de ladrillo (textura procedural), con **fajas horizontales de balcón**, **toldo semicilíndrico** con el número mirando al banco, zócalo de tablones de madera en diagonal y seto.
- **Reja con enredadera** siguiendo la cuadra del lado del edificio.
- **Autos** estacionados **paralelos al cordón** (sedán/van/SUV) con cabina, pilares, ruedas con llanta y luces.
- **Esquina oeste**: la calle dobla (cruce) + **portón de madera** y casa. **Farolitos** verdes con luz cálida.
- **Colisiones** (AABB) contra banco, edificio, autos, árboles, muros y portón.

**Personajes y cara**
- `buildCharacter()` arma cuerpo (torso/brazos/piernas con cápsulas), campera, jeans, zapatillas y **pelo rulo 3D** voluminoso.
- **Cara real**: se recortó la cara de una foto provista (`assets/face.jpg`) y se mapea sobre una **cabeza curva de más polígonos** (sphere 40×40 + parche con relieve), con el fondo de la foto **desvanecido por una máscara ovalada** para que se funda con la cabeza.
- Tanto el **jugador** (campera bordó) como el **FRU MAN** (campera naranja) comparten esa cara (“son parecidos”).

**Audio** (`AudioFX`, Web Audio API)
- **Track de fondo** real (`assets/track.mp3`) que **suena solo durante la interacción** con el FRU MAN y se **pausa al terminar, retomando desde donde quedó**.
- **Mumbles** procedurales (la voz “blablah” del FRU MAN) generados con osciladores.
- **Moneditas** al comprar/vender; bips de diálogo.

**Diálogo y economía**
- Sistema de diálogo con efecto *typewriter* y mumbles sincronizados.
- **Shop** con compra/venta de FRU en **ARS** (banderita argentina dibujada en CSS).
- Estado inicial: `cash = 12.000 ARS`, `FRU = 0`, compra `3.500`, venta `2.600`.

**UX / plataforma**
- **Fullscreen** y diseño responsive; controles **táctiles** (joystick + botón) en mobile.
- **Salvavidas de carga**: si el motor no arranca (p. ej. htmlpreview), el loading no queda colgado — muestra el error/guía a los ~12 s.

---

## 📁 Estructura del repo

```
JueguitoFru/
├── index.html          # TODO el juego en un solo archivo (HTML + CSS + Three.js módulo)
├── assets/
│   ├── track.mp3       # música de fondo (suena al hablar con el FRU MAN)
│   ├── face.jpg        # cara real recortada de la foto, usada como textura del personaje
│   └── README.md       # notas sobre los assets
├── .nojekyll           # para que Pages sirva todo tal cual (sin Jekyll)
└── README.md           # este archivo
```

> **Arquitectura:** todo vive en `index.html`. No hay build step ni `node_modules`.
> Three.js y sus addons (`EffectComposer`, `RenderPass`, `UnrealBloomPass`) se importan
> por **importmap** desde el CDN. Abrís el archivo (servido) y corre.

---

## 🚀 Deploy (GitHub Pages, gratis)

El repo es **público**, así que Pages es gratis. Está configurado como **“Deploy from
a branch”** (Settings → Pages → Source: *Deploy from a branch* → branch del proyecto →
`/root`). Cada push a la branch redeploya solo. URL final:

```
https://galcieragaua.github.io/JueguitoFru/
```

### Correr localmente
```bash
# desde la carpeta del repo (sirve el mp3/face correctamente)
python3 -m http.server 8000   # luego abrí http://localhost:8000
```
(Abrir el `index.html` con doble clic también funciona, pero servirlo es más confiable
para que cargue `assets/`.)

---

## 🗺️ Roadmap — Ambiente fotorrealista por fotogrametría / 360

Objetivo: acercar el entorno a “real life” usando imágenes reales del lugar.

**Estrategia recomendada (desde iPhone/MacBook):**
1. **Polycam → 360 Mode** parado al lado del banco → **panorámica equirectangular** que
   se usa como **skybox/fondo fotográfico real** en Three.js.
2. **Polycam → Photo Mode (fotogrametría)** para props sólidos (banco, fachada) → **GLB**
   que se coloca como malla real en la escena.
3. (Alternativa Mac nativa de alta calidad: **Apple Object Capture** vía la app *PhotoCatch*.)

**Reparto de tareas:**
- **El usuario** corre la captura/reconstrucción (el paso pesado necesita la GPU del
  dispositivo o la nube de la app — el contenedor donde corre Claude **no tiene GPU**).
- **Claude/Code** hace: extracción/curado de frames (`imageio-ffmpeg`), limpieza/decimado
  de malla (`pymeshlab`/`trimesh`), conversión a **GLB**, **shaders/materiales** (look GTA
  con textura nítida + toque pixelado/estilizado), integración en Three.js y **deploy**.

**Pendiente / ideas:**
- [ ] Skybox 360 fotográfico del lugar real.
- [ ] Banco y edificio por fotogrametría (GLB) reemplazando los modelos procedurales.
- [ ] Hojas/follaje con más variación de color y caída animada.
- [ ] Más NPCs / gente caminando; ciclo día-noche.

---

## ⚠️ Limitaciones conocidas / decisiones

- **No hay generación de imágenes con IA** ni fotogrametría dentro del entorno de Claude
  (sin GPU, efímero). Por eso los assets reales (cara, futuro skybox) salen de **fotos que
  sube el usuario como archivo** y se procesan con PIL/Three.js.
- **htmlpreview no sirve** (no ejecuta módulos ES); usar siempre el link de **GitHub Pages**.
- El realismo tiene techo: es un motor hecho a mano con geometría procedural, no un engine AAA.
- **Privacidad**: el repo es público; `assets/face.jpg` (cara real) y `assets/track.mp3`
  quedan visibles. Si se quiere privacidad, conviene repo privado (Pages pasa a ser pago)
  o quitar esos assets.

---

## 🧾 Historial (resumen de iteraciones)

1. Prototipo 2D (canvas) — terraza/plaza, comprar FRU al FRU MAN, ARS, track + mumbles.
2. Versión 2D pixel-art fullscreen + deploy a Pages.
3. **Salto a 3D** (Three.js): primera persona, árboles instanciados, FRU MAN en el banco.
4. Música con **pausa/resume desde la posición**; escena diurna → **otoñal**.
5. Escena más fiel: **colina + árboles dispersos**, escalón vereda/calle, edificio 3198, autos.
6. **Cara real** del personaje (recorte de foto → cabeza curva de más polígonos).
7. Fix de strafe (D/A), **autos paralelos al cordón** (+van), reja con enredadera, **esquina
   oeste con portón**, cuadra acotada.

---

Hecho con cariño porteño. 🌳🍂🇦🇷
