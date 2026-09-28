# Portfolio-CRT — Guía de Arquitectura y Contexto de Antigravity

## 🚀 Entorno de Desarrollo y Despliegue

- **Servidor local:** `pnpm dev` (o `astro dev`).
- **Despliegue:** Desplegado en **Cloudflare Pages** como sitio estático puro (SSG) en la carpeta `dist/`.
  - *Regla crítica:* **NO** usar adaptador `@astrojs/cloudflare` ni `wrangler.jsonc` en este proyecto estático (evita el error de binding reservado `ASSETS` en Cloudflare Pages).
  - Versión de Node fijada en `.nvmrc` (`22.12.0`).
  - Cabeceras de caché global en `public/_headers` para modelos 3D (`.glb`), imágenes y fuentes.

---

## 📺 Componentes y Características Clave

1. **Splash Art 3D Three.js: Pantalla de Carga Puerta 3D Resident Evil PS1 (`src/components/CRTSplash.astro`)**:
   - Secuencia cinemática puramente visual de ~3.8s que recrea la mítica animación de apertura de puerta de *Resident Evil (PS1)*, ejecutada como búfer de precarga únicamente en la primera visita absoluta (`localStorage.getItem('portfolio_splash_seen')`). Una vez completada, el navegador almacena el estado de forma persistente y cualquier recarga (F5) carga la página estándar directamente con cero milisegundos de splash o destello.
   - *Protección Anti-Flash:* Cortina crítica inline `#critical-boot-curtain` en el `<head>` y primer hijo de `<body>` (`Layout.astro`) a nivel de renderizado 0ms, ocultando `#app-content-root` hasta que el splash 3D termina, impidiendo cualquier parpadeo de contenido antes de la cinemática.
   - *Flujo:* Emergencia gradual desde velo opaco oscuro ("poco a poco") con encuadre completo de la puerta y pasillo de la mansión → El foco linterna cálido ilumina el picaporte y la madera → Giro del picaporte mecánico → La puerta de madera se abre suavemente hacia adentro → La cámara avanza adentrándose por el umbral hacia la oscuridad de la siguiente habitación → Disolución gradual y revelación fluida al 100% de rendimiento del portafolio.

2. **Fondo Persistente y Shaders GLSL (`src/components/CRTWarp.astro` y `Layout.astro`)**:
   - Shader de plasma CRT en GPU en pantalla completa persistente entre rutas (`transition:persist`).
   - Calibrado exclusivamente para modo oscuro (ámbar fósforo analógico de alto contraste).

3. **Escena 3D Three.js Persistente (`src/components/RustScene.astro`)**:
   - Modelos PBR interactivos que se adaptan al viewport y a los contenedores DOM de cada página.

4. **Easter Egg en la Laptop 3D (`src/pages/index.astro`)**:
   - Al hacer clic en la laptop del Hero, se revela el modal biométrico con la foto del creador (`public/creator.jpg`) y su gato, audio procedural retro y tooltip de confirmación humana.

---

## 📚 Documentación Astro
- Documentación completa: https://docs.astro.build
