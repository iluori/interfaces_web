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


# 02. Conceptos Base y Preflight
Preflight es un conjuntod e estilos bas que incluye Tailwind para resetear los estilos prederterminados de los navegadores. Asegura una consistencia de visionado en todos los navegadores desde el inicio y obtienes un control total ya que eliminamos el factor de que el navegador decida por ti.

## Cómo dar estilo
Usando ```Utility Classes```.
Como por ejemplo: ```<h1 clas="text-4x1 font-bold mb-4>Título Grand ey Negrita</h1>```

## Estilos Globales ```@layer base```
Se inserta en tu archivo CSS principal.
```
@import "tailwindcss";

@layer base {
  h1 {
    @apply text-4xl font-bold mb-4;
  }
}
```
Esto hará que, que todos los h1 tengan el mismo estilo.


# 03. Colores y Personalización

## Uso básico

Los colores se aplican combinando la propiedad con el nombre del color y su intensidad (50-950).
- Texto: ```text-color-intensidad```
- Fondo: ```bg-color-intensidad```
- Borde: ```border-color-intensidad```

## Opacidad transparencia

Barra inclinada ```/``` seguida del porcentaje de opacidad. Ejemplo: ```text-pink-600/50``` (50% de transparencia).
