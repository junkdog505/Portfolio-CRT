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
   - Secuencia cinemática puramente visual de ~3.8s que recrea la mítica animación de apertura de puerta de *Resident Evil (PS1)*, ejecutada como búfer de precarga únicamente en la primera visita de sesión (`sessionStorage.getItem('portfolio_door_opened')`, rejugable con `Ctrl + F5` o `Ctrl + R`). No es saltable para permitir que todos los modelos 3D, shaders y fuentes de la web terminen de compilar y cargar fluidamente en segundo plano.
   - *Flujo:* Emergencia gradual desde velo opaco oscuro ("poco a poco") con encuadre completo de la puerta y pasillo de la mansión → El foco linterna cálido ilumina el picaporte y la madera → Giro del picaporte mecánico → La puerta de madera se abre suavemente hacia adentro → La cámara avanza adentrándose por el umbral hacia la oscuridad de la siguiente habitación → Disolución gradual y revelación fluida al 100% de rendimiento del portafolio.

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
