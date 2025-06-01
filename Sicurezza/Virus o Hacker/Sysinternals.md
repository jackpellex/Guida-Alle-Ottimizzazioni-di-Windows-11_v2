# Come Trovare, Scovare e Rimuovere Virus con Sysinternals Suite su Windows 11

Questa guida è pensata per utenti non esperti e si basa sul video **“Come scoprire se hai un VIRUS NASCOSTO nel PC (e cosa fare)”** 
del canale YouTube nFire. Verranno spiegati i passaggi per scaricare, installare e utilizzare la Sysinternals Suite 
per individuare e rimuovere eventuali minacce, oltre a mostrare come verificare attività sospette come connessioni esterne e applicazioni sconosciute.

---

## 1. Introduzione

I virus e altri malware possono infettare il computer, rallentarlo e compromettere la sicurezza del sistema. 
Utilizzando strumenti avanzati come quelli presenti nella Sysinternals Suite, è possibile:
- **Individuare** processi sospetti e voci di avvio indesiderate.
- **Scoprire** connessioni di rete insolite.
- **Rimuovere** manualmente o bloccare componenti dannosi.

---

## 2. Scaricare e Installare la Sysinternals Suite

1. **Scarica la Suite:**
   - Visita il sito ufficiale di Microsoft Sysinternals:  
     [https://learn.microsoft.com/en-us/sysinternals/downloads/sysinternals-suite](https://learn.microsoft.com/en-us/sysinternals/downloads/sysinternals-suite)
   - Scarica il file ZIP contenente tutti gli strumenti.

2. **Estrai il Contenuto:**
   - Estrai il file ZIP in una cartella a tua scelta (ad esempio, `C:\Sysinternals`).

3. **Apri un Prompt dei Comandi (Admin):**
   - Premi `Win + X` e seleziona **Windows Terminal (Admin)** o **Prompt dei comandi (Admin)**.
   - Naviga alla cartella estratta:
     ```sh
     cd C:\Sysinternals
     ```

---

## 3. Utilizzare gli Strumenti della Sysinternals Suite per Scovare e Rimuovere Virus

### 3.1 Process Explorer 

Process Explorer è uno strumento avanzato che fornisce informazioni dettagliate su tutti i processi attivi nel sistema. Permette di individuare eventuali processi sospetti e di analizzarli nel dettaglio.

#### 1. Avvio di Process Explorer

- Apri la cartella Sysinternals e avvia il file `procexp64.exe` (per sistemi a 64-bit) o `procexp.exe` (per sistemi a 32-bit).
- Concedi i permessi di amministratore, se richiesto.
- Una volta aperto, vedrai una lista di tutti i processi attivi, organizzati in una struttura ad albero che mostra quali processi dipendono da altri.

#### 2. Identificare Processi Sospetti

**Colori e Significato:**

- **Viola:** Processi contenenti DLL .NET.
- **Verde:** Nuovi processi appena avviati.
- **Rosa:** Processi in modalità sospesa.
- **Rosso:** Processi terminati di recente.

**Analizza i nomi dei processi:**

- I nomi devono essere familiari (es. `explorer.exe`, `svchost.exe`).
- Processi con nomi casuali o simili a quelli di sistema ma con errori di battitura possono essere malware (es. `svhost.exe` invece di `svchost.exe`).

#### 3. Uso della Scheda Properties

- Clicca con il tasto destro su un processo sospetto e seleziona **Properties**.
- Controlla:
  - **Command Line:** Mostra il percorso esatto di esecuzione del file.
  - **Parent Process:** Indica quale processo ha avviato quello selezionato.
  - **Threads e Handles:** Alcuni malware aprono molti thread per evitare la chiusura.
  - **Scheda Strings:** Può rivelare stringhe di codice sospette contenute nel processo.

#### 4. Verifica con VirusTotal

Process Explorer ha un'integrazione con **VirusTotal**, un database online che analizza file sospetti con molteplici motori antivirus.

- Abilita VirusTotal andando su **Options → VirusTotal.com → Check VirusTotal.com**.
- Dopo pochi secondi, accanto ai processi appariranno punteggi come `0/70` (pulito) o `5/70` (sospetto).
- Se il numero di segnalazioni è elevato, il processo è probabilmente dannoso.

#### 5. Terminare Processi Pericolosi

Se un processo risulta dannoso:

- **Clic destro → Kill Process** per chiuderlo immediatamente.
- Se si riavvia da solo, significa che è gestito da un altro processo (**vedere Parent Process**).
- Rimuovere il file sorgente manualmente o con **Autoruns**.

#### 6. Diagnostica Avanzata e Confronto con altri Strumenti

| Funzionalità | Task Manager | Process Explorer | Process Hacker |
|-------------|-------------|-----------------|---------------|
| Visualizzazione Processi | ✔️ | ✔️ (con dettagli avanzati) | ✔️ (simile a Process Explorer) |
| Verifica VirusTotal | ❌ | ✔️ | ❌ |
| Modifica Permessi Processi | ❌ | ❌ | ✔️ |
| Analisi dei Thread | ❌ | ✔️ | ✔️ |
| Individuazione DLL | ❌ | ✔️ | ✔️ |

Process Explorer è lo strumento più potente per l'analisi dei processi, ma in alcuni casi **Process Hacker** offre più opzioni per la rimozione forzata.

3. Utilizzare gli Strumenti della Sysinternals Suite per Scovare e Rimuovere Virus

### 3.2 Autoruns (Gestione dell'Avvio e Rimozione Persistente)

Autoruns è un potente strumento che permette di gestire le applicazioni e i servizi che si avviano automaticamente con Windows. È utile per rimuovere malware persistenti che si riattivano dopo ogni riavvio.

1. Avvio di Autoruns

Apri la cartella Sysinternals e avvia il file Autoruns64.exe (per sistemi a 64-bit) o Autoruns.exe (per sistemi a 32-bit).

Concedi i permessi di amministratore, se richiesto.

Attendi il caricamento della lista, che mostrerà tutte le applicazioni, driver, servizi e task pianificati che si avviano con il sistema operativo.

2. Identificare e Disabilitare Elementi Sospetti

- Scorri le schede per individuare voci sospette:
  - "Logon": Mostra i programmi che si avviano con il login dell'utente.
  - "Scheduled Tasks": Contiene attività pianificate, a volte usate dai malware per autorigenerarsi.
  - "Services": Elenca i servizi attivi, tra cui quelli di Windows e di terze parti.
  - "Drivers": Mostra i driver caricati all'avvio.
  - "AppInit": Elenca le librerie caricate da ogni processo.

- Analizza i percorsi e i nomi:
  - I percorsi dovrebbero puntare a directory ufficiali (es. C:\Program Files, C:\Windows\System32).
  - Programmi sconosciuti con percorsi in "Temp" o "AppData" potrebbero essere dannosi.
  
3. Uso della Verifica VirusTotal

- Abilita VirusTotal dal menu Options → Scan Options → Check VirusTotal.com.
- Controlla il punteggio: se un processo ha molte segnalazioni, è probabile che sia dannoso.

4. Disabilitazione e Rimozione

- Per disabilitare un elemento, deseleziona la casella accanto al nome.
- Per eliminare definitivamente un elemento sospetto:
  - Clic destro → Delete.
  - Se il file è bloccato, potrebbe essere necessario eliminarlo manualmente in modalità provvisoria.

5. Diagnostica Avanzata e Confronto con altri Strumenti

| Funzionalità | Task Manager | Autoruns | MSConfig |
|-------------|--------------|----------|----------|
| Visualizzazione Avvio | ✔️ | ✔️ (dettagli avanzati) | ✔️ (limitato) |
| Verifica VirusTotal | ❌ | ✔️ | ❌ |
| Rimozione Diretta | ❌ | ✔️ | ❌ |
| Controllo Servizi | ❌ | ✔️ | ✔️ |

Autoruns è lo strumento più avanzato per la gestione dell'avvio, consentendo di individuare e rimuovere elementi pericolosi in modo efficace.


### 3.3 TCPView
3.3 TCPView (Monitoraggio delle Connessioni di Rete)

TCPView è uno strumento avanzato della Sysinternals Suite che consente di monitorare in tempo reale tutte le connessioni di rete attive sul sistema. È utile per individuare attività sospette, come connessioni non autorizzate o processi che comunicano con server sconosciuti.

### 1. Avvio di TCPView

- Apri la cartella Sysinternals e avvia il file `Tcpview.exe`.
- Concedi i permessi di amministratore, se richiesto.
- Una volta avviato, apparirà una lista di tutti i processi che stabiliscono connessioni di rete, mostrando indirizzi IP locali e remoti, porte e stato della connessione.

### 2. Interpretazione della Lista di Connessioni

**Colonne principali:**
- **Process**: Nome del processo che sta utilizzando la connessione.
- **PID**: ID del processo, utile per identificare il programma in esecuzione.
- **Local Address**: Indirizzo IP e porta utilizzati in locale.
- **Remote Address**: Indirizzo IP e porta del server remoto con cui è stabilita la connessione.
- **State**:
  - **ESTABLISHED**: Connessione attiva e in uso.
  - **LISTENING**: Il processo sta aspettando connessioni in entrata.
  - **CLOSE_WAIT/TIME_WAIT**: La connessione è stata chiusa di recente.
  - **SYN_SENT**: Il processo sta tentando di stabilire una connessione.

### 3. Identificare Connessioni Sospette

- Se un processo sconosciuto stabilisce connessioni con IP remoti insoliti, potrebbe trattarsi di malware o spyware.
- Attenzione ai processi che inviano dati a indirizzi con nomi di dominio sconosciuti o a indirizzi IP di paesi insoliti.
- Se noti molte connessioni aperte da un singolo processo verso IP multipli senza motivo apparente, potrebbe essere segno di un'infezione.

### 4. Analisi Avanzata e Uso di VirusTotal

- Per verificare se un processo è sicuro, individua il PID nella lista e controlla il nome del processo.
- Confronta il nome del processo con quelli comuni del sistema (es. `svchost.exe`, `chrome.exe`, `explorer.exe`).
- Clicca con il tasto destro su un processo sospetto e seleziona **Properties** per visualizzare il percorso del file.
- Per un'analisi approfondita, usa Process Explorer o VirusTotal per verificare se il file è segnalato come dannoso.

### 5. Terminare Connessioni Pericolose

- Se una connessione è sospetta, clicca con il tasto destro sul processo e seleziona **Close Connection**.
- Se il processo si riconnette automaticamente, potrebbe trattarsi di malware persistente. Usa Autoruns per bloccarlo all'avvio.
- Se il file è dannoso, rimuovilo manualmente o con un antivirus affidabile.

### 6. Diagnostica Avanzata e Confronto con altri Strumenti

| Funzionalità       | Task Manager | TCPView | Wireshark |
|--------------------|-------------|---------|-----------|
| Visualizzazione connessioni attive | ❌ | ✔️ | ✔️ |
| Identificazione IP remoto | ❌ | ✔️ | ✔️ |
| Terminare connessioni manualmente | ❌ | ✔️ | ❌ |
| Analisi dettagliata del traffico | ❌ | ❌ | ✔️ |

TCPView è uno strumento essenziale per il monitoraggio delle connessioni di rete e permette di identificare e chiudere attività sospette. Per un'analisi ancora più approfondita del traffico dati, è possibile utilizzare Wireshark.


### 3.4 Altri Strumenti Utili
3.4 Process Monitor (Monitoraggio Dettagliato delle Attività di Sistema)

Process Monitor (ProcMon) è uno degli strumenti più potenti della Sysinternals Suite, utile per tracciare in tempo reale ogni operazione eseguita dai processi sul sistema, come accessi ai file, modifiche ai registri e creazione di nuovi processi. Questo strumento è fondamentale per individuare comportamenti anomali e sospetti legati a malware.

### 1. Avvio di Process Monitor

- Apri la cartella Sysinternals e avvia `Procmon.exe`.
- Concedi i permessi di amministratore, se richiesto.
- Al primo avvio, vedrai un flusso continuo di eventi che potrebbero sembrare caotici. È necessario applicare dei filtri per ottenere informazioni utili.

### 2. Applicare Filtri per Individuare Attività Sospette

Process Monitor raccoglie enormi quantità di dati, quindi è essenziale filtrare i risultati:

- **Mostrare solo eventi legati a processi specifici:**
  - Vai su `Filter` → `Filter...` → `Process Name` → `is` → Digita il nome del processo sospetto → `Add` → `OK`.
- **Mostrare solo modifiche ai file:**
  - Filtro su `Operation` → `is` → `WriteFile`.
- **Mostrare solo modifiche al registro:**
  - Filtro su `Operation` → `is` → `RegSetValue`.
- **Mostrare solo esecuzioni di nuovi processi:**
  - Filtro su `Operation` → `is` → `Process Create`.

### 3. Identificare Attività Anomale

- Malware spesso crea o modifica chiavi di registro per garantirsi la persistenza. Se noti attività di `RegSetValue` su chiavi di avvio (`HKLM\Software\Microsoft\Windows\CurrentVersion\Run`), potrebbe trattarsi di un programma indesiderato.
- Alcuni virus scrivono file eseguibili in percorsi insoliti, come `C:\Users\Public\` o `C:\ProgramData\`. Se trovi operazioni `WriteFile` sospette in queste directory, verifica il file.
- Processi sconosciuti che si avviano ripetutamente (`Process Create`) senza il tuo intervento potrebbero essere segno di un’infezione.

### 4. Verifica con VirusTotal

- Clicca con il tasto destro sul processo sospetto → `Properties`.
- Copia il percorso del file e caricalo su [VirusTotal](https://www.virustotal.com) per verificare se è segnalato come minaccia.

### 5. Bloccare Processi e Rimuovere Minacce

- Se un processo è chiaramente dannoso, utilizza `Process Explorer` per terminarlo e individuarne l'origine.
- Se il processo viene riavviato automaticamente, usa `Autoruns` per disabilitarlo dall’avvio.
- Cancella manualmente eventuali file sospetti individuati in percorsi insoliti.

### 6. Diagnostica Avanzata e Confronto con altri Strumenti

| Funzionalità                  | Task Manager | Process Monitor | Wireshark |
|--------------------------------|-------------|----------------|-----------|
| Visualizzazione attività processi | ✔️ | ✔️ (dettagli avanzati) | ❌ |
| Tracciamento modifiche registro | ❌ | ✔️ | ❌ |
| Tracciamento modifiche file | ❌ | ✔️ | ❌ |
| Analisi traffico di rete | ❌ | ❌ | ✔️ |

Process Monitor è un tool indispensabile per il troubleshooting avanzato e l'analisi forense di possibili infezioni malware. Se usato in combinazione con gli altri strumenti della Sysinternals Suite, permette di rilevare e rimuovere minacce in modo efficace.

---

## 4. Verifica di Attività Sospette sul PC

Oltre agli strumenti già citati, è utile controllare:
- **Connessioni di rete:** Usa TCPView per monitorare eventuali comunicazioni indesiderate.
- **Applicazioni Installate:** Controlla nel Pannello di Controllo e nelle Impostazioni di Windows eventuali programmi sconosciuti o non autorizzati.
- **Avvii Automatici:** Utilizza Autoruns per verificare che non siano presenti voci anomale che si avviano all’accensione del PC.

---

## 5. Prevenzione e Consigli per il Futuro

- **Mantieni il Sistema Aggiornato:** Installa regolarmente gli aggiornamenti di Windows e dei software.
- **Scarica Solo da Fonti Affidabili:** Evita di installare programmi o file da siti non verificati.
- **Utilizza un Antivirus Affidabile:** Anche se la Sysinternals Suite aiuta a individuare malware, un buon antivirus è fondamentale per la protezione quotidiana.
- **Monitora il Sistema Periodicamente:** Controlla regolarmente i processi attivi e le connessioni di rete con gli strumenti della suite.

---

## 6. Conclusione

Seguendo i passaggi sopra indicati potrai individuare e rimuovere virus e malware dal tuo sistema utilizzando la Sysinternals Suite. 
Per ulteriori dettagli e una dimostrazione pratica, consulta il video:
**[“Come scoprire se hai un VIRUS NASCOSTO nel PC (e cosa fare)” – nFire](https://www.youtube.com/watch?v=zDDGme4BIys)**

Ricorda che, in caso di infezioni persistenti o problemi gravi, potrebbe essere necessario rivolgersi a un tecnico specializzato.