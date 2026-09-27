# Portfolio-CRT — Guía de Arquitectura y Contexto de Antigravity

## 🚀 Entorno de Desarrollo y Despliegue

- **Servidor local:** `pnpm dev` (o `astro dev`).
- **Despliegue:** Desplegado en **Cloudflare Pages** como sitio estático puro (SSG) en la carpeta `dist/`.
  - *Regla crítica:* **NO** usar adaptador `@astrojs/cloudflare` ni `wrangler.jsonc` en este proyecto estático (evita el error de binding reservado `ASSETS` en Cloudflare Pages).
  - Versión de Node fijada en `.nvmrc` (`22.12.0`).
  - Cabeceras de caché global en `public/_headers` para modelos 3D (`.glb`), imágenes y fuentes.

---

## 📺 Componentes y Características Clave

1. **Splash Art de TV CRT + Tux + PS2 (`src/components/CRTSplash.astro`)**:
   - Secuencia de ~3.4s ejecutada únicamente en la primera visita (almacenada en `sessionStorage.getItem('portfolio_crt_booted')`, rejugable con `Ctrl + F5`).
   - *Flujo:* TV retro apagada en habitación oscura → Encendido analógico con haz de electrones y nieve/estática de TV → Tux 3D (`public/tux-nobg.png`) entra caminando y saluda (`¡HOLA! 👋`) → Zoom dramático de inicio de PlayStation 2 (`scale(28)`) con acorde ambiental sintético y barrido sub-grave → Revelación fluida del portafolio.

2. **Fondo Persistente y Shaders GLSL (`src/components/CRTWarp.astro` y `Layout.astro`)**:
   - Shader de plasma CRT en GPU en pantalla completa persistente entre rutas (`transition:persist`).
   - Calibrado para modo oscuro (ámbar fósforo) y modo claro (laboratorio técnico limpio).

3. **Escena 3D Three.js Persistente (`src/components/RustScene.astro`)**:
   - Modelos PBR interactivos que se adaptan al viewport y a los contenedores DOM de cada página.

4. **Easter Egg en la Laptop 3D (`src/pages/index.astro`)**:
   - Al hacer clic en la laptop del Hero, se revela el modal biométrico con la foto del creador (`public/creator.jpg`) y su gato, audio procedural retro y tooltip de confirmación humana.

---

## 📚 Documentación Astro
- Documentación completa: https://docs.astro.build
