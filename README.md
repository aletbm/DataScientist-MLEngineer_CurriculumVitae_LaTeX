# 📄 CV - Alexander D. Rios

Este repositorio contiene el código fuente de mi currículum vitae, escrito en LaTeX. A continuación, se detallan las instrucciones para editar, compilar y visualizar el documento en Visual Studio Code.

## 🚀 Empezando

### 1. Requisitos previos

Para poder compilar el documento LaTeX y generar el PDF, necesitas tener instalado lo siguiente:

* **Visual Studio Code**
* **Git**
* Una distribución de LaTeX:
    * [**MiKTeX**](https://miktex.org/) (recomendado para Windows)
    * [**TeX Live**](https://www.tug.org/texlive/) (recomendado para Linux/macOS)
* **Perl**: Es un requisito indispensable para que `latexmk` funcione. Si no lo tienes, instálalo desde [**Strawberry Perl**](http://strawberryperl.com/) para Windows.

### 2. Sincronizar el proyecto

Si tu proyecto está en Overleaf, la forma más sencilla de sincronizarlo con tu entorno local es a través de Git.

1.  En tu proyecto de Overleaf, ve a **Menú > Sincronizar > Git**.
2.  Copia la URL del repositorio Git.
3.  Abre una terminal en VS Code y clona el proyecto con el siguiente comando:
    ```bash
    git clone [URL_DE_TU_PROYECTO]
    ```

---

## 🔧 Configuración de VS Code y MiKTeX

### 1. Instalar la extensión LaTeX Workshop

Para una experiencia de edición y visualización óptima, instala la extensión oficial de LaTeX en VS Code:

1.  Abre la pestaña de **Extensiones** (`Ctrl+Shift+X`).
2.  Busca y haz clic en **Instalar** para la extensión **`LaTeX Workshop`**.

### 2. Configurar el motor de compilación (`xelatex`)

Debido a que tu CV utiliza paquetes como `fontspec`, es necesario usar el motor de compilación `xelatex`.

1.  Abre la **Paleta de Comandos** (`Ctrl+Shift+P`).
2.  Busca y selecciona `Preferences: Open Settings (JSON)`.
3.  Añade o modifica la siguiente configuración para forzar a la extensión a usar `xelatex`:

    ```json
    "latex-workshop.latex.recipe.default": "latexmk (xelatex)",
    "latex-workshop.latex.tools": [
        {
            "name": "xelatex",
            "command": "xelatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "%DOC%"
            ]
        },
        {
            "name": "latexmk",
            "command": "latexmk",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "-pdf",
                "-shell-escape",
                "-xelatex",
                "%DOC%"
            ]
        }
    ],
    "latex-workshop.latex.recipes": [
        {
          "name": "latexmk (xelatex)",
          "tools": [
            "latexmk"
          ]
        },
        {
          "name": "xelatex",
          "tools": [
            "xelatex"
          ]
        }
    ]
    ```

### 3. Actualizar los paquetes de MiKTeX

Si encuentras errores de "Undefined control sequence" en paquetes como `polyglossia`, es probable que tus paquetes estén desactualizados.

1.  Abre la aplicación **MiKTeX Console**.
2.  Ve a **Updates** y haz clic en **Check for updates**.
3.  Haz clic en **Update now** para instalar todos los paquetes más recientes.

---

## 👨‍💻 Editar y Visualizar el CV

### 1. Limpiar el proyecto

Si una compilación anterior falló, el proyecto puede quedar en un estado de error. Para solucionar esto:

* Abre la **Paleta de Comandos** (`Ctrl+Shift+P`).
* Selecciona `LaTeX Workshop: Clean up auxiliary files`.

### 2. Compilar el PDF

* **Atajo de teclado**: Presiona `Ctrl+Alt+B`.
* **Paleta de comandos**: Abre la paleta (`Ctrl+Shift+P`) y selecciona `LaTeX Workshop: Build with Recipe`.

### 3. Visualizar el PDF

* **Vista previa integrada**: Haz clic derecho en el archivo `.tex` y selecciona `View LaTeX PDF file` > `View in VSCode Tab`.
* **Abrir en el navegador**: Haz clic derecho en el archivo `.tex` y selecciona `View in Web Browser`.