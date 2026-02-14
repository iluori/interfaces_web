# Ejercicio 3: Formulario Estilizado con Validación Visual

## 🎯 Objetivo

Crear un formulario HTML5 con validación nativa y aplicar estilos CSS que proporcionen **feedback visual inmediato** al usuario mediante pseudo-clases.

## 📋 Instrucciones

Se te proporciona un archivo `plantilla_base.html` con un formulario HTML básico sin estilos.

Tu tarea es:
1. Completar el formulario con los campos especificados
2. Añadir atributos de validación HTML5
3. Crear estilos CSS que cambien según el estado de validación
4. Aplicar efectos visuales con pseudo-clases

## 📝 Campos del Formulario

El formulario debe incluir:

1. **Nombre completo** (text, requerido)
2. **Email** (email, requerido)
3. **Teléfono** (tel, requerido, pattern para formato)
4. **Fecha de nacimiento** (date, requerido)
5. **Contraseña** (password, requerido, mínimo 8 caracteres)
6. **URL del sitio web** (url, opcional)
7. **Comentarios** (textarea, opcional)
8. **Botón de envío**

## ✅ Requisitos HTML5

### Atributos de validación que debes usar:

- `required` - Para campos obligatorios
- `type="email"` - Validación automática de email
- `type="tel"` - Para teléfonos
- `type="date"` - Selector de fecha
- `type="url"` - Validación de URLs
- `minlength="8"` - Para la contraseña
- `pattern="[0-9]{9}"` - Para teléfono (9 dígitos)
- `placeholder` - Texto de ayuda en los campos

### Estructura HTML recomendada:

```html
<label for="nombre">Nombre completo:</label>
<input type="text" id="nombre" name="nombre" required>
```

## 🎨 Requisitos CSS

### 1. Estilos base para inputs:

```css
input, textarea {
    padding: 10px;
    font-size: 16px;
    border: 2px solid #ccc;
    border-radius: 4px;
    transition: all 0.3s ease;
}
```

### 2. Pseudo-clases que DEBES implementar:

#### `:focus` - Cuando el campo está activo
```css
input:focus {
    outline: none;
    border-color: #2196F3;
    box-shadow: 0 0 0 3px rgba(33, 150, 243, 0.1);
}
```

#### `:valid` - Cuando el valor es válido
```css
input:valid {
    border-color: #4CAF50; /* Verde */
    background-color: #f1f8f4; /* Fondo verde claro */
}
```

#### `:invalid` - Cuando el valor es inválido
```css
input:invalid {
    border-color: #f44336; /* Rojo */
    background-color: #ffebee; /* Fondo rojo claro */
}
```

#### `:required` - Campos obligatorios
```css
input:required {
    border-left: 4px solid #ff9800; /* Borde naranja izquierdo */
}
```

#### `:optional` - Campos opcionales
```css
input:optional {
    border-left: 4px solid #9e9e9e; /* Borde gris izquierdo */
}
```

### 3. Estilos para el botón:

```css
button {
    background-color: #2196F3;
    color: white;
    padding: 12px 30px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    font-size: 16px;
    transition: background-color 0.3s;
}

button:hover {
    background-color: #1976D2;
}
```

## 🎨 Criterios de Evaluación

| Criterio | Puntos |
|----------|--------|
| Todos los campos del formulario presentes | 1 |
| Atributos de validación correctos (required, type, pattern) | 2 |
| Pseudo-clase `:focus` implementada | 1 |
| Pseudo-clases `:valid` y `:invalid` implementadas | 2 |
| Pseudo-clases `:required` y `:optional` implementadas | 1 |
| Estilos del botón con :hover | 1 |
| Layout ordenado y legible del formulario | 1 |
| Validación W3C HTML y CSS sin errores | 1 |
| **TOTAL** | **10 puntos** |

## 📤 Entrega

**Archivos a entregar:**
- `Apellido_Nombre_Ejercicio3.html`
- `estilos.css`

**Formato:** Carpeta comprimida (.zip)

## 💡 Pistas y Consejos

### Pattern para teléfono español:
```html
<input type="tel" pattern="[0-9]{9}" 
       placeholder="Ej: 612345678" 
       title="Introduce 9 dígitos">
```

### Evitar validación prematura:
A veces no queremos mostrar el error hasta que el usuario haya interactuado con el campo:

```css
/* Solo mostrar error si el campo NO está enfocado */
input:not(:focus):invalid {
    border-color: #f44336;
}
```

### Mensajes de ayuda:
Puedes añadir texto de ayuda usando el atributo `title`:

```html
<input type="password" 
       minlength="8" 
       title="Mínimo 8 caracteres"
       required>
```

### Layout del formulario:
```css
form {
    max-width: 500px;
    margin: 0 auto;
    padding: 2rem;
    background-color: #f5f5f5;
    border-radius: 8px;
}

label {
    display: block;
    margin-top: 1rem;
    margin-bottom: 0.5rem;
    font-weight: bold;
}

input, textarea {
    width: 100%;
    display: block;
}
```

## 🔍 Verificación

### Para probar tu formulario:

1. **Campos vacíos:** Verifica que los campos requeridos muestren estilo inválido
2. **Email incorrecto:** Escribe "texto" en el campo email → debe mostrar error
3. **Email correcto:** Escribe "usuario@example.com" → debe mostrar válido
4. **Teléfono:** Debe aceptar solo 9 dígitos
5. **Contraseña:** Debe requerir mínimo 8 caracteres
6. **Campos opcionales:** Deben verse diferentes visualmente
7. **Focus:** Al hacer clic en un campo debe cambiar su aspecto

## 🎓 Conceptos Clave

### Pseudo-clases de formularios:

| Pseudo-clase | Se aplica cuando... |
|--------------|---------------------|
| `:focus` | El campo está seleccionado (tiene el cursor) |
| `:valid` | El valor cumple con todas las validaciones |
| `:invalid` | El valor NO cumple con las validaciones |
| `:required` | El campo tiene el atributo `required` |
| `:optional` | El campo NO tiene el atributo `required` |

### Buenas prácticas:

✅ Siempre usa `<label>` con el atributo `for`
✅ Proporciona `placeholder` como ayuda visual
✅ Usa `title` para mensajes de error descriptivos
✅ Añade `transition` para efectos suaves
✅ Desactiva el `outline` por defecto solo si añades tu propio estilo de focus

## ❓ Preguntas de Reflexión

Al final de tu CSS, responde en comentarios:

1. ¿Por qué es importante dar feedback visual inmediato en los formularios?
2. ¿Qué ventaja tiene usar `type="email"` en lugar de `type="text"`?
3. ¿Cómo mejora la accesibilidad el uso de `<label>` con el atributo `for`?

## 🔗 Referencias

- [MDN: Validación de formularios](https://developer.mozilla.org/es/docs/Learn/Forms/Form_validation)
- [MDN: Pseudo-clases](https://developer.mozilla.org/es/docs/Web/CSS/Pseudo-classes)
- [HTML5 Input Types](https://developer.mozilla.org/es/docs/Web/HTML/Element/input)

---

¡Un formulario bien diseñado mejora enormemente la experiencia del usuario! 📝✨
