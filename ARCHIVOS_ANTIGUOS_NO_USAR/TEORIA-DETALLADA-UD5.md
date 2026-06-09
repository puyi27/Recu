# 🧠 LA BIBLIA DE DIW: UD5 (TEORÍA DETALLADA)

Si tienes tiempo antes del examen y quieres **entender el porqué** de cada línea de código que vas a copiar y pegar, lee este documento. Entender los conceptos te salvará si el profesor te cambia el enunciado y tienes que improvisar.

---

## CAPÍTULO 1: El DOM y la Magia de jQuery

El DOM (Document Object Model) no es más que tu archivo HTML convertido en un "árbol" de cajas que Javascript puede leer y modificar. jQuery es una librería que crearon hace años para hacer que modificar ese árbol fuera facilísimo.

### El misterio del `$(document).ready()`
El navegador lee el HTML de arriba a abajo. Si intentas ponerle un evento a un botón (`$("#btn").click()`) antes de que el navegador lo haya dibujado en la pantalla, Javascript dirá: *"Ese botón no existe"*, y no hará nada.
Por eso TODO el código jQuery se mete dentro del `$(document).ready(...)`. Es como decirle a Javascript: *"Cierra los ojos, espera a que termine de cargar toda la página, y entonces ejecutas esto"*.

### ¿Por qué `e.preventDefault()` nos salva la vida?
Los enlaces (`<a>`) y los botones de los formularios (`<button type="submit">`) tienen comportamientos "por defecto" (Default) muy agresivos: quieren irse de tu página o quieren recargarla.
Cuando escribes `function(e)`, esa `e` es la información del "Evento" que acaba de ocurrir (el click). Si a ese evento le dices `e.preventDefault()`, le estás cortando las alas. Le dices: *"No hagas lo que haces normalmente, no recargues la página. Quédate quieto que yo me encargo por Javascript"*.

---

## CAPÍTULO 2: Semántica HTML5 y Accesibilidad

Antes, las páginas web eran una sopa de `<div id="cabecera">`, `<div id="pie">`, etc. Para ti eso tiene sentido, pero para Google (SEO) o para el lector de pantalla de un ciego, son solo cajas vacías.

HTML5 inventó etiquetas con "significado" (Semántica):
- `<header>`: Para el menú y el logo.
- `<main>`: Para el contenido principal. Solo puede haber uno por página.
- `<footer>`: Para el copyright y enlaces legales.
- `<section>` y `<article>`: Para agrupar cosas.

**Accesibilidad:** Si programas un botón usando un simple `<div>`, un usuario ciego que navega con la tecla Tabulador nunca llegará a él, porque el navegador no sabe que es interactivo. Para arreglarlo, le pones `tabindex="0"` (para que se pueda tabular) y si es un icono sin texto, le pones `aria-label="Botón de enviar"` para que el ordenador se lo lea en voz alta.

---

## CAPÍTULO 3: Web Storage (La memoria del navegador)

Antiguamente, para que una web recordara tu nombre al recargar, había que usar Cookies, que son un dolor de cabeza. HTML5 trajo el Web Storage, que es literalmente un diccionario súper sencillo integrado en el navegador.

- **`localStorage`**: Lo que guardes aquí se queda guardado para siempre en ese ordenador y en ese navegador. Aunque lo cierres, apagues el PC o te vayas de vacaciones.
- **`sessionStorage`**: Lo que guardes aquí sufre amnesia en cuanto cierras la pestaña.

**¿Cómo funciona?**
Es un sistema de "Llave" y "Valor".
- `localStorage.setItem("usuario", "Angel")`: Creas la llave "usuario" y metes "Angel".
- `localStorage.getItem("usuario")`: Te devuelve "Angel".

*Truco avanzado:* El Storage solo admite TEXTO. Si quieres guardar un array o un objeto entero, tienes que convertirlo a texto con `JSON.stringify(objeto)` al guardarlo, y volverlo a convertir a objeto con `JSON.parse(texto)` al sacarlo.

---

## CAPÍTULO 4: Drag & Drop (La mochila de datos)

Mover una caja arrastrándola parece magia, pero en HTML5 es un protocolo muy estricto de eventos. Imagina que el ratón es un cartero.

1. Al objeto que quieres mover le pones `draggable="true"`.
2. Cuando haces click y arrastras, salta el evento `dragstart`. En ese momento, coges la ID del objeto y se la metes en "la mochila" al cartero. Esa mochila invisible en código se llama `dataTransfer.setData(...)`.
3. Mientras mueves el ratón, pasas por encima de otras cajas (`dragover`). Por defecto, los navegadores **prohíben terminantemente** que se suelten cosas encima de otras cajas por seguridad. Por eso tienes que atrapar el evento `dragover` de la caja destino y aplicarle el famoso `e.preventDefault()`. Es la llave que abre la puerta.
4. Cuando sueltas el ratón, salta el evento `drop`. El cartero abre la mochila, saca el ID del objeto (`getData()`) y usa ese ID para arrancar el objeto físico de su sitio antiguo y pegarlo en el nuevo (`appendChild` o `.append()` en jQuery).

---

## CAPÍTULO 5: Canvas (El lienzo tonto de píxeles)

El elemento `<canvas>` es, literalmente, un trozo de papel en blanco de X por Y píxeles. 
La clave para entender el Canvas es saber que **no tiene memoria**. Si tú le dices "Dibuja un círculo rojo", él mancha los píxeles de rojo. Pero al segundo siguiente, él ya no sabe que ahí hay un círculo; solo ve un montón de píxeles manchados.

Por eso las animaciones de Canvas son difíciles. Para mover un coche en Canvas de izquierda a derecha, tienes que hacerlo como en los cuadernillos de dibujo antiguos (Stop-Motion):
1. **Borras el papel entero** (`clearRect(0,0, ancho, alto)`).
2. Calculas dónde tiene que estar el coche ahora (ej: `x = 10`).
3. Dibujas el coche de nuevo.
4. Pausas unos milisegundos (`requestAnimationFrame`).
5. Vuelves al paso 1 (pero ahora la `x` vale 12).
Si te olvidas del paso 1 (borrar), el coche irá dejando una estela infinita pintada por toda la pantalla.

El "pincel" que mancha el lienzo se llama **Contexto**, y se pide haciendo `.getContext("2d")`.

---

## CAPÍTULO 6: SVG (La magia de las matemáticas)

A diferencia del Canvas (que son píxeles brutos), el SVG es pura matemática. En vez de manchar píxeles, el código SVG dice: *"Calcula un círculo perfecto en la coordenada 50,50 con radio 20"*. Como es matemática, puedes hacer zoom infinito en una imagen SVG y nunca jamás verás un píxel borroso.

El elemento rey del SVG es el `<path>` (Camino). Es como el juego de unir los puntos numerados:
- `d="M 10 10 ..."`: El comando `M` significa "Mover el bolígrafo sin pintar hasta la coordenada 10,10".
- `L 50 10`: El comando `L` significa "Dibuja una línea recta desde donde estoy hasta 50,10".
- `Q`: Es para hacer curvas de Bézier (curvas tensas con un punto invisible que estira la línea).
- `Z`: Cierra la figura dibujando una línea recta hasta el punto original donde empezaste.

**Animación SMIL:** El SVG tiene su propio motor de animaciones sin usar Javascript ni CSS. Puedes meter la etiqueta `<animateMotion>` y la figura se moverá sola siguiendo el camino del `<path>` que le digas.

---

## CAPÍTULO 7: FETCH API y AJAX (El mensajero ninja)

Hace muchos años, si querías ver si tenías mensajes nuevos en Tuenti/Facebook, tenías que darle a F5 y recargar toda la página. Una locura.
Luego inventaron AJAX y posteriormente **Fetch**: es un "mensajero ninja" de Javascript.

Tú le dices a Fetch: *"Ve a este enlace silenciosamente por detrás, recoge los datos que haya, y tráemelos. Yo no voy a recargar la página"*.
Como el mensajero tarda un tiempo en ir y volver (la conexión de internet puede ser lenta), tú no puedes bloquear toda tu web esperando a que llegue. Fetch funciona con **Promesas** (`.then()`). 
Es como decir: *"Haz la petición, y **LUEGO (.then)** cuando vuelvas, conviertes el paquete en un JSON fácil de leer, y **LUEGO (.then)**, coges mi HTML y creas tarjetas con los datos nuevos"*.

Por eso el código Fetch siempre es una escalera de `fetch().then().then()`.

---

### CONCLUSIÓN ESTRATÉGICA
Si entiendes esto, da igual qué código te pida el profesor. Sabes que si te pide guardar un dato es LocalStorage; si te pide un formulario que falla hay que meter un preventDefault; si te pide animar un muñeco hay que hacer clearRect antes, y si quiere que leas datos externos, necesitas enviar a tu mensajero Fetch.

**¡Léete esto un par de veces, respira hondo y ve a romper ese examen!**
