# Optimización para ciencia de datos

Libro/blog en [Quarto](https://quarto.org), publicado en GitHub Pages.

## Estructura

```
_quarto.yml          configuración (capítulos, tema, publicación)
_macros.qmd          macros LaTeX (\R, \norm, \inner, \prox, ...)
references.bib       bibliografía
capNN/capNN.qmd      un capítulo: solo incluye sus secciones
capNN/sMM-*.qmd      una sección (aquí se escribe)
apendices/           guía de formato con ejemplos
```

Para agregar una sección: crear `capNN/sMM-nombre.qmd` (empieza con `## Título {#sec-nombre}`) y añadir su `{{< include >}}` en `capNN/capNN.qmd`.

## Uso local

```bash
pip install -r requirements.txt
quarto preview            # vista previa con recarga en vivo
```

## Publicar en GitHub Pages

Una sola vez:

1. Crear el repo `convexcat/opt_notes` en GitHub y hacer push de `main`.
2. `quarto publish gh-pages` (crea la rama `gh-pages`).
3. En GitHub: Settings → Pages → Source: rama `gh-pages`, carpeta `/ (root)`.

Después, cada push a `main` ejecuta `.github/workflows/publish.yml` y republica. Si ejecutas código pesado, usa `quarto render` localmente y sube la carpeta `_freeze/` (con `freeze: auto` no se re-ejecuta lo que no cambió).
