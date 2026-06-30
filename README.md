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

## Tecnologie
HTML/CSS/JS puro + Canvas. Librerie via CDN: pdf.js, mammoth.js (estrazione testo), lz-string (compressione link).

## Crediti
Asset grafici: **Anokolisa** — https://www.patreon.com/Anokolisa
