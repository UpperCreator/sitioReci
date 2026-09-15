# Prototipo Modelo N°1 — Clasificador en vivo

Página web que carga un modelo de **Teachable Machine** (imagen) con
TensorFlow.js y clasifica en vivo usando la cámara del navegador.

Clases del modelo: **Verde**, **Negro**, **Blanco**.

## Estructura

```
.
├── index.html          # página principal
└── model/
    ├── model.json       # arquitectura del modelo
    ├── weights.bin       # pesos del modelo
    └── metadata.json     # etiquetas y config
```

## Probar localmente

Los navegadores bloquean el acceso a la cámara y la carga de archivos
locales (`file://`) por seguridad, así que necesitas un servidor local.
Desde esta carpeta, corre uno de estos comandos y abre la URL que te
indique (normalmente `http://localhost:8000`):

```bash
# Python 3
python3 -m http.server 8000

# o con Node (npx)
npx serve .
```

## Publicar en GitHub Pages

1. Crea un repositorio nuevo en GitHub (público, para que Pages sea gratis),
   por ejemplo `prototipo-modelo-n1`.
2. Sube estos archivos manteniendo la estructura de carpetas:
   - `index.html`
   - `model/model.json`
   - `model/weights.bin`
   - `model/metadata.json`

   Desde la terminal, dentro de esta carpeta:

   ```bash
   git init
   git add .
   git commit -m "Prototipo modelo N1"
   git branch -M main
   git remote add origin https://github.com/TU_USUARIO/prototipo-modelo-n1.git
   git push -u origin main
   ```

   (O simplemente arrastra los archivos en la interfaz web de GitHub,
   respetando la carpeta `model/`.)

3. En el repositorio, ve a **Settings → Pages**.
4. En "Build and deployment" → "Source", elige **Deploy from a branch**.
5. En "Branch", selecciona `main` y la carpeta `/ (root)`, luego **Save**.
6. Espera 1-2 minutos. GitHub te dará una URL como:

   ```
   https://TU_USUARIO.github.io/prototipo-modelo-n1/
   ```

7. Abre esa URL — como GitHub Pages sirve por HTTPS, el navegador
   permitirá el acceso a la cámara (requisito de seguridad de WebRTC).

## Notas

- El modelo se carga desde la carpeta local `model/`, así que **no
  depende del enlace de Teachable Machine** una vez publicado — funciona
  aunque borres el proyecto en Teachable Machine.
- Si prefieres seguir usando el modelo alojado en Teachable Machine en
  vez de los archivos locales, puedes cambiar en `index.html`:

  ```js
  const URL_MODEL = "./model/";
  ```

  por:

  ```js
  const URL_MODEL = "https://teachablemachine.withgoogle.com/models/RZ3BN_YOv/";
  ```

  (esto requiere conexión constante a los servidores de Google).
