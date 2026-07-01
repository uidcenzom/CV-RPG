# Portfolio World

Portfolio World trasforma un curriculum in un **mondo 2D esplorabile** in stile pixel art.
Ogni esperienza del CV — studi, lavoro, progetti — diventa un edificio sulla mappa, in cui si
cammina e si entra per leggerne i dettagli.

È interamente **statico e lato browser**: nessun server, nessun database, nessun login.
Si pubblica gratis (es. su GitHub Pages) e si condivide con un semplice link.

---

## Come funziona (il flusso)

1. **Importa il CV** — nella pagina iniziale carichi un PDF, un DOCX o un file JSON Resume.
   Il testo viene estratto nel browser e i campi vengono pre-compilati; tu controlli e correggi.
2. **Genera il mondo** — dai dati viene creata una mappa esplorabile con un edificio per esperienza.
3. **Condividi** — con un pulsante ottieni un link che contiene tutto il tuo portfolio.
   Chi lo apre esplora il tuo mondo, senza dover installare o registrare nulla.

---

## Funzionalità

### Importazione del curriculum
- Formati supportati: **PDF**, **DOCX** e **JSON Resume** (formato standard).
- Estrazione del testo direttamente nel browser (niente upload a server esterni).
- Riconoscimento automatico delle sezioni (istruzione, esperienza, progetti) e delle date, con
  supporto **multilingua** (italiano, inglese, spagnolo, francese, tedesco).
- Gestione dei **PDF a due colonne**: il testo viene riordinato per colonna, evitando i tipici errori.
- Distinzione automatica tra ente e titolo (es. "Università" contro "Laurea"), anche quando l'ordine
  cambia da un CV all'altro.
- **Correzione manuale**: ogni voce è modificabile in un form (ente, ruolo, tipo, date, descrizione,
  competenze, link). Puoi aggiungere o rimuovere voci a mano.

### Il mondo esplorabile
- Un **edificio per ogni esperienza**, colorato per tipo:
  - blu = studi
  - verde = lavoro
  - viola = progetti
- Ci si muove con tastiera o con un joystick su schermo (mobile) e si **entra negli edifici** per
  vedere le informazioni dell'esperienza (ruolo, periodo, descrizione, competenze, link).
- **Generazione semi-casuale**: il mondo non è sempre uguale. In base a un "seme" ricavato dai tuoi
  dati vengono scelti:
  - il **layout** (a griglia/campus, a quartieri per tipo, oppure a timeline cronologica);
  - il **tema/atmosfera** (prato, bosco, notte, deserto, neve);
  - la **dimensione degli edifici** (più grandi per le esperienze più lunghe) e la texture dei muri.
- La generazione è **deterministica**: lo stesso CV produce sempre lo stesso mondo, quindi il link
  condiviso mostra a tutti la stessa mappa. Il pulsante **Rigenera** permette di provare varianti
  diverse; quella scelta viene salvata nel link.

### Condivisione con un link
- Premendo **Crea link condivisibile** i dati del CV vengono **compressi dentro il link stesso**.
- Chi apre il link vede il tuo portfolio: **niente viene salvato su un server**, non serve alcun
  database e creare tanti portfolio non ha alcun costo.
- La parte dopo `#` nel link non viene inviata a nessun server: resta un dato locale che viaggia
  solo nell'URL.

### Editor della mappa
Per personalizzare la disposizione, dal form iniziale si apre l'**editor**, che carica **la mappa
attuale già generata dal CV** (terreno, strade, edifici, alberi e rocce). Da qui puoi:
- **spostare gli edifici** trascinandoli (strumento *Sposta edif.*);
- **aggiungere o togliere alberi e rocce** (strumenti *Albero* e *Roccia*);
- **dipingere altri tile** scegliendoli dalla palette (erba, acqua, decorazioni, ecc.);
- impostare il **punto di partenza** del giocatore.

Al termine, **Genera link mondo** produce un link alla mappa personalizzata: gli edifici restano
quelli del CV e sono sempre consultabili.

> Per sicurezza, la modifica è possibile **solo dall'editor** (raggiungibile dal form iniziale):
> il visualizzatore è di **sola lettura**, così chi riceve un link non può alterare la mappa.

### Personalizzazione grafica (tileset)
Un tileset è una **cartella con la stessa struttura di `tiles/`** (stesse sottocartelle e nomi file).
Puoi usarne uno tuo, senza database, in tre modi:

1. **Fork e sostituzione dei file** — cloni il repository e rimpiazzi le immagini in `tiles/`
   mantenendo nomi e struttura: tutto il sito userà la tua grafica.
2. **Cartella pacchetto di default** — crei una cartella (es. `packs/city/`) con la stessa struttura
   e la imposti come base aggiungendo, prima dello script principale in `portfolio-map.html`:
   ```html
   <script>window.PW_TILESET = 'packs/city/';</script>
   ```
3. **Tileset via URL** — nel builder, sotto *"Aspetto / Tileset personalizzato"*, incolli l'URL di una
   cartella tileset che ospiti tu (es. `https://tuo-utente.github.io/miei-tiles/`). L'URL (non
   l'immagine) viene incluso nel link condiviso.

> Priorità della base grafica: link condiviso → localStorage → `window.PW_TILESET` → `tiles/` (default).

### Supporto mobile
- Su smartphone e tablet compaiono un **joystick analogico** (per muoversi) e un pulsante **Entra**
  (per aprire i dettagli degli edifici).
- Il canvas si adatta alla larghezza dello schermo; i form sono a colonna singola.

### Privacy
Tutto avviene nel browser dell'utente. I dati del CV restano nel dispositivo o dentro il link
condiviso: **niente viene inviato o salvato su un server**.

---

## Controlli

| Azione | Tastiera | Mobile |
|---|---|---|
| Muoversi | WASD o frecce | joystick |
| Entrare in un edificio | E | pulsante *Entra* |
| Chiudere una scheda | ESC | pulsante *Chiudi* / tocco fuori |

---

## Struttura del progetto

- `index.html` — pagina iniziale.
- `cv-builder.html` — importazione del CV, form di controllo, generazione mondo/link, accesso all'editor.
- `portfolio-map.html` — il mondo esplorabile (visualizzatore, sola lettura).
- `editor.html` — editor della mappa (dipingere tile, spostare edifici, aggiungere alberi/rocce).
- `tiles/` — asset grafici in pixel art.

---

## Pubblicazione (GitHub Pages)

Essendo un sito statico, basta metterne i file online.

1. Crea un repository **pubblico** su GitHub e carica i file del progetto.
2. Vai in **Settings → Pages** e scegli come sorgente il branch `main`, cartella `/ (root)`.
3. Dopo circa un minuto il sito è disponibile all'indirizzo
   `https://<utente>.github.io/<repository>/`.

In alternativa vanno bene altri hosting statici gratuiti (Netlify, Cloudflare Pages, Vercel).

---

## Tecnologie

HTML, CSS e JavaScript puri, con rendering su `<canvas>`. Librerie caricate da CDN:
- **pdf.js** e **mammoth.js** — estrazione del testo da PDF e DOCX;
- **lz-string** — compressione dei dati nel link.

Serve una connessione a internet solo per caricare queste librerie (e, se usato, un tileset via URL).

---

## Crediti

Asset grafici in pixel art di **Anokolisa** — https://www.patreon.com/Anokolisa
