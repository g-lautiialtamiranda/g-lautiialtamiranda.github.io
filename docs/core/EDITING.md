# Guía para editar la página

Todo el sitio vive en `index.html` (texto, estilos y el poco JavaScript que hay). Las fotos
están en `assets/img/`. No hay framework ni build. La única dependencia es Lenis (scroll suave
con mouse), que se baja de jsdelivr: si falla, la página scrollea normal. La velocidad se ajusta
en el script, sección 7 (`wheelMultiplier` y `lerp`).

## Verla en tu compu

- **Fácil:** doble clic en `index.html`.
- **Igual a publicada:** en la carpeta del repo, `python -m http.server 8000` y entrá a
  <http://localhost:8000>. Cortalo con `Ctrl+C` cuando termines.

## Editar los textos

`index.html` está dividido en bloques con carteles. Editá **solo el texto entre las
etiquetas**, sin tocar los `<p>`, `<h2>` ni las comillas.

| Cartel en el archivo | Qué controla |
|---|---|
| `BARRA DE ARRIBA` | La barra que aparece al scrollear |
| `1 · HERO` | Nombre, frase grande, retrato y los dos botones |
| `2 · QUIÉN SOY` | Los dos párrafos que "se encienden" y el remate en el bloque amarillo |
| `3 · CUATRO LUGARES` | Las cuatro frases y sus fotos |
| `4 · EN QUÉ ANDO` | Costear, Mareterra y la carrera |
| `5 · CÓMO PIENSO` | Las tres ideas numeradas |
| `6 · CONTACTO` | WhatsApp, correo, Instagram y LinkedIn |

> ⚠️ Si cambiás la frase grande del hero o la descripción, cambiá también el `<title>`, las
> etiquetas `og:` de arriba de todo y **regenerá `og.png`**: la frase está pintada dentro de
> la imagen que se ve al pegar el link en WhatsApp.

### Las cuatro frases de "Cuatro lugares"

Cada frase está **dos veces**: en la lista fija de la izquierda (`lugares__frases`, la que
cambia al scrollear en pantalla grande) y en el `<h3 class="lugar__frase">` de cada lugar
(la que se ve en teléfono y leen los lectores de pantalla). Si cambiás una, cambiá las dos.

### Las tarjetas de proyectos

Cada tarjeta muestra el primer párrafo; el resto va adentro de `<details>` ("Seguir
leyendo"). Las tres miden lo mismo a propósito. Para sumar una cuarta, copiá un
`<article class="tile">` entero.

### El año del pie

Lo escribe el navegador. El `2026` del HTML es solo para quien tiene JavaScript apagado.

## Datos de contacto

Están en cuatro lugares marcados con **`[CONTACTO]`**, más un resumen al principio del archivo.

- **WhatsApp:** `https://wa.me/5493813419869?text=…`. Número con código de país, sin `+`,
  espacios ni guiones. En el mensaje, los espacios van `%20` y las comas `%2C`.
- **Correo:** en el `href="mailto:…"` y partido en `data-mail-user` y `data-mail-domain`
  (arman la dirección visible). Si cambia, cambialo en los tres.
- **LinkedIn e Instagram:** la URL del perfil y el texto chico de la fila.

## Cambiar una foto

Cada foto está dos veces en `assets/img/`: `.webp` (la que usa el navegador) y `.jpg`
(respaldo). Reemplazá **las dos** con el mismo nombre y actualizá el `alt` y el
`<figcaption>`.

| Archivo | Qué es | Dónde | Recorte |
|---|---|---|---|
| `retrato` | Vos en el stand de Costear | Hero | 2:3 (308×462) |
| `parroquia` | El grupo de la parroquia | Parroquia | 3:4 |
| `iglesia` | El altar, sin gente | Parroquia | 3:4 (720×960) |
| `oficina-alan` | Con Alan, trabajando en Costear | Oficina | 3:4 (720×960) |
| `mareterra-playa` | Con la remera de la agencia | Oficina | 3:4 |
| `facultad-clase` | Una clase en la UNT | Facultad | 3:4 (720×960) |
| `emprende-u-unt` | El equipo en Emprende U | Facultad | 3:4 (720×960) |
| `familia` | La familia en la mesa | En casa | 4:3 (1200×900) |
| `costear-equipo` | Vos con dos socios | Tarjeta de Costear | 3:4 |
| `emprende-u` | Presentando Costear | Costear › El recorrido | 3:4 |
| `expocon` | El stand, con tus viejos | Costear › El recorrido | 3:4 |
| `costear-gaceta` | El recorte del diario | Costear › Seguir leyendo | 880×239 |
| `mareterra-atardecer` | Filmando el atardecer | Tarjeta de Mareterra | 3:4 |
- **El `alt`** dice qué pasa en la foto. **El `<figcaption>`** va en tu voz y dice algo, en
  una línea.
- **Antes de subir una foto:** recortala al aspecto de la tabla, bajala a ~720 px de ancho
  (menos de ~120 KB) y **sacale los metadatos**. Las fotos del teléfono guardan las
  coordenadas GPS. Las `.heic` hay que pasarlas a JPG.
- **Quién más sale:** la parroquia, los socios, tus viejos, tu familia (con menores) y los
  compañeros de clase. Ninguno eligió estar en el link de tu bio. Si alguien pide salir, son
  dos archivos y dos líneas.

## Publicar

Está en GitHub Pages: cada push a `main` actualiza <https://g-lautiialtamiranda.github.io/>
en un par de minutos. Si algún día pasa a un dominio propio, cambiá la dirección en
`canonical`, `og:url`, `og:image` y `twitter:image`. Para ver cómo sale el link:
<https://www.opengraph.xyz/>.

## Lo que la página no hace, a propósito

- **Sin analytics, cookies ni píxeles**, así que tampoco hace falta el cartel de consentimiento.
- **Sin formulario:** los cuatro canales son links directos.
- **Solo modo claro.** La página es luminosa siempre y no sigue el modo oscuro del sistema.
- **El número de WhatsApp queda público.** Conviene usar WhatsApp Business (respuestas
  rápidas, horario, mensaje de ausencia).
