# DevOps - Versionamiento de Código 🚀

[![N|Solid](https://www.elempleo.com/sitios-empresariales/colombia/periferia-it-corp/img/logo-periferia-01.png)](https://periferiaitgroup.com/)

Este repositorio tiene como objetivo generar una guía para el desarrollo de una práctica de versionamiento con github, aprender los comandos básicos y manejar la herramienta GitHub.

# Requisitos 🛠️

  - Crear cuenta en [GitHub].
  - Instalar el cliente de [Git] en el equipo local.
  - Instalar un editor de texto como [Visual Studio Code]. (Puede usar bloc de notas)

# Archivos 📋 
Es necesario descargar este repositorio de forma local, para poder usar los archivos de ejemplo que representan los requisitos para integrar y ejecutar esta practica.
| Archivo   |      Descripción      |
|----------|:-------------:|
| index.html |  Linea base, versión inicial del proyecto. |
| feature-body.txt |  Archivo que contiene la solución del requisito del body, este se debe agregar en el archivo index.html de la rama del feature/body   |
| feature-footer.txt | Archivo que contiene la solución del requisito del footer, este se debe agregar en el archivo index.html de la rama del feature/footer  |

# Planteamiento 📄

Un proyecto de desarrollo tiene como objetivo realizar un lanzamiento de su sitio web, actualmente se encuentra en desarrollo y ya se tiene el header de la página, se tienen los dos siguientes requisitos para realizar el lanzamiento del producto mínimo viable (MVP).

  - Desarrollo del body del sitio web.
  - Desarrollo del footer del sitio web.

# Configuración Inicial ⚙️

Configurar nombre y correo electrónico:

```sh
git config --global user.name "Nombre"
git config --global user.email correo@gmail.com
git config --list
```
**Crear un repositorio en GitHub llamado practica-devops**
# Planeación y ejecución del flujo de trabajo ⚙️

Se requiere llevar un control del código fuente con el modelo de gitflow, para lo cual se plantea la siguiente estructura inicial de branching:

  - main -----> tag: v0.1
     - develop
        - feature/body
        - feature/footer

#### Clonar repositorio practica-devops
```sh
git clone url_repo
```
#### Crear tag
```sh
git checkout main
git tag v0.1
git push --tags
```
#### Crear rama develop
```sh
git checkout -b develop
git push origin develop
```
#### Crear rama feature/body
```sh
git checkout -b feature/body
```
Agregar el contenido del archivo de texto **feature-body.txt** al archivo **index.html** debajo del **header** del html
#### Commit y subir cambios a feature/body
```sh
git add .
git commit -m "Desarrollo terminado de body"
git push origin feature/body
```

#### Crear rama feature/footer
```sh
git checkout develop
git checkout -b feature/footer
```
Agregar el contenido del archivo de texto del **feature-footer.txt** al archivo **index.html** debajo del **body** del html
#### Commit y subir cambios a feature/footer
```sh
git add .
git commit -m "Desarrollo terminado de footer"
git push origin feature/footer
```
------
Una vez completado el desarrollo de los requisitos del proyecto se debe integrar a las ramas en el siguiente orden para pasar por un flujo de pruebas y finalmente su lanzamiento:
> Eliminar ramas temporales feature una vez se integren.
  - feature/body -----> delete
  - feature/footer -----> delete
     - develop
        - release/mvp
            - main -----> **(No integrar, continué al siguiente paso)**
            
#### Integrar ramas feature a develop
```sh
git checkout develop
git merge feature/body
git merge feature/footer
```
#### Si genera error por el merge, resuelva el merge y luego ejecute los siguientes comandos integrar a develop
```sh
git add .
git commit -m "se resuelven conflictos de merge de feature a develop"
git push --set-upstream origin develop
```
#### Eliminar ramas features remotamente
```sh
git push origin --delete feature/body
git push origin --delete feature/footer
```
#### Eliminar ramas features localmente
```sh
git branch -d feature/body
git branch -d feature/footer
```
#### Crear rama release
```sh
git checkout -b release/mvp
```
------
El equipo de pruebas encuentra un error en el ambiente de QA y debe cambiar el nombre del sitio web, el equipo de desarrollo debe solucionarlo aplicando el siguiente flujo:
> Eliminar ramas temporales bugfix y release/mpv una vez se integren en el flujo completo.
  - release/mvp -----> tag: v1.0-alpha
     - bugfix/nombre-sitio
        - develop
        - release/mvp -----> tag: v1.0-alpha
            - main -----> tag: v1.0
            
#### Crear bugfix
```sh
git checkout release/mvp
git checkout -b bugfix/nombre-sitio
```
#### Corregir bug
Modificar el título en la siguiente sección del archivo index.html por **DevOps Professional**
```
<header>
  <h2>Versionamiento de código con GitHub</h2>
</header>
```

#### Commit y subir cambios

```sh
git add .
git commit -m "Corrección de nombre"
git push origin bugfix/nombre-sitio
```

#### Integrar a develop
```sh
git checkout develop
git merge bugfix/nombre-sitio
```
#### Integrar a release
```sh
git checkout release/mvp
git merge bugfix/nombre-sitio
```
#### Eliminar bugfix remotamente
```sh
git push origin --delete bugfix/nombre-sitio
```
#### Eliminar bugfix localmente
```sh
git branch -d bugfix/nombre-sitio
```
#### Crear tag release
```sh
git checkout release/mvp
git tag v1.0-alpha
git push --tags
```
#### Integrar a main y crear tag
```sh
git checkout main
git merge release/mvp
git tag v1.0
git push --tags
```

Finalmente se cumple el flujo completo y se tiene productivo el desarrollo de los requisitos para el MVP.

> NOTA: Para proyectos empresariales, se establecen políticas y restricciones para evitar la integración directa por linea de comandos a la rama main y develop, este proceso se realiza por medio de un pull request para revisar y aprobar los cambios.

# Autores ✒️

* **John Alexander Cruz** - *Versión Inicial* - [jhonalexander0809](https://github.com/jhonalexander0809)


   [visual studio code]: <https://code.visualstudio.com>
   [git]: <https://git-scm.com>
   [github]: <https://github.com>
