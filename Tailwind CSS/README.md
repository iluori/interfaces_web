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

```<h1 class="bg-black/90 text-pink-900/50">Título con transparencias</h1>```

<img src="img/img1.jpg" width="300" height="200" alt="descripción">

## Agrupación de Estilos

Si quieres aplicar el mismco color a más de un elemento, a veces puedes aguprarlos en un ```<div>``` padre.

(img2)

**Hay que tener cuidado con la herencia.**

### Arbitrary Variants ```[&>*]```

Si realmente quieres forzar que todos los hijos tengan una propiedad no heredable (como padding o background), puedes usar ```[&>*]```:

```
<div class="[&>*]:bg-blue-500 [&>*]:p-4">
    <p>Soy azul con padding</p>
    <p>Yo también</p>
</div>
```

(img3)

## Valores Personalizados (Arbitrary Values)

Si un color no está en la paleta de Tailwind solo debes usar corchetes ```[]```

```<h1 class="bg-[#2E86AB] text-white">Título con color personalizado directo</h1>```

(img4)

## Ejemplo Práctico: Iconos SVG

Vamos a usar un icono SVG externo (ej. de boxicons.com) y controlarlo con Tailwind.

1. Copiamos el SVG.
2. **Importante**: Eliminamos los estilos en línea que traiga (`width`, `height`, `fill`) para que Tailwind pueda controlarlos.
3. Añadimos nuestras clases: `w-`, `h-`, `fill-`.

```
<svg  xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"  class="w-12 h-12 fill-[#ff6600]">
   <!--Boxicons v3.0.8 https://boxicons.com | License  https://docs.boxicons.com/free-->
   <path d="M18.76 5.24A3.5 3.5 0 0 0 15.5 3c-.31 0-.63.04-.93.13a3.487 3.487 0 0 0-5.14 0C9.12 3.04 8.81 3 8.5 3c-1.47 0-2.75.91-3.26 2.24a3.498 3.498 0 0 0-1.22 5.73c0 .08-.02.15 0 .22l2 10c.09.47.5.8.98.8h10c.48 0 .89-.34.98-.8l2-10c.02-.08 0-.15 0-.22.63-.63 1.02-1.51 1.02-2.47 0-1.47-.91-2.75-2.24-3.26M6.23 7.03a.99.99 0 0 0 .8-.8c.18-.97 1.33-1.55 2.24-1 .24.14.52.18.79.11.27-.08.49-.26.62-.5a1.486 1.486 0 0 1 2.66 0c.13.25.35.43.62.5.27.08.55.04.79-.11.91-.54 2.06.03 2.24 1 .07.41.39.73.8.8a1.498 1.498 0 0 1-.27 2.97H6.5a1.498 1.498 0 0 1-.27-2.97M13.4 12l-.8 8h-1.19l-.8-8zm-7.18 0H8.6l.8 8H7.82zm9.96 8H14.6l.8-8h2.38z"></path>
   </svg>
```

(img5)


# 04. Tipografía

## Fuente Predeterminada

Por defecto, Tailwind aplica la fuente Sans-Serif `(ui-sans-serif)`.

Si aplicas una clase de fuente al body, como font-family es una propiedad **heredable**, se aplicará a toda la página.

## Fuentes Personalizadas (Google Fonts)

Para usar una fuente que no sea estándar, lo ideal es usar **Google Fonts** y valores arbitrarios.

### Pasos:
1. Ve a [Google Fonts](https://fonts.google.com/).
2. Busca una fuente.
3. Selecciona los estilos que quieras.
4. Copia los `<link>` que te proporciona y pégalos en el `<head>` de tu HTML.

```
<head>
  <!-- ... otros meta tags ... -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:ital,wght@0,200..800;1,200..800&display=swap" rel="stylesheet">
</head>
```

### Usar la fuente personalizada

Ahora usa la sintaxis de **corchetes** `font-[Nombre_Fuente]`.

```
<body class="font-[Plus_Jakarta_Sans]">
   <h1 class="text-3xl font-bold text-center mt-8">¡Hola, Tailwind CSS!</h1>
   <p class="text-center mt-4 text-gray-600">Este es un proyecto de ejemplo utilizando Tailwind CSS.</p>
</body>
```

(img6)

