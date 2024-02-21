# MkDocs
Este repositorio es para realizar la página 6.2 de IAW donde trabajaremos con MkDocs.


## Primeros pasos que tendremos que hacer.

1. Como primer paso tendremos que hacer uso del siguiente comando : `docker run --rm -it -p 8000:8000 -v "$PWD":/docs squidfunk/mkdocs-material new .` Este comando realmente nos permitirá generar la estructura de un proyecto *_MK2_* desde cero.


2. Tendremos que crear un sitio llamado `about.md` dentro de la carpeta docs.

    ```

    .
    ├── README.md
    ├── docs
    │   ├── about.md
    │   └── index.md
    └── mkdocs.yml

    ```
3. Añadimos el siguiente *_contenido_* al archivo *_mkdocs.yml_* 

    ```
    site_name: Sitio de Joaquín para IAW

    nav:
        - Principal: index.md
        - Acerca de: about.md

    theme: material #Se puede cambiar el tema que queramos, pero tendríamos que cambiar el contenedor.

    ```

4. Si queremos generar un sitio web `servidor` desde nuestra consola, hacemos uso del siguiente comando `docker run --rm -it -p 8000:8000 -v "$PWD":/docs squidfunk/mkdocs-material`

