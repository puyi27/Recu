# 📖 RESUMEN EXPRÉS: DIW UD5 (LEER ANTES DE ENTRAR)

Aquí tienes el resumen teórico "para vagos", rápido y directo al grano para que lo leas en el metro o 5 minutos antes de entrar.

---

### 1. JQUERY Y DOM (Interactividad Básica)
- **Selectores:** Con `#` pillas IDs (únicos), con `.` pillas Clases (varios).
- **El terror de los formularios:** Cuando pulsas un botón `type="submit"`, la página se recarga por defecto y pierdes todo. **Solución:** Atrapas el evento y escribes `e.preventDefault()`.
- **Modificar al vuelo:** `.css("color", "red")` para estilos, `.attr("src", "foto.jpg")` para cambiar imágenes, `.toggleClass("clase")` para añadir/quitar clases tipo "Modo noche".

### 2. FETCH API (Cargar datos)
- Sirve para conectarte a un archivo o servidor (ej: un `.json`) e inyectar datos en tu web sin recargarla.
- **La chuleta mental:** `fetch(url) -> .then(convertir a json) -> .then(pintar en HTML con un bucle)`.

### 3. SEMÁNTICA HTML5 Y ACCESIBILIDAD
- A los profesores de Diseño no les vale que uses `<div>` para todo.
- Usa `<header>` para la cabecera, `<main>` para el cuerpo (obligatorio y único), y `<footer>`.
- **Para los ciegos/teclados:** Pon `tabindex="0"` a los botones hechos a mano para que el Tabulador llegue a ellos, y `aria-label="texto"` para describir iconos que no tienen texto al lado.

### 4. API CANVAS (El Lienzo de Dibujo)
- Funciona por coordenadas `(x, y)`. La `(0, 0)` está **arriba a la izquierda**.
- Tienes que pedir siempre el pincel en Javascript con `getContext("2d")`.
- Si quieres animar algo, la regla de oro es: **Borra el lienzo entero (`clearRect`) -> Dibuja la nueva posición -> Repite.** Si no borras, pintarás un rastro infinito.

### 5. GRÁFICOS SVG
- **Diferencia clave:** Canvas dibuja píxeles (se pixela si amplías), SVG dibuja vectores matemáticos (calidad infinita siempre).
- El camino (la línea invisible por donde se mueven las cosas) se dibuja en la etiqueta `<path d="...">`. En esa `d`, la letra `M` significa "mover el lápiz aquí" y la `Q` "hacer una curva".
- **Animar en SVG:** Metes un `<animateMotion>` DENTRO de la imagen que quieres mover, y le dices que siga al camino.

### 6. DRAG & DROP (Arrastrar)
Para que algo se pueda arrastrar y soltar tienes que programar 3 pasos sí o sí:
1. Poner `draggable="true"` en el HTML al objeto que quieres mover.
2. Al empezar a arrastrar, guardas su ID en la memoria (`setData`).
3. **¡La Trampa!:** La caja de destino no admite que le tiren cosas por defecto. Tienes que atrapar el evento `ondragover` y hacer un `preventDefault()` para anular esa prohibición de seguridad. Luego ya en el evento `ondrop`, lo recuperas y lo mueves físicamente.

### 7. WEB STORAGE (Guardar variables)
Para que la web "recuerde" cosas como tu nombre o tu High Score si recargas la página:
- `localStorage`: Guarda los datos para siempre (hasta que borres cookies/caché).
- `sessionStorage`: Guarda los datos solo mientras la pestaña esté abierta.

---
*Con esto, la plantilla de copiar y pegar, y media hora de práctica, el examen está reventado. ¡Cierra los ojos, repasa mentalmente y al lío!*
