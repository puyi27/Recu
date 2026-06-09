# 🗺️ GUIÓN DE BATALLA: EXAMEN DIW (20:00H)

Sigue este guion paso a paso para no bloquearte durante el examen. Si te atascas en un paso, sáltatelo y ve al siguiente; es mejor tener el 80% del examen a medias que solo el 20% perfecto.

---

## 🕒 FASE 1: Preparación (19:45 - 20:00)
- [ ] **Abre tus herramientas:** Abre VS Code y el navegador (Chrome/Edge).
- [ ] **Abre tus chuletas:** Abre `guia-ud5.html`, `guia-extras-examen.html` y `simulacro-examen.html` en el navegador para ver qué hacen, y también en VS Code por si tienes que copiar código.
- [ ] **Prepara la consola:** En tu navegador, pulsa `F12` y deja abierta la pestaña **Console**. Aquí verás si te has equivocado al escribir el nombre de una variable.
- [ ] **Ponte cómodo:** Agua, cero distracciones y mentalidad fría.

---

## 🕒 FASE 2: Arranque del Examen (Minuto 0 al 10)
- [ ] **Lee todo el examen:** No empieces a teclear a lo loco. Lee todas las preguntas para saber qué te piden.
- [ ] **Estructura Semántica:** Crea tu `index.html` e importa el CSS y jQuery.
  - Escribe el esqueleto obligatorio (búscalo en `guia-extras-examen.html`): `<header>`, `<main>`, `<section>`, `<footer>`.
  - ¡Ojo! No uses solo `<div>`.

---

## 🕒 FASE 3: Maquetación y CSS (Minuto 10 al 30)
*El profesor quiere ver si sabes colocar las cosas en la pantalla.*
- [ ] **CSS Grid es tu dios:** Si te piden hacer una galería de fotos o tarjetas de productos, vete a `guia-extras-examen.html`, copia el código de `grid-template-columns: repeat(auto-fit...)` y pégalo. Ya tienes el responsive hecho.
- [ ] **Flexbox para centrar:** Si te piden que un logo o un texto quede perfectamente centrado, usa `display: flex; justify-content: center; align-items: center;`.
- [ ] **No pierdas el tiempo:** Si un color no es exactamente el azul que pide el profesor, da igual. Pasa al siguiente ejercicio. La lógica de Javascript da más puntos que un color exacto.

---

## 🕒 FASE 4: La Lógica y DOM con jQuery (Minuto 30 al 60)
*Aquí es donde se aprueba el examen.*
- [ ] **Siempre el `document.ready`:** Todo tu código jQuery debe ir dentro de `$(document).ready(function() { ... });`.
- [ ] **Validación de Formularios:** Si hay un formulario, el 100% de las veces tienes que poner `e.preventDefault()` en el evento `submit`. Búscalo en tu simulacro.
- [ ] **Eventos de botones:** Si te piden ocultar o mostrar cosas, usa `.hide()`, `.fadeIn()`, o `.slideToggle()` (Mírate el ejercicio del Acordeón).
- [ ] **Clases CSS Dinámicas:** Si te piden que algo "cambie de estado" (ej. Modo Noche, o "Marcar Tarea como Completada"), crea una clase en tu CSS y ponla con `toggleClass()` desde jQuery.

---

## 🕒 FASE 5: Los Jefes Finales (Minuto 60 al final)
*Estos ejercicios son para sacar el 8, 9 o 10.*
- [ ] **¿Pide cargar datos externos? (Fetch):** Vete a `guia-extras-examen.html`, copia el bloque de `fetch()` y adáptalo a la URL que te dé el profesor.
- [ ] **¿Pide un gráfico o dibujo? (Canvas):** Recuerda la Regla de Oro: seleccionar el Canvas -> `getContext('2d')` -> `fillStyle` -> `fillRect` o `arc`. (Está en `guia-ud5.html` y en el simulacro).
- [ ] **¿Pide una animación rara? (SVG):** Si te pide un recorrido curvo, copia el `<path>` y el `<animateMotion>` de tu chuleta y juega con los números.
- [ ] **¿Pide Drag & Drop?:** Cuidado con "la trampa". Recuerda que la zona donde sueltas la caja NECESITA atrapar el evento `ondragover` y hacer `e.preventDefault()`. Si no, nunca se soltará.

---

## 🚨 PROTOCOLO DE EMERGENCIA (Si te quedas en blanco)
1. **"El botón no hace nada":** Tienes un error de sintaxis. Abre la consola (F12). Probablemente has puesto `$("#boton")` pero en el HTML el botón se llama `<button class="boton">`. (Recuerda: `#` para ID, `.` para clase).
2. **"La página parpadea y vuelve al inicio":** Tienes un formulario o un enlace `<a href="">` y se te ha olvidado poner `e.preventDefault()`.
3. **"No me acuerdo de cómo se escribía X":** Para eso tienes las 3 guías. Haz `Ctrl + F` (Buscar) en tu editor y pon la palabra clave (ej: `canvas`, `fetch`, `grid`, `animacion`).

¡Respira hondo, tienes todas las respuestas en esa carpeta! 💻🔥
