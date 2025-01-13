# Creación y configuración de repositorios basados en Jupyter Book

## 1. Creación de un ambiente Conda

```shell
# Actualización de Conda
conda update conda

# Borrado del ambiente (si es que existe)
# conda remove -n datos-geoespaciales-biodiversidad

# Creación y configuración del entorno, e instalación de mamba
conda create -n datos-geoespaciales-biodiversidad -c conda-forge --strict-channel-priority mamba

# Activación del entorno
conda activate datos-geoespaciales-biodiversidad

# Instalación de módulos
mamba install -c conda-forge --strict-channel-priority python jupyter jupyter-book ghp-import

# Desactivación del ambiente
conda deactivate
```

## 2. Creación del Jupyter Book principal y publicación inicial del sitio web en GitHub Pages

```shell
conda activate datos-geoespaciales-biodiversidad

# Creación del Jupyter Book con una plantilla inicial
jupyter-book create datos-geoespaciales-biodiversidad.github.io

# Generación de archivos HTML (en el subdirectorio _build/html)
jupyter-book build datos-geoespaciales-biodiversidad.github.io

# En este punto, debe crearse en GitHub el repositorio datos-geoespaciales-biodiversidad.github.io

# Configuración del repositorio local y su branch main (para manejar los archivos fuente)
cd datos-geoespaciales-biodiversidad.github.io
git init
git add .
git commit -m "Commit inicial"
git branch -M main
git remote add origin git@github.com:datos-geoespaciales-biodiversidad/datos-geoespaciales-biodiversidad.github.io.git
git push -u origin main

# Creación del branch gh-pages (para manejar los archivos HTML publicados)
ghp-import -n -p -f _build/html

# En este punto, se configura el repositorio para buscar los archivos de GH Pages en la rama gh-pages
# El sitio debe estar disponible en https://datos-geoespaciales-biodiversidad.github.io/

conda deactivate
```

## 3. Creación de un Jupyter Book para el curso de Python

```shell
conda activate datos-geoespaciales-biodiversidad

# Creación del Jupyter Book con una plantilla inicial
jupyter-book create python
# Generación de archivos HTML (en el subdirectorio _build/html)
jupyter-book build python

# En este punto, se crea en GitHub el repositorio python

# Configuración del repositorio local y su branch main (para manejar los archivos fuente)
cd python
git init
git add .
git commit -m "Commit inicial"
git branch -M main
git remote add origin git@github.com:datos-geoespaciales-biodiversidad/python.git
git push -u origin main

# Creación del branch gh-pages (para manejar los archivos HTML publicados)
ghp-import -n -p -f _build/html

# En este punto, se configura el repositorio para buscar los archivos de GH Pages en la rama gh-pages
# El sitio debe estar disponible en https://datos-geoespaciales-biodiversidad.github.io/python/
```

## 4. Publicación de modificaciones

```shell
# Generación de archivos HTML (debe hacerse desde el directorio padre del Jupyter Book)
jupyter-book build python

cd python

# Aplicación de cambios en el branch main
git status
git add .
git commit -m "###Comentario###"
git push

# Aplicación de cambios en el branch gh-pages
ghp-import -n -p -f _build/html
```