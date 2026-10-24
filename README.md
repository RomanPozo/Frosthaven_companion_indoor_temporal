# ❄️ Frosthaven: Outpost & Campaign Companion

Aplicación web ligera para acompañar las partidas de **Frosthaven** desde el móvil, la tablet o el ordenador. Lleva el calendario de la campaña, guía al grupo por la Fase de Puesto Avanzado, dibuja el árbol de escenarios y guarda las fotos de vuestros momentos épicos.

Funciona **sin conexión una vez cargada**, sin cuentas ni servidores. Todos los datos se quedan en el navegador del dispositivo.

> Los recursos, la moral, la prosperidad y las cartas de edificios se siguen llevando en la mesa. La app se centra en lo que es fácil de olvidar.

---

## ✨ Funcionalidades

### 🏰 Fase de Puesto Avanzado
Asistente paso a paso por las 5 subfases oficiales:

1. **Paso del Tiempo**
   - Calendario de 80 semanas (4 años de 10 semanas de Verano y 10 de Invierno).
   - Agenda de secciones del Libro de Secciones en cualquier semana futura.
   - Botón **Avanzar 1 Semana** con avisos automáticos:
     - **¡Lectura del Libro de Secciones!** si la nueva semana tiene secciones agendadas.
     - **¡Cambio de Estación!** al pasar de Verano a Invierno o al revés.
2. **Evento de Puesto Avanzado**: qué mazo robar según la estación, diario opcional de eventos y resumen de la resolución de ataques.
3. **Operaciones de Edificios**: orden de resolución y efectos de ruina.
4. **Tiempo Libre**: subir de nivel, retirar y crear personajes, artesano, alquimista y venta de objetos, con una calculadora de nivel y oro inicial según la Prosperidad.
5. **Construcción**: construir, mejorar, construcción extra y reconstruir.

### 🗺️ Árbol de Escenarios
- Grafo interactivo con arrastrar y zoom (ratón, rueda o pellizco táctil).
- Tres estados: **Disponible** (azul), **Completado** (dorado) y **Bloqueado** (rojo).
- Cada escenario guarda número, nombre, coordenadas del mapa y notas.
- **Desbloquear nueva misión**: crea el escenario hijo ya conectado con una flecha y colocado en un hueco libre.
- Los nodos se pueden arrastrar, y hay un botón para reorganizar el árbol automáticamente.
- Vienen precargados **#0 Howling in the Snow** y **#1 A Town in Flames**.

### 🏆 Salón de los Héroes
- Galería de fotos de la mesa, miniaturas pintadas y victorias ajustadas.
- Las fotos se reducen a un máximo de 1280 px y se comprimen a JPEG antes de guardarse en **IndexedDB**.
- Visor a pantalla completa con navegación, edición y borrado.
- 100 % local: ninguna imagen sale del dispositivo.

### 💾 Copias de seguridad
- **Exportar** descarga un archivo `.json` con la campaña y, si quieres, también las fotos.
- **Cargar** restaura un backup. Sirve también para pasar la campaña de un dispositivo a otro.

---

## 🚀 Uso

### Online
Abre la dirección de GitHub Pages del proyecto:

```
https://TU-USUARIO.github.io/NOMBRE-DEL-REPOSITORIO/
```

En el móvil puedes usar **"Añadir a pantalla de inicio"** para tenerla como una app más.

### En local
La app usa módulos ES, así que **no funciona abriendo `index.html` con doble clic**. Necesita un servidor local. Cualquiera de estos vale:

```bash
python -m http.server 5173
```

```bash
npx serve .
```

Después abre `http://localhost:5173`, o la dirección que indique `serve`.

---

## 📦 Publicar en GitHub Pages

1. Crea un repositorio **público** en GitHub.
2. Sube `index.html` y las carpetas `css/` y `js/` a la **raíz** del repositorio.
3. Ve a **Settings → Pages**, elige **Deploy from a branch**, rama `main` y carpeta `/ (root)`, y pulsa **Save**.
4. En 1 o 2 minutos la app estará en `https://TU-USUARIO.github.io/NOMBRE-DEL-REPOSITORIO/`.

No hay paso de compilación: los archivos se sirven tal cual. También funciona en Vercel, Netlify o cualquier hosting estático.

---

## 🔒 Dónde se guardan los datos

| Qué | Dónde | Clave |
|---|---|---|
| Campaña (calendario, diario, árbol) | LocalStorage | `fh_campaign_state` |
| Fotos del Salón de los Héroes | IndexedDB | base de datos `fh_gallery_db` |

- Los datos son **de cada navegador y de cada dirección web**. El móvil y la tablet no se sincronizan solos; usad *Exportar* y *Cargar*.
- Si borras los datos del navegador para este sitio, se pierde la campaña. **Haced backups de vez en cuando.**
- El modo incógnito o privado puede no conservar los datos al cerrar.

---

## 🗂️ Estructura del proyecto

```text
/
├── index.html          # Estructura principal, Tailwind CDN y fuentes
├── css/
│   └── styles.css      # Estilos personalizados, animaciones y scrollbars
└── js/
    ├── app.js          # Punto de entrada: cabecera, pestañas y backups JSON
    ├── state.js        # Estado centralizado y persistencia en LocalStorage
    ├── db.js           # IndexedDB y compresión de imágenes con canvas
    ├── ui.js           # Utilidades compartidas: modales, avisos, iconos
    ├── outpostUI.js    # Fase de Puesto Avanzado: calendario y guías de reglas
    ├── flowchartUI.js  # Árbol de escenarios: pan, zoom, arrastre y modales
    └── galleryUI.js    # Salón de los Héroes: subida, cuadrícula y visor
```

## 🛠️ Tecnología

- HTML5, CSS3 y JavaScript (ES2020+) con **módulos ES nativos**, sin compilación.
- [Tailwind CSS](https://tailwindcss.com) (Play CDN) para el maquetado.
- [Lucide](https://lucide.dev) para los iconos.
- Google Fonts: *Cinzel* para los títulos e *Inter* para el texto.
- LocalStorage e IndexedDB para guardar los datos.

Navegadores compatibles: versiones actuales de Chrome, Edge, Firefox y Safari, también en iOS y Android.

---

## ⚖️ Aviso

Proyecto de fans sin ánimo de lucro, no oficial. **Frosthaven** es una marca de Cephalofair Games, que no respalda este proyecto. Las guías de reglas son resúmenes de consulta rápida; ante cualquier duda, manda el reglamento oficial.
