# Expediente Check — Guía rápida (coquito)

Esta es la página web pública de Expediente Check (`expedientecheck.com`). Es un sitio simple: solo archivos, sin programas complicados detrás. Esta guía te explica, paso a paso, cómo hacer las dos cosas que más vas a necesitar: **subir una noticia nueva** y **cambiar/agregar una foto**.

No necesitas saber programar. Solo seguir los pasos.

---

## 1. ¿Dónde está todo?

| Carpeta / archivo | Para qué sirve |
|---|---|
| `index.html` | La página completa (textos, diseño, secciones). Normalmente **no** hace falta tocarlo. |
| `news.json` | La lista de noticias que aparece en "Novedades". Aquí es donde agregas noticias nuevas. |
| `img/news/` | Fotos que acompañan cada noticia. |
| `img/team/` | Fotos del equipo (Rocío, Marco, Rodrigo). |

---

## 2. Cómo subir una noticia nueva

Abre el archivo `news.json`. Vas a ver algo así:

```json
[
  {
    "date": "Julio 2026",
    "tag": "Nueva entidad",
    "title": "Iniciamos en la Municipalidad de Miraflores y la Municipalidad de Urubamba",
    "excerpt": "Comenzamos la implementación del piloto...",
    "image": "/img/news/miraflores-urubamba.jpg"
  },
  ...
]
```

Para agregar una noticia nueva, **copia y pega este bloque al inicio de la lista** (justo después del primer `[`), y cambia los textos:

```json
  {
    "date": "Agosto 2026",
    "tag": "Novedad",
    "title": "Aquí va el título de tu noticia",
    "excerpt": "Aquí va un texto corto (2-3 líneas) explicando la noticia.",
    "image": "/img/news/nombre-de-tu-foto.jpg"
  },
```

**Importante:**
- No olvides la **coma** `,` al final del bloque que pegaste (para separarlo del siguiente).
- El campo `"image"` debe apuntar al nombre exacto del archivo de foto que subiste a `img/news/` (ver sección 3).
- Si la noticia no tiene foto todavía, puedes dejar `"image": ""` — la tarjeta igual se verá bien, solo sin imagen de fondo.
- Si quieres agregar un link (por ejemplo a YouTube o WhatsApp), agrega una línea `"link": "https://..."` dentro del bloque.

### Dos formas de hacerlo:

**Opción A — Desde GitHub (más fácil, sin instalar nada):**
1. Entra a https://github.com/rociobejar-source/expedientecheck-principal
2. Haz clic en el archivo `news.json`.
3. Haz clic en el ícono del **lápiz** (Edit this file), arriba a la derecha.
4. Pega tu bloque nuevo al inicio de la lista.
5. Baja hasta el final, escribe un mensaje corto (ej. "Nueva noticia agosto") y presiona **"Commit changes"**.
6. Espera 1-2 minutos y revisa expedientecheck.com — ya debería estar publicada.

**Opción B — Local (editando en tu computadora):**
1. Abre `news.json` con el Bloc de notas (o pide ayuda a Claude Code).
2. Edita y guarda.
3. Pide que se suba con `git add`, `git commit` y `git push` (o hazlo tú si sabes usar Git).

---

## 3. Cómo agregar o cambiar una foto

### Fotos de noticias
1. Guarda la foto en tu computadora.
2. Ponla dentro de la carpeta `img/news/` con un nombre simple, sin espacios ni tildes (ejemplo: `evento-agosto.jpg`).
3. En `news.json`, en el campo `"image"`, escribe `"/img/news/evento-agosto.jpg"` (el mismo nombre exacto).

**Tamaño recomendado:** horizontal, aprox. **1200 × 750 px** (o similar, apaisada), formato **JPG**, peso menor a 500 KB. Si la foto es más grande o de otra proporción, no pasa nada — se recorta automáticamente al mostrarse, pero se ve mejor si ya viene horizontal.

### Fotos del equipo (Rocío, Marco, Rodrigo)
Los nombres de archivo están fijos en el código, así que **deben llamarse exactamente así**:

- `img/team/rocio.jpg`
- `img/team/marco.jpg`
- `img/team/rodrigo.jpg`

Si subes un archivo con ese nombre exacto (reemplazando al anterior), la foto se actualiza sola — no hace falta tocar `index.html`.

**Tamaño recomendado:** **cuadrada, 500 × 500 px**, cara centrada, formato JPG, peso menor a 300 KB. Si tu foto no es cuadrada (por ejemplo, es vertical de celular), pide que te ayuden a recortarla antes de subirla — si subes una foto no cuadrada igual funcionará, pero puede cortar la cara de forma rara.

### Cómo subir la foto:
- **Desde GitHub:** entra a la carpeta (`img/news` o `img/team`) → botón **"Add file" → "Upload files"** → arrastra la imagen con el nombre correcto → "Commit changes".
- **Local:** copia el archivo directo a la carpeta en tu computadora y pide que se suba con git.

---

## 4. Errores comunes

| Problema | Causa probable |
|---|---|
| La noticia no aparece | Falta una coma `,` en `news.json`, o hay un error de formato (falta una comilla `"` o una llave `}`). Revisa que el JSON sea válido. |
| La foto no aparece, solo se ve un fondo de color | El nombre del archivo no coincide exactamente con lo escrito en `news.json` (o con `rocio.jpg` / `marco.jpg` / `rodrigo.jpg`), o la foto no se subió a la carpeta correcta. |
| Los cambios no se ven en expedientecheck.com | Puede tardar 1-2 minutos en publicarse. Si pasan más de 5 minutos, revisa que el "Commit" se haya guardado en GitHub. |

Si algo no funciona o no estás segura, mejor pide ayuda antes de seguir intentando — es preferible preguntar que romper algo por error.
