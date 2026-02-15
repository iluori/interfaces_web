# 01. Instalación y Configuración de Tailwind CSS

## Metodología 1: Instalación mediante CDN
Esta instalación no es recomendada para producción pero sí para pruebas rápidas.

Para instalarlo se añade ```<script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>``` dentro de la etiqueta ```<head>``` del HTML.

## Metodología 2: Instalación mediante CLI
Es la forma profesional. Se utiliza la línea de comandos y NPM.
Debemos tener instalado previamente ```Node.js```.

### Pasos de instalación
1. Inicializar el proyecto:
   Abre la terminal en tu carpeta de trabajo y pon: ```npm init -y```
   Esto crea el archivo ```package.jason```.

2. Instalar Tailwind CSS
   En la terminal: ```npm install tailwindcss @tailwindcss/cli```
   Esto crea la carpeta ```node_modules``` y el archivo ```package-lock.sjon```.

3. Crear estructura de archivos:
   1- Crea una carpeta ```src```
   2- Dentro crea una carpeta ```css```
   3- Dentro de ```src/css```, crea un archivo ```tailwind.css```
   4- En ```src```, crea tu ```index.html```

4. Configurar Tailwind
   El archivo ```src/css/tailwind.css``` es importante y debe tener la importación de tailwind: ```@import "tailwindcss";```

5. Compilar el CSS
   Ejecutamos el comando CLI.
   ```npx @tailwindcss/cli -i ./src/css/tailwind.css -o -/src/css/estilos.css -watch```

6. Vincular en HTML
   En ```index.html```, enlaza el archivo generado ```estilos.css```: ```<link rel="stylesheet" href="css/estilos.css">```
