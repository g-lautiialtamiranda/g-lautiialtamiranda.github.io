# Landing page personal — Lautaro Altamiranda Mastri

El link que va en la bio de Instagram. Una sola página, sin framework, sin build, sin
dependencias: **todo vive en `index.html`** (texto, estilos y el poco JavaScript que hay).

```
index.html     ← la página entera. Es el único archivo que vas a tocar.
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
| `1 · HERO` | Tu nombre, la frase grande, la bajada y el botón «Escribime» |
| `2 · SOBRE MÍ` | El párrafo que explica por qué los cuatro temas son uno solo |
| `3 · LOS CUATRO TERRENOS` | Las cuatro tarjetas (negocios, IA, literatura, fe) |
| `4 · PROYECTOS` | CosteAR, la agencia y la carrera |
| `5 · SOBRE QUÉ PUBLICO` | Los tres pilares y el link a Instagram |
| `6 · CONTACTO` | WhatsApp, correo y LinkedIn |

**Ejemplo.** Si querés cambiar la bajada del hero, buscá `class="hero__lead"` y cambiá lo que
está entre `>` y `</p>`:

```html
<p class="hero__lead">Cofundador de CosteAR, un software de costos con IA para PyMEs. …</p>
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

### Poner tu foto

1. Guardá el retrato en esta carpeta con el nombre **`retrato.jpg`** (vertical, tipo 800×1000).
2. En `index.html`, buscá `HUECO PARA LA FOTO` y **borrá las dos líneas de comentario** que
   envuelven el bloque `<figure>`: la que dice `-->` y la que abre con `<!--`.

El diseño se reacomoda solo: en el teléfono la foto va arriba del texto y en pantalla grande
el hero pasa a dos columnas. No hay que tocar nada más.

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
