# Naplex Prime — Report aggiornato delle funzionalità

**Data:** 28 settembre 2026  
**Creatore indicato nel sorgente:** naplex19 / naplex 19  
**Versione applicativa:** 1.6 AI Error Center – Clean UI, con aggiornamenti recenti.

## 1. Novità aggiunte

### Scheda “Guida e Creatore”
Nuova scheda dedicata alla documentazione del programma, con:

- Istruzioni per iniziare a elaborare un video.
- Descrizione delle sezioni e delle funzioni disponibili.
- Ricerca per parola chiave nella guida.
- Pulsante “Mostra tutto” per ripristinare il contenuto completo.
- Pulsante per copiare tutta la guida negli appunti.
- Elenco delle scorciatoie da tastiera.
- Crediti del creatore **naplex19**.
- Riconoscimenti a Python, Tkinter, FFmpeg e VLC.
- Accesso anche dal menu **Aiuto → Guida e Creatore**.

Non sono stati inventati biografia, contatti o informazioni personali del creatore.

## 2. Correzioni recenti

| Problema individuato | Modifica apportata |
|---|---|
| Possibili collisioni dei file temporanei tra elaborazioni parallele | Ogni temporaneo riceve un identificatore univoco. |
| Retry audio AAC senza un secondo tentativo nelle modalità diverse dallo split per dimensione | Aumentati i tentativi disponibili per consentire il fallback. |
| Riferimenti a temporanei già eliminati quando il limite di dimensione non viene raggiunto | Azzerati i riferimenti e aggiunto un messaggio di errore specifico. |
| Timecode numerici come `nan` e `inf` accettati dal parser | Rifiutati i valori non finiti. |
| Caricamento manuale di una coda durante l’elaborazione | Bloccata la sostituzione della coda mentre l’encoding è attivo. |

## 3. Funzioni precedenti mantenute

### Dashboard e gestione dei file
- Dashboard principale con riepilogo e comandi di elaborazione.
- Inserimento di un file singolo o di più file.
- Scansione di cartelle, anche ricorsiva.
- Filtro dei file superiori a 4 GiB.
- Drag & drop tramite la dipendenza opzionale `tkinterdnd2`.
- Inventario delle tracce video, audio e sottotitoli.
- Visualizzazione delle informazioni tecniche del file selezionato.
- Apertura delle cartelle sorgente, output e log.

### Output e organizzazione
- Selezione di una o più cartelle di destinazione.
- Scelta del contenitore di output o mantenimento dell’estensione sorgente.
- Rinomina delle parti con schemi predefiniti o personalizzati.
- Riconoscimento di nomi di film e serie TV.
- Organizzazione delle cartelle per Plex, Jellyfin e Kodi.
- Opzioni di sovrascrittura.
- Gestione del sorgente dopo l’elaborazione secondo le impostazioni.
- Supporto al cestino di sistema o a una cartella di raccolta.

### Elaborazione video
- Copia del video senza ricodifica.
- Codifica CPU H.264 e H.265.
- Opzioni di codifica hardware NVIDIA, Intel e AMD.
- Impostazione del bitrate video.
- Modifica di risoluzione e frame rate.
- Sovrimpressione di un logo.
- Argomenti FFmpeg personalizzati.
- Fallback da encoder hardware a CPU.
- Controllo degli encoder disponibili.

La disponibilità della codifica hardware dipende da GPU, driver e versione di FFmpeg.

### Audio, sottotitoli e tracce
- Copia o conversione dell’audio.
- Impostazione del bitrate audio.
- Gestione dei sottotitoli secondo le opzioni disponibili.
- Rilevamento delle tracce sottotitoli e dei sottotitoli forzati.
- Manager MAP per scegliere le tracce da includere.
- Selezione di tutte le tracce, per tipo, oppure azzeramento della selezione.
- Tentativo di conversione audio in AAC in alcuni casi di incompatibilità con il contenitore.

### Split e timeline
- Elaborazione del file intero.
- Divisione per dimensione.
- Divisione per durata fissa.
- Divisione in un numero prestabilito di parti.
- Divisione per capitoli.
- Estrazione di un singolo intervallo.
- Impostazione del punto iniziale e della durata da elaborare.
- Estensione dell’intervallo fino alla fine del video.
- Lettura della durata del sorgente.
- Riepilogo dell’intervallo e anteprima del piano di divisione.
- Timecode in secondi, `MM:SS` e `HH:MM:SS.mmm`.
- Target preimpostati per Telegram, FAT32, DVD, Blu-ray e altri limiti di dimensione.

In modalità copia, la precisione dei tagli può dipendere dai fotogrammi chiave.

### Coda di elaborazione
- Coda persistente con salvataggio e caricamento JSON.
- Aggiunta, rimozione e riordino dei job.
- Svuotamento della coda e rimozione dei completati.
- Ricoda dei job selezionati.
- Retry dei job falliti.
- Ripresa delle parti registrate come completate.
- Pausa e ripresa tra le parti.
- Annullamento dell’elaborazione.
- Copia del percorso o dell’errore del job.
- Apertura della posizione del file selezionato.

### Avanzamento e risorse
- Percentuale di avanzamento per job e per parte.
- Riepilogo dell’avanzamento globale.
- Velocità, FPS, tempo trascorso e tempo residuo stimato.
- Numero di worker automatico o configurabile.
- Limite dei thread FFmpeg.
- Priorità del processo.
- Monitor CPU, RAM e GPU quando disponibili.

### Verifiche e integrità
- Controllo dello spazio disponibile.
- Pre-flight check della configurazione.
- Dry-run per esaminare l’elaborazione prevista.
- Verifica degli output con ffprobe, se abilitata.
- Controllo della durata con tolleranza configurabile.
- Generazione opzionale di hash SHA-256.
- Controllo di integrità mediante decodifica audio/video.
- Protezioni sulla gestione finale del sorgente legate all’esito dell’elaborazione e alle opzioni attivate.

### Lettore VLC
- Lettore video incorporato nell’interfaccia.
- Apertura di un file o caricamento della selezione.
- Play, pausa e stop.
- Salti avanti e indietro di 10 secondi.
- Spostamento nella timeline.
- Volume e mute.
- Velocità di riproduzione.
- Snapshot.
- Schermo intero.

Richiede VLC e il collegamento Python appropriato.

### Utility multimediali
- Informazioni tecniche rapide sui media.
- Esportazione dell’inventario in CSV o JSON.
- Estrazione di un’anteprima JPG al timecode impostato.
- Analisi del file selezionato.
- Statistiche della sessione.
- Pulizia dei temporanei.
- Salvataggio del report di sessione.

### FFmpeg Manager
- Rilevamento di FFmpeg e ffprobe.
- Ricerca nel PATH e nei percorsi Windows previsti.
- Configurazione di un percorso personalizzato.
- Test dell’installazione.
- Diagnostica di encoder e filtri.
- Benchmark del codec selezionato.
- Copia ed esportazione della diagnostica.
- Accesso alla pagina ufficiale per il download.
- Esecuzione senza finestre console FFmpeg su Windows.

### Preset, impostazioni e interfaccia
- Preset nominati, fino al limite previsto di cinque.
- Salvataggio, caricamento ed eliminazione dei preset.
- Salvataggio e caricamento delle impostazioni.
- Validazione, riepilogo e ripristino dei valori predefiniti.
- Backup delle impostazioni.
- Temi grafici selezionabili.
- Schede con contenuti scorrevoli.
- Menu File, Elaborazione, Lettore, Strumenti, AI e Aiuto.
- Interfaccia Clean UI con etichette prevalentemente testuali.
- Notifiche desktop opzionali.

### AI Error Center
- Raccolta centralizzata degli errori Python, Tkinter, thread, FFmpeg e delle integrazioni gestite.
- Storico e contatore degli errori.
- Indicazione di origine, categoria, causa probabile e suggerimenti.
- Analisi dell’ultimo errore.
- Applicazione delle correzioni previste dalle regole interne.
- Opzioni di retry e riparazione della configurazione.
- Test dell’ambiente.
- Backup del sorgente previsto dalla modalità sicura.

**Il centro utilizza regole locali di diagnosi: non è una chat collegata a un modello AI remoto.**

### Log ed esportazione comandi
- Log delle operazioni.
- Esportazione CSV e JSON.
- Report diagnostici e di sessione.
- Esportazione dei comandi come script Windows `.bat` e Unix `.sh`.
- Copia dei comandi negli appunti.
- Generazione dei comandi coerente con il piano di split.

## 4. Scorciatoie principali

| Scorciatoia | Azione |
|---|---|
| Ctrl+O | Apri un file nel lettore |
| Ctrl+Shift+O | Seleziona la cartella sorgente |
| Ctrl+I | Inserisci un file singolo |
| Ctrl+S | Salva le impostazioni |
| F5 | Scansiona |
| F9 | Avvia encoding |
| Ctrl+Q | Esci |

## 5. Pacchetti aggiornati

| Pacchetto | Contenuto e requisiti |
|---|---|
| **Windows — Naplex Prime 1.6.1.exe** | Sorgente aggiornato confezionato con Python e Tkinter. FFmpeg/ffprobe restano da installare o configurare. Le integrazioni opzionali non sono incluse in questa compilazione. |
| **Debian/Ubuntu — naplex-prime_7.0+guide1_all.deb** | Sorgente aggiornato, lanciatore e voce nel menu applicazioni. Dichiara Python, Tkinter e FFmpeg come dipendenze. |

La numerazione Debian `7.0+guide1` serve a consentire l’aggiornamento del precedente pacchetto `7.0`. Il sorgente continua a riportare la versione applicativa **1.6 AI Error Center – Clean UI**.

## 6. Stato delle verifiche

**Controlli completati:**
- Sintassi Python del sorgente.
- Otto casi di validazione dei timecode.
- Costruzione della guida con componenti grafici simulati.
- Compilazione dell’EXE con PyInstaller.
- Struttura del DEB, permessi del lanciatore e corrispondenza del sorgente incluso.
- Generazione dei checksum SHA-256 dei pacchetti.
- Copia di backup prima dell’aggiornamento del sorgente originale.

**Non ancora verificati:**
- Aspetto e interazione della finestra reale dopo l’aggiornamento.
- Installazione e avvio su Debian/Ubuntu.
- Conversioni complete con diversi codec e contenitori.
- Funzionamento dei fallback e delle elaborazioni parallele su file reali.
- Integrazioni opzionali nei diversi ambienti.

Il report descrive le funzionalità presenti nel codice; non equivale a un collaudo completo di ogni funzione.
