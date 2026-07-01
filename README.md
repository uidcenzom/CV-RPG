# Portfolio World 🗺️

Trasforma un **curriculum** in un **mondo 2D esplorabile** in stile pixel art.
Ogni esperienza (studi, lavoro, progetti) diventa un edificio sulla mappa.

## Come si usa
1. Apri il sito (`index.html`).
2. **Crea dal tuo CV** → carica un PDF o DOCX, controlla/correggi i campi.
3. Premi **🔗 Crea link condivisibile**: i dati vengono compressi *dentro* il link.
4. Condividi il link: chiunque lo apra esplora il tuo mondo (WASD/frecce per muoversi, **E** per entrare negli edifici).

## Caratteristiche
- 100% statico: nessun server, nessun database, nessun login.
- Privacy: i dati del CV restano nel browser dell'utente (o dentro il link condiviso). Niente viene inviato a un server.
- Colori per tipo: 🔵 Studi · 🟢 Lavoro · 🟣 Progetti.

## File principali
- `index.html` — pagina d'ingresso.
- `cv-builder.html` — caricamento CV, estrazione testo, form, generazione link.
- `portfolio-map.html` — il mondo esplorabile.
- `tiles/` — asset grafici (pixel art di Anokolisa).

## Personalizzare la grafica (tileset)
Un tileset è una **cartella con la stessa struttura di `tiles/`** (stesse sottocartelle e nomi file). Tre modi per usarne uno tuo, senza database:

1. **Fork + sostituzione file** — cloni il repo e rimpiazzi le immagini dentro `tiles/` (mantenendo nomi e layout). Tutto il sito usa la tua grafica.
2. **Cartella pacchetto di default** — crei una cartella (es. `packs/city/`) con la stessa struttura e imposti la base creando un file `config.js` con:
   ```html
   <!-- aggiungi in portfolio-map.html, prima dello script principale -->
   <script>window.PW_TILESET = 'packs/city/';</script>
   ```
3. **Tileset via URL (per singolo utente)** — nel builder, sotto *"🎨 Aspetto / Tileset personalizzato"*, incolli l'URL di una cartella tileset che ospiti tu (es. `https://tuo-utente.github.io/miei-tiles/`). Viene incluso nel **link condiviso** (solo l'URL, non l'immagine), così chi apre il link vede la tua grafica.

> Priorità della base: link condiviso → localStorage → `window.PW_TILESET` → `tiles/` (default).

## Tecnologie
HTML/CSS/JS puro + Canvas. Librerie via CDN: pdf.js, mammoth.js (estrazione testo), lz-string (compressione link).

## Crediti
Asset grafici: **Anokolisa** — https://www.patreon.com/Anokolisa
