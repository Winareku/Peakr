# Peakr - Torneos Musicales en el Navegador

**Peakr** es una extensión de navegador para organizar duelos 1v1 entre canciones y rankearlas con un sistema de puntuación inspirado en Elo.

<p align="center">
  <img src="assets/Relayouter_LogoBanner.png" alt="Banner"/>
</p>

---

## 💻 Instalación y carga desde código fuente

La extensión se ejecuta directamente en el navegador. Python solo se usa para los scripts de build y release.

### Requisitos

- **Python 3.6+** (solo para automatizar builds)
- **Navegador compatible**: Chrome/Edge, Firefox u Opera

### Pasos

1. Clona el repositorio:
   ```bash
   git clone https://github.com/Winareku/Peakr.git
   cd Peakr
   ```
2. Copia el manifiesto correspondiente para tu navegador:
   ```bash
   cp src/manifests/manifest.chromium.json src/manifest.json
   ```
   O usa `manifest.firefox.json` / `manifest.opera.json` según el navegador.
3. Carga la carpeta `src/` como extensión sin empaquetar:
   - Chrome/Edge: `chrome://extensions`
   - Firefox: `about:debugging`
   - Opera: `opera://extensions`

> En Firefox, usa "Cargar complemento temporal" y selecciona `src/manifest.json`.

---

## 🚀 Características principales

- **Duelos 1v1**: compite canciones en batallas rápidas.
- **Ranking dinámico**: top 3 y lista ordenada por puntuación.
- **Sistema Elo**: los puntos se ajustan tras cada victoria.
- **Importar / exportar JSON**: copia de seguridad y migración de biblioteca.
- **Integración con Deezer**: datos y portadas de canciones.
- **Interfaz dark Material 3**: estilo moderno y optimizado para sidebar.
- **Arquitectura multi-navegador**: mismo código UI con manifiestos específicos.

---

## 📁 Estructura del proyecto

```
Peakr/
├── scripts/                    # Automatización de build/release
│   ├── build.py               # Genera builds para cada navegador
│   └── release.py             # Build + empaquetado ZIP
├── src/                        # Código fuente principal
│   ├── assets/                # Iconos y recursos compartidos
│   │   └── icon.png
│   ├── background/            # Background scripts por plataforma
│   │   ├── chromium.js
│   │   ├── firefox.js
│   │   └── opera.js
│   ├── manifests/             # Manifiestos por navegador
│   │   ├── manifest.chromium.json
│   │   ├── manifest.firefox.json
│   │   └── manifest.opera.json
│   ├── ui/                    # Interfaz unificada del sidepanel/sidebar
│   │   ├── ui.html
│   │   └── ui.css
│   ├── scripts/               # Lógica compartida de la UI
│   │   ├── app.js
│   │   └── modules/
│   │       ├── state.js
│   │       ├── storage.js
│   │       ├── elo.js
│   │       ├── deezer.js
│   │       ├── audio-manager.js
│   │       └── ui/
│   │           ├── base.js
│   │           ├── arena.js
│   │           ├── ranking.js
│   │           ├── settings.js
│   │           ├── modal.js
│   │           ├── navigation.js
│   │           ├── maturity.js
│   │           └── toast.js
│   ├── shared/                # Código reutilizable (opcional)
│   └── content/               # Scripts de inyección para páginas
├── dist/                      # Builds generados automáticamente
│   ├── chromium/
│   ├── firefox/
│   └── opera/
├── .gitignore
└── README.md
```

---

## 🔧 Flujo de trabajo

### Desarrollo local

1. Copia el manifiesto del navegador que quieras probar:
   ```bash
   cp src/manifests/manifest.chromium.json src/manifest.json
   ```
2. Carga la carpeta `src/` en el navegador en modo desarrollador.
3. Haz tus cambios en `src/` y recarga la extensión.

### Generar builds para todas las plataformas

```bash
python scripts/build.py
```

Esto crea carpetas en `dist/` para:
- `dist/chromium/`
- `dist/firefox/`
- `dist/opera/`

Cada build incluye el manifiesto correcto y solo los assets necesarios para esa plataforma.

### Generar release empaquetado

```bash
python scripts/release.py
```

Esto ejecuta el build y empaqueta cada versión en ZIP listos para subir a la tienda.

---

## 🛠️ Desarrollo

### Requisitos mínimos

- Python 3.6+ (solo para los scripts de automatización)
- Navegador compatible: Chrome/Edge, Firefox u Opera

### Dónde hacer cambios

- `src/ui/ui.html`: estructura del panel lateral
- `src/ui/ui.css`: estilos de la UI
- `src/scripts/app.js`: inicialización de la app
- `src/scripts/modules/`: lógica de estado, almacenamiento y UI
- `src/background/`: comportamiento específico por navegador
- `src/manifests/`: configuración de cada plataforma

---

## 📝 Notas importantes

- La carpeta `dist/` y `src/manifest.json` se ignoran en Git.
- No comitees archivos generados ni ZIP.
- Mantén el manifiesto específico separado en `src/manifests/`.
- El código de UI es compartido; solo el manifest y el background cambian por navegador.

---

## 🤝 Donaciones

Si quieres apoyar el desarrollo de Peakr, me ayudas mucho con un café:

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/winareku)

---

## 📄 Licencia

Proyecto personal - Todos los derechos reservados.
