# Mapa del portal de la Sede Medellín

Visor estático de las conexiones públicas de `medellin.unal.edu.co`, con búsqueda,
filtros por sección y estado, recorridos desde la portada y reportes descargables.

## Publicar en GitHub Pages

1. Sube los archivos de esta carpeta a la raíz del repositorio, en la rama `gh-pages`.
2. En **Settings → Pages → Build and deployment**, selecciona **Deploy from a branch**.
3. Selecciona la rama **gh-pages**, la carpeta **/ (root)** y pulsa **Save**.
4. GitHub mostrará la dirección publicada en esa misma pantalla al terminar el despliegue.

La página inicial es `index.html`. Los enlaces a los CSV son relativos, por lo que
funcionan tanto en un sitio de proyecto como en la raíz de un dominio.

## Contenido

- `index.html`: mapa interactivo y tabla de resultados.
- `errores-resumen.csv`: una fila por URL problemática.
- `errores.csv`: detalle de páginas de origen, textos de enlace y recorridos.

Es una fotografía del rastreo cuya fecha aparece en el visor. La publicación no
ejecuta nuevos rastreos. El visor identifica recursos pendientes, exclusiones y
enlaces externos sin comprobar; no constituye un inventario de artículos privados
o huérfanos de Joomla. Los fallos HTTP corresponden al momento de la comprobación.

Para actualizarlo, vuelve a generar los resultados localmente y reemplaza estos
tres archivos en el repositorio. No requiere dependencias ni servicios externos.

## Actualizar desde el proyecto local

En este repositorio, `main` conserva los archivos y `gh-pages` publica la página.
Desde la raíz del proyecto local:

```bash
python3 mapa-sede-medellin/preparar_publicacion.py
cd mapa-sede-medellin/publicacion-github
git add index.html errores.csv errores-resumen.csv README.md .nojekyll
git commit -m "Actualizar mapa y reportes"
git push origin main main:gh-pages
```

GitHub vuelve a desplegar al actualizar `gh-pages`. No se fuerza ni se sobrescribe
el historial remoto; si hay cambios hechos desde otra computadora, hay que
integrarlos antes de publicar.

Guía oficial: https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site
