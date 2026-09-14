# Lessons

Mistakes already made. One line each: the rule, then why. Read before starting; add when something breaks.

## CSS
- `ch` resolves against the element's own font-size — a container measured in `ch` with big children came out too narrow.
- `<img>` inside `<picture>` ignores `height:100%` crops unless `picture` is `display:block;height:100%`.
- Don't hide whole sections for scroll reveals — fast scrolling lands on blank screens. Reveal small pieces.
- Don't cap a display headline with `max-width` in `ch` — it forced four lines; break lines explicitly.
- `nth-child` counts among the element's own siblings — an only-child `figure` is always "odd".

## Color
- Compute contrast, never eyeball it — `#C2410C` on white looked AA and measured 4.35.
- Following `prefers-color-scheme` means half the visitors see a design nobody reviewed. Choose one, or test both.

## Testing
- Chrome extension window resize doesn't change the viewport — test phones with a 390px iframe.
- Iframes only repaint after a real scroll event — programmatic scroll gave blank screenshots.
- Don't leave dev servers running in the background — one was killed on low memory mid-review. Stop after verifying.
- When screenshots time out (low memory), stop retrying — verify layout with JS measurements (sizes, overflow, broken images).
- Re-read long generated JS before running it — an observer block came out garbled.

## Assets
- Apply EXIF rotation, then strip metadata (GPS) before publishing phone photos. HEIC needs conversion first.
- Check crops by eye — one "no people" photo had a stranger in the corner; one blurred crop was just an arm.
- Open Graph image and URL must be absolute — WhatsApp shows no preview otherwise.

## Copy
- Write from enthusiasm and choice, never sacrifice or complaint.
- AI is a tool in the background, not the headline.
- No concrete numbers (sales, clients, team size).
