# Intervalos · Tábata Air Bike

Temporizador de intervalos para entrenar con la Air Bike del gimnasio. Un solo archivo HTML,
sin dependencias, funciona offline y se puede instalar como ícono en la pantalla de inicio del celular.

## Archivos

| Archivo | Para qué sirve |
|---|---|
| `index.html` | La app entera (HTML + CSS + JS en un solo archivo) |
| `manifest.webmanifest` | Datos de instalación: nombre, colores, íconos |
| `sw.js` | Service worker: guarda la app en el celular para que funcione sin internet |
| `icon-*.png` | Íconos de la pantalla de inicio (512, 192, 180 para iPhone, 32 para la pestaña) |
| `intervalos.html` | Copia original de un solo archivo, para abrir con doble clic en la PC |

## Publicarlo en GitHub Pages

Desde la carpeta del proyecto, en PowerShell o Git Bash:

```bash
git init
git add .
git commit -m "App de intervalos Tabata para Air Bike"
git branch -M main
git remote add origin https://github.com/USUARIO/intervalos-airbike.git
git push -u origin main
```

Creá antes el repositorio vacío `intervalos-airbike` en github.com (puede ser público o privado; para
GitHub Pages gratis conviene **público**).

Después, en GitHub: **Settings → Pages → Source: Deploy from a branch → Branch: `main` / `(root)` → Save**.
En un minuto queda publicado en:

```
https://USUARIO.github.io/intervalos-airbike/
```

Para actualizar la app más adelante: editás `index.html`, subís el número de versión en `sw.js`
(`const CACHE = "intervalos-v2"`) y hacés `git add . && git commit -m "cambios" && git push`.

## Poner el ícono en la pantalla de inicio

**Android (Chrome):** abrí la URL → menú ⋮ → *Instalar aplicación* / *Agregar a la pantalla principal*.
También aparece el botón **⤓ Instalar** arriba a la derecha de la app.

**iPhone (Safari, tiene que ser Safari):** abrí la URL → botón Compartir → *Agregar a inicio*.

Una vez instalada se abre a pantalla completa, sin barra del navegador, y funciona sin señal
(la primera visita con internet es la que la deja guardada).

## Probarlo en la PC antes de publicar

El service worker no funciona abriendo el archivo con doble clic; necesita un servidor. Con Python:

```bash
python -m http.server 8080
```

y entrás a `http://localhost:8080`. Desde el celular en la misma red: `http://IP-DE-TU-PC:8080`.

## Perfiles

Se guardan en el navegador de cada dispositivo (`localStorage`). Para pasarlos de la PC al celular:
**Exportar respaldo** en una punta, **Importar respaldo** en la otra.
