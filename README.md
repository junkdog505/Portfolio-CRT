# 📺 Portfolio-CRT | Creative 3D & Full-Stack Engineering

Portafolio web interactivo con estética analógica retro, CRT phosphor shaders en GPU, experiencias 3D en tiempo real y arquitectura de alto rendimiento construida con Astro.

---

## ✨ Características Principales

- 🎮 **Escena 3D Persistente (Three.js)**: Modelos interactivos en tiempo real (Laptop retro con terminal Arch Linux, radio analógica, pala, etc.) con sombreado PBR y rotación física sensible al cursor.
- ⚡ **CRT Warp Shader en GPU**: Fondo reactivo programado en GLSL con scanlines, curvatura de tubo, bloom y soporte dinámico y fluido tanto para tema oscuro (fósforo ámbar) como tema claro (modo técnico).
- 📺 **Splash Art de TV CRT & Tux**:
  - Silueta analógica de televisor vintage con antenas y diales.
  - Encendido con haz catódico y estática/ruido de TV sin señal a 60 FPS.
  - Tux (pingüino 3D de Linux) entra caminando sobre una rejilla retro, saluda al usuario (`¡HOLA! 👋`) y detona un zoom dramático acelerado inspirado en el inicio de PlayStation 2.
  - Control de sesión: se reproduce en la primera visita y se puede repetir con `Ctrl + F5`.
- 🐱 **Easter Egg de Identidad**: Al hacer clic en la laptop 3D del Hero, se despliega una tarjeta biométrica con sonido procedural y verificación del desarrollador.
- 🚀 **Astro & View Transitions**: Navegación instantánea entre páginas (`/sobre-mi`, `/experiencia`, `/formacion`, `/proyectos`, `/contacto`) preservando el estado de Three.js y el lienzo de fondo.
- ♿ **Accesibilidad & Performance**: Certificación WCAG AA, soporte táctil responsivo y 60 FPS estables.

---

## 🛠️ Stack Tecnológico

- **Core:** [Astro](https://astro.build/) (Zero JS por defecto, ClientRouter para transiciones fluidas)
- **3D & Gráficos:** [Three.js](https://threejs.org/), WebGL, GLSL Shaders
- **Estilizado:** Tailwind CSS v4, CRT overlay analógico y scanlines personalizadas
- **Audio:** Web Audio API sintético (relé mecánico, ruido blanco y acorde de arranque PS2 sin dependencias externas)
- **Tipado:** TypeScript

---

## 🚀 Desarrollo Local

Instalar dependencias:
```bash
pnpm install
```

Iniciar servidor de desarrollo:
```bash
pnpm dev
```

---

## 📄 Licencia

Desarrollado por [junkdog505](https://github.com/junkdog505).
