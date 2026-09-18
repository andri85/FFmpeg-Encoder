# 🎬 Naplex Prime — FFmpeg GUI Ultimate

**Versione:** v1.2 AI Auto-Fix
**Data:** 15/09/2026

GUI avanzata in **Python + Tkinter** per gestire FFmpeg con funzioni di analisi, encoding, splitting, verifica automatica, gestione code, organizzazione dei file multimediali e recupero dagli errori.

L'obiettivo è offrire un frontend completo per FFmpeg, automatizzando il flusso:

**Analisi → Configurazione → Encoding / Split → Verifica → Retry / Recovery → Organizzazione → Logging**

---

## ✨ Funzionalità principali

### ✂️ Split intelligente

Supporta diversi metodi di suddivisione:

* Split per dimensione
* Split per durata
* Split in N parti uguali
* Split tramite capitoli
* Nessuno split

### 📦 Target automatici

Preset per dimensioni comuni:

* Telegram Standard — 1.95 GiB
* Telegram Premium — 3.95 GiB
* FAT32 — 3.95 GiB
* DVD5 — 4.36 GiB
* DVD9 — 7.95 GiB
* Blu-ray — 24 GiB
* Google Drive — 4.9 GiB
* Target personalizzato

Sono inoltre disponibili target manuali da **2000 MB a 4000 MB**.

---

## 🎞️ Encoding video

Supporto ai principali encoder FFmpeg:

* `Copy` — nessun re-encode
* H.264 — `libx264`
* H.265 — `libx265`
* H.264 — NVIDIA NVENC
* H.265 — NVIDIA NVENC
* H.264 — Intel QSV
* H.265 — Intel QSV
* H.264 — AMD AMF
* H.265 — AMD AMF

### 🔄 GPU Fallback

Se un encoder hardware non è disponibile, il programma può effettuare automaticamente il fallback verso l'encoding CPU:

```text
NVENC / QSV / AMF
        ↓
   CPU fallback
        ↓
libx264 / libx265
```

---

## 🎵 Audio

Possibilità di:

* Copiare l'audio originale
* Rimuovere l'audio
* AAC
* AC3
* E-AC3
* MP3
* Opus
* FLAC Lossless

---

## 🖥️ Risoluzione e FPS

### Risoluzioni

* Originale
* 2160p
* 1440p
* 1080p
* 720p
* 480p
* 360p

### Frame rate

* Originale
* 60 FPS
* 50 FPS
* 30 FPS
* 25 FPS
* 24 FPS
* 23.976 FPS

---

## 💬 Sottotitoli

Gestione dei sottotitoli con diverse modalità:

* Copy
* Nessun sottotitolo
* Solo forced
* Escludi forced
* Burn-in

Il programma analizza automaticamente gli stream tramite `ffprobe` e può rilevare i sottotitoli forced.

---

## 📺 Organizzazione automatica

Supporto per la gestione automatica della struttura delle librerie multimediali:

* Plex
* Jellyfin
* Kodi
* Film
* Serie TV

Esempio:

```text
Show (Year)/
└── Season 01/
    ├── Show - S01E01.mkv
    ├── Show - S01E02.mkv
    └── Show - S01E03.mkv
```

Sono disponibili strutture:

* Flat
* Plex
* Jellyfin
* Kodi
* Movie

---

## 🏷️ Rinomina automatica

Template disponibili:

```text
.part001
Part 01 of 05
Show - S01E01 - Part 1
001
Custom Template
```

Il parser riconosce diversi formati di naming delle serie, tra cui:

```text
Show S01E01
Show 1x01
Show (2024) S01E01
```

e i film con formato:

```text
Movie (2024)
```

---

## 🧠 Smart Encode

Profili automatici disponibili:

### Smart

Selezione conservativa del codec e della modalità in base al file sorgente.

### Archivio

* H.265 CPU
* Alta qualità
* Audio originale
* Verifica del risultato

### Velocità

Profilo ottimizzato per ridurre i tempi di elaborazione.

### TV

* H.264
* 1080p
* `yuv420p`
* AAC

### Compressione

H.265 con impostazioni orientate alla riduzione delle dimensioni.

---

## 🤖 AI Auto-Fix

Sistema automatico di analisi e recupero dagli errori FFmpeg.

Può utilizzare:

* Analisi degli errori
* Retry automatico
* Configurazione automatica
* Safe Mode
* Storico degli errori
* Backup del sorgente
* Conteggio dei fix

Il sistema include diagnostica per errori come:

* Encoder non disponibile
* Decoder non disponibile
* NVENC non disponibile
* Memoria GPU esaurita
* File inesistente
* Permessi negati
* Disco pieno
* File corrotto/incompleto
* Errori di scrittura
* Incompatibilità codec/muxer
* Parametri non validi
* Errori relativi a filtri e sottotitoli
* Problemi di timestamp
* Pixel format non supportato

---

## 📋 Coda di elaborazione

Gestione avanzata dei job:

* Coda persistente
* Riordinamento dei job
* Salvataggio/caricamento JSON
* Resume
* Recovery queue
* Retry automatico
* Pausa tra le parti
* Avvio automatico della coda
* Skip dei file già completati

La coda viene salvata in:

```text
~/.ffmpeg_split_gui_queue.json
```

---

## ✅ Verifica automatica

Al termine dell'elaborazione il programma può verificare automaticamente l'output tramite `ffprobe`.

Sono disponibili:

* Verifica del file prodotto
* Verifica durata
* Verifica stream
* Verifica metadata
* SHA-256 opzionale
* Protezione del file sorgente
* Recovery in caso di errore

Il file originale viene elaborato solo dopo aver completato i controlli previsti.

---

## 📊 Monitoraggio in tempo reale

Durante l'elaborazione vengono mostrati:

* Percentuale
* Tempo di output
* ETA
* FPS
* Speed
* File corrente
* CPU
* GPU
* RAM
* Progress bar

Il progresso viene ottenuto tramite:

```text
-progress pipe:1
```

---

## 💾 Gestione spazio disco

Prima dell'elaborazione può essere effettuato un controllo dello spazio disponibile per evitare errori dovuti a disco pieno.

---

## 🗑️ Protezione e cestino

La cancellazione dei file può utilizzare il cestino di sistema tramite `send2trash`.

Quando non disponibile viene utilizzata una directory:

```text
_TRASH
```

con gestione automatica dei conflitti di nome.

---

## ⚙️ Gestione FFmpeg

Il programma include un **FFmpeg Manager** con:

* Ricerca automatica di FFmpeg
* Ricerca di FFprobe
* Supporto al `PATH`
* Percorsi statici Windows
* Percorso FFmpeg personalizzato
* Supporto a cartelle portable
* Diagnostica del percorso
* Download tramite sito ufficiale FFmpeg
* Console CMD nascosta durante l'esecuzione su Windows

FFmpeg deve essere disponibile nel `PATH` oppure configurato manualmente.

---

## 🔧 Preset Encoder

### x264 / x265

Supporto ai preset:

```text
ultrafast
superfast
veryfast
faster
fast
medium
slow
slower
veryslow
```

### NVENC

Preset:

```text
p1 → p7
```

### Tune

Supporto a:

```text
film
animation
grain
stillimage
fastdecode
zerolatency
```

---

## 🧵 Gestione risorse

Configurazione dei thread:

```text
Auto
1
2
4
6
8
12
16
24
32
```

Priorità processo:

```text
Normal
Below Normal
Low
Idle
```

Il programma può inoltre utilizzare `psutil` per monitorare e gestire le risorse del sistema.

---

## 📝 Logging

Generazione di log delle operazioni in formato:

* CSV
* JSON

Il log può contenere informazioni come:

```text
timestamp
input
output
part number
duration
size
codec
resolution
fps
split mode
status
verified
sha256
elapsed
speed
error
```

---

## 📤 Export comandi FFmpeg

È possibile esportare i comandi generati nei formati:

```text
.sh
.bat
```

utile per eseguire successivamente le operazioni anche senza la GUI.

---

## 🧰 Utility

Il progetto include strumenti per:

* Quick Media Info
* Analisi tramite ffprobe
* Pulizia file temporanei
* Diagnostica
* Copia diagnostica
* Analisi encoder disponibili
* Analisi filtri disponibili

---

## 💾 Preset e configurazione

Sono supportati fino a **5 preset nominati**.

Le impostazioni vengono salvate in:

```text
~/.ffmpeg_split_gui.json
```

Sono inoltre previste funzioni di:

* Auto-save
* Auto-load
* Backup delle impostazioni
* Validazione della configurazione
* Compatibilità con impostazioni precedenti

---

## 🎨 Interfaccia

L'interfaccia è organizzata in più sezioni:

* **Principale**
* **File & Output**
* **Video & Audio**
* **Split**
* **Utility**
* **AI Auto-Fix**
* **Coda e Log**

La barra inferiore mostra:

```text
File corrente
Speed
ETA
CPU
GPU
RAM
Progress
```

Sono inoltre disponibili i comandi principali:

```text
Scan
Start Encoding
Cancel
Pause
Open Output
Clear Log
```

---

## 📁 Formati video supportati

### Input

```text
.mkv
.mp4
.m4v
.mov
.avi
.ts
.m2ts
.mts
.webm
.flv
.wmv
.mpg
.mpeg
.vob
```

### Output

```text
.mkv
.mp4
.m4v
.ts
.mov
.avi
.webm
```

---

## 📦 Dipendenze

Il programma utilizza:

* Python 3
* FFmpeg
* FFprobe

Dipendenze Python opzionali:

```text
send2trash
plyer
psutil
```

Installazione:

```bash
pip install send2trash plyer psutil
```

---

## 🚀 Avvio

Assicurarsi che `ffmpeg` e `ffprobe` siano disponibili nel `PATH`.

Esempio:

```bash
python ffmpeg_split_gui.py
```

Su Windows è possibile configurare manualmente il percorso di FFmpeg tramite **FFmpeg Manager**.

---

## 🖥️ Piattaforme

Il progetto è pensato per funzionare con FFmpeg su sistemi desktop, con gestione specifica anche per Windows, inclusi:

* Ricerca automatica di FFmpeg
* Percorsi statici
* FFmpeg portable
* Console nascosta
* Export `.bat`

---

## 🔐 Affidabilità

Il progetto integra diversi meccanismi per ridurre il rischio di perdita o produzione di file incompleti:

* Verifica post-elaborazione
* SHA-256 opzionale
* Backup sorgente
* Recovery queue
* Retry automatico
* Disk-space check
* Protezione input
* Gestione del cestino
* Diagnostica FFmpeg
* Fallback encoder
* Resume dei job completati

---

## 📌 Stato del progetto

**Naplex Prime — FFmpeg GUI Ultimate v1.2 AI Auto-Fix**

Frontend completo per FFmpeg orientato a:

> **Splitting · Encoding · Conversion · Verification · Recovery · Automation · Media Organization**

---

## ⚠️ Requisiti

Prima dell'utilizzo verificare:

1. Python 3 installato
2. FFmpeg installato
3. FFprobe disponibile
4. Spazio disco sufficiente per gli output
5. Driver GPU corretti se si utilizzano encoder hardware

---



oppure specificare la licenza effettivamente utilizzata dal repository.
