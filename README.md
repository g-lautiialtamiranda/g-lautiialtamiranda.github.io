# Landing page personal — Lautaro Altamiranda Mastri

El link que va en la bio de Instagram. Una sola página, sin framework, sin build, sin
dependencias: **todo el sitio vive en `index.html`** (texto, estilos y el poco JavaScript
que hay), y las fotos en `assets/`.

```
index.html     ← la página entera. Es el único archivo que vas a tocar.
assets/        ← las fotos, ya recortadas y comprimidas para web
og.png         ← la imagen que se ve cuando compartís el link (1200×630)
favicon.svg    ← el iconito de la pestaña
README.md      ← esto
```

---

## Verla en tu compu

**La forma fácil:** doble clic en `index.html`. Se abre en el navegador y funciona todo.

**La forma prolija** (igual a como se va a ver publicada, con la imagen OG resolviéndose bien):
abrí una terminal en esta carpeta y corré una de estas dos líneas, después entrá a
<http://localhost:8000>:

```bash
python -m http.server 8000
```

```bash
npx serve .
```

---

## Editar los textos

Abrí `index.html` con cualquier editor (el Bloc de notas sirve). Está dividido en bloques
con carteles bien visibles; buscá el que quieras cambiar y editá **solo el texto que está
entre las etiquetas**, sin tocar los `<p>`, `<h2>` ni las comillas.

| Buscá este cartel en el archivo | Qué controla |
|---|---|
| `1 · HERO` | Tu nombre, la frase grande, tu retrato y los dos botones |
| `2 · QUIÉN SOY` | Los tres párrafos que cuentan quién sos |
| `3 · TIRA DE FOTOS` | Las seis fotos y sus epígrafes |
| `4 · EN QUÉ ANDO` | Costear, Mareterra y la carrera |
| `5 · CÓMO PIENSO` | Las tres ideas numeradas |
| `6 · CONTACTO` | WhatsApp, correo, Instagram y LinkedIn |

### La lista que se escribe sola

Debajo de la frase grande hay una línea que se escribe letra por letra y va
cambiando: *En la parroquia → En la oficina → En la facultad → En la cancha*.
Son cuatro, los cuatro lugares que promete la bajada de arriba. Las frases **no
están en el HTML**: están al final del archivo, en el script, en una lista que
dice `var FRASES = [`. Editá esa lista y listo. La última frase es la que queda
fija cuando termina la vuelta —hoy, «En la cancha»—.

Si cambiás las frases, cambiá también el párrafo `sr-only` que está justo debajo
del `<p class="typer">` en el HTML: es el que leen los lectores de pantalla y el
que se ve si el visitante tiene JavaScript apagado.

**Ejemplo.** Si querés cambiar la bajada del hero, buscá `class="hero__lead"` y cambiá lo que
está entre `>` y `</p>`:

```html
<p class="hero__lead">Cofundador de Costear, un software de costos con IA para PyMEs. …</p>
                      └──────────────── esto es lo que se edita ────────────────┘
```

> ⚠️ Si cambiás la frase grande del hero o la descripción, acordate de cambiar también el
> `<title>` y las etiquetas `og:` de arriba de todo, que son las que se ven cuando pegás el
> link en WhatsApp.

### Los datos de contacto

Están en cuatro lugares, todos marcados con el comentario **`[CONTACTO]`**. Hay además un
resumen al principio del archivo para que sepas cuáles son sin buscar:

- **WhatsApp** — `https://wa.me/5493813419869?text=…`. El número va con código de país y sin
  `+`, espacios ni guiones. El texto después de `?text=` es el mensaje que le aparece escrito
  a quien te escribe; si lo cambiás, los espacios se escriben `%20` y las comas `%2C`.
- **Correo** — aparece dos veces en el mismo bloque: en el `href="mailto:…"` (el que funciona
  aunque el visitante tenga JavaScript apagado) y partido en dos atributos,
  `data-mail-user` y `data-mail-domain`, que son los que arman la dirección visible en
  pantalla. Si cambiás el correo, cambialo en los tres lugares.
- **LinkedIn** e **Instagram** — la URL completa del perfil.

### Cambiar una foto

Todas las fotos viven en `assets/` y cada una está **dos veces**: un `.webp` (el que
usa el navegador) y un `.jpg` (el respaldo). Para cambiar una, reemplazá **las dos**
manteniendo el nombre:

| Archivo | Qué es | Recorte |
|---|---|---|
| `retrato` | El retrato del hero | Vertical 2:3 (408×612) |
| `parroquia` | El grupo de la parroquia | Vertical 3:4 (440×587) |
| `costear-equipo` | Vos con dos socios de Costear | Vertical 3:4 (440×587) |
| `emprende-u` | Presentando, con el sistema proyectado | Vertical 3:4 (440×587) |
| `expocon` | El stand de EXPOCON, con tus viejos | Vertical 3:4 (440×587) |
| `mareterra-playa` | Con la remera de la agencia, en la playa | Vertical 3:4 (440×587) |
| `mareterra-atardecer` | De espaldas, filmando el atardecer | Vertical 3:4 (440×587) |
| `costear-gaceta` | El recorte del diario, dentro del bloque de Costear | Apaisado (880×239) |

Después, en `index.html`, actualizá el **`alt`** y el **`<figcaption>`** de esa foto para
que digan lo que se ve. El `alt` es lo que lee alguien que no puede ver la imagen: escribí
qué pasa en la foto, no «foto 3».

> **Sacales los metadatos.** Una foto sacada con el teléfono viaja con la fecha, el modelo del
> aparato y, muy seguido, las **coordenadas GPS exactas** de dónde se tomó. Publicada tal cual,
> eso queda a disposición de cualquiera que se baje el archivo. Las que están ahora se subieron
> limpias; si agregás una, limpiala antes (la mayoría de los editores tiene «exportar sin datos
> de ubicación»).

> Las fotos originales del teléfono pesan más de 1 MB y muchas son `.heic`, que el navegador
> no sabe mostrar. Antes de subir una hay que recortarla al aspecto de la tabla y bajarla a
> unos 440 px de ancho. Si no tenés a mano con qué, cualquier editor de fotos sirve; lo
> importante es el aspecto y que el archivo quede por debajo de ~80 KB.

**Cuidado con quién más sale en la foto.** Varias de las que están ahora tienen gente
además de vos: el grupo de la parroquia, los socios de Costear, tus viejos en el stand.
Fue una decisión tomada a propósito, pero conviene tenerla presente — ninguna de esas
personas eligió aparecer en el link de tu bio, y la página la puede abrir cualquiera. Si
alguna te pide salir, es cambiar dos archivos y dos líneas.

---

## Publicarla

### Opción 1 — Netlify Drop (lo más rápido, sin cuenta ni comandos)

1. Entrá a <https://app.netlify.com/drop>.
2. Arrastrá **la carpeta entera** a la ventana.
3. En segundos te da una URL. Creando una cuenta gratis podés renombrarla a algo como
   `lautaro.netlify.app` y conectarle un dominio propio si algún día comprás uno.

Para actualizarla más adelante: volvés a arrastrar la carpeta al mismo sitio.

### Opción 2 — GitHub Pages (si querés que el historial viva en GitHub)

1. Creá un repositorio nuevo en GitHub y subí esta carpeta.
2. En el repo: **Settings → Pages → Build and deployment → Source: Deploy from a branch**,
   rama `main`, carpeta `/ (root)`.
3. En un par de minutos queda en `https://<tu-usuario>.github.io/<repo>/`.

### Después de publicar: arreglar la previsualización del link

Las etiquetas `og:url` y `og:image` están puestas con rutas relativas y en general funcionan,
pero para que WhatsApp y las redes muestren siempre la imagen conviene ponerlas absolutas.
Buscá el bloque `OPEN GRAPH` arriba de todo en `index.html` y cambiá esas dos líneas por tu
dirección real:

```html
<meta property="og:url"   content="https://tudominio.com/">
<meta property="og:image" content="https://tudominio.com/og.png">
```

Podés comprobar cómo se ve pegando el link en <https://www.opengraph.xyz/>.

---

## Cosas que la página no hace, a propósito

- **No tiene analytics, cookies ni píxeles de seguimiento.** Por eso tampoco necesita cartel
  de consentimiento.
- **No tiene formulario de contacto.** Un formulario necesita un servidor o un servicio de
  terceros; acá los tres canales son links directos que no dependen de nadie.
- **No tiene modo claro/oscuro manual.** Sigue la preferencia del sistema del visitante.

## Una advertencia

El número de WhatsApp queda **público**: cualquiera que abra el link de tu bio lo tiene, y los
robots que rastrean páginas también. Si es el mismo número que usás para todo, vale la pena
pasar ese contacto a **WhatsApp Business** antes de difundir el link — te da respuestas
rápidas, horario de atención y mensaje de ausencia, que es justo lo que vas a querer cuando
empiecen a escribirte desconocidos.
