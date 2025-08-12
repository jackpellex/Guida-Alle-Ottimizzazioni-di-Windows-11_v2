# Guida Avanzata alle Ottimizzazioni su Windows 11

> 🎮 **Ottimizza Windows 11 per il gaming e l’uso quotidiano** 🔧  
> Progettata per **utenti esperti e non**, questa guida ti mostra percorsi **sicuri e avanzati** per massimizzare le prestazioni software e hardware del tuo PC.

## CleanOS: Personalizza la Tua Installazione di Windows 11 per una Base Stabile

Prima di immergerti nelle ottimizzazioni, puoi gettare le fondamenta per un sistema pulito e performante. Questa guida include una sezione dedicata a **CleanOS**, che ti permette di creare un'installazione personalizzata di Windows 10/11 fin dall'inizio.

Questo significa che potrai avere un'immagine ISO su misura, **priva di bloatware** (software preinstallato non necessario) e già configurata con le tue preferenze di lingua, regione, account utente, impostazioni di rete e privacy.

Utilizzando l'**Unattend Generator** e seguendo il percorso indicato in `2_Personalizzazione/CleanOS.md`, ti assicurerai che il tuo sistema parta già da una **base stabile e ottimizzata**, priva di elementi superflui che potrebbero influire sulle prestazioni future.

---

## 📑 Indice

1. [Scopo della Guida](#scopo-della-guida)  
2. [Struttura delle Cartelle](#struttura-delle-cartelle)  
3. [Prestazioni Realistiche vs. Extreme Tuning](#prestazioni-realistiche-vs-extreme-tuning)  
4. [Sezioni Principali](#sezioni-principali)  
   - [Ottimizzazioni](#ottimizzazioni)  
   - [Personalizzazione](#personalizzazione)  
   - [Risoluzione Errori](#risoluzione-errori)  
   - [Sicurezza](#sicurezza)  
5. [Linee Guida di Stile](#linee-guida-di-stile)  

---

## Scopo della Guida

Questa guida ti accompagnerà passo dopo passo nell’**ottimizzazione di Windows 11** con un focus sul **gaming** e sul **massimo rendimento** del sistema:

- Percorsi **sicuri**: modifiche consigliate per un +8% medio di FPS e minore latenza input.  
- **Extreme tuning**: opzioni **sconsigliate** per un potenziale +30–40% FPS, evidenziate con avvertenze chiare (rischio di instabilità variabile a seconda della configurazione).

Perfetta sia per chi vuole migliorare in modo stabile, sia per sperimentatori pronti a correre qualche rischio.

---

## Struttura delle Cartelle

- **App_e_Siti/**: applicazioni e risorse esterne per test hardware, monitoraggio e ottimizzazione.  
- **Collegamenti/**: scorciatoie a impostazioni di sistema e tool avanzati.  
- **Icone/**: set di icone personalizzate per abbellire e distinguere le cartelle.  
- **1_Ottimizzazioni/**: tecniche di tuning per CPU, GPU, I/O e avvio di sistema.  
- **2_Personalizzazione/**: temi, layout, automazioni e script per adattare UI/UX.  
- **3_Risoluzione_Errori/**: diagnostica, log, riparazione file e recupero configurazioni.  
- **4_Sicurezza/**: hardening, crittografia, protezione memoria e best practice difensive.  
- **README.md**: punto di partenza e indice di tutta la guida.

> Le cartelle **1–4** sono il cuore dell’ottimizzazione: esplorale con ordine e attenzione.

---
## Prestazioni Realistiche vs. Extreme Tuning

Quando si parla di ottimizzazione delle prestazioni grafiche (tuning), è fondamentale distinguere tra un approccio sicuro e uno più estremo, soprattutto in base all'hardware del proprio sistema.

### Sistemi Moderni

Per i sistemi più recenti, equipaggiati con hardware performante, le aspettative di miglioramento dovrebbero essere realistiche e mirate alla stabilità:

* **Tuning Sicuro:** Questo tipo di ottimizzazione punta a un aumento medio delle prestazioni di circa **+8% di FPS**, garantendo al contempo una maggiore fluidità di gioco e una riduzione della latenza. Si concentra su piccole modifiche che migliorano l'esperienza senza compromettere la stabilità del sistema.
* **Tuning Estremo (Sconsigliato):** Spingersi oltre con un tuning aggressivo può portare a un incremento degli FPS **fino al +30-40%**. Tuttavia, questo approccio è altamente **sconsigliato** a causa dell'elevato **rischio di crash**, l'insorgere di artefatti video e una generale instabilità del sistema. I benefici percepiti non giustificano i potenziali problemi.

### Sistemi Meno Recenti

Per i sistemi più datati, l'ottimizzazione può offrire margini di miglioramento potenzialmente più significativi, dato che il software è spesso più limitato dall'hardware obsoleto:

* **Tuning Sicuro:** Anche su hardware più vecchio, un tuning sicuro può portare a benefici interessanti. L'aumento medio degli FPS potrebbe essere **superiore al +8%** visto sui sistemi moderni, contribuendo a rendere i giochi più giocabili e reattivi, pur mantenendo un'ottima stabilità.
* **Tuning Estremo (Sconsigliato):** Similmente ai sistemi moderni, anche sui PC meno recenti il tuning estremo può promettere incrementi di FPS **fino al +30-40% o anche di più**. Tuttavia, i rischi di **instabilità, crash frequenti e artefatti visivi** sono ancora più elevati su hardware meno tollerante. La stabilità del sistema ne risentirebbe gravemente, compromettendo l'usabilità generale.

> ⚠️ Ogni modifica estrema è segnalata da un avviso e va testata su singola macchina.


---

## Sezioni Principali

### Ottimizzazioni 📈
- **Aggiornamento Applicazioni**:
  - Utilizza **winget** e **Chocolatey** per mantenere software aggiornati con un singolo comando: `winget upgrade --all` o `choco upgrade all -y`.
- **Eseguibile .bat**:
  - Script di pulizia per eliminare file temporanei: `cleanmgr /sagerun:1` o personalizza un `.bat` che rimuove `%temp%`, cache browser e log di sistema obsoleti.
- **BIOS Tweaks** (⚠️ sconsigliato in ambienti di produzione):
  - **Hyper-Threading Disabled** per ridurre latenza in alcuni giochi CPU-bound.
- **Terminale PowerShell**:
  - **Compressione della memoria**: `Enable-MMAgent -MemoryCompression`.
  - **Sleep States**: disabilita stati di basso consumo (S1–S3) in sistemi desktop per ridurre lag.
- **Configurazione di Sistema**:
  - Rilevamento e affinità core avanzata via `bcdedit /set {current} numproc N`.
- **Ottimizzazione Connessione e Rete**:
  - Regola TCP Window Scaling e auto-tuning: `netsh interface tcp set global autotuninglevel=high`.
- **Gestione Attività**:
  - Disabilita startup non necessari dal Task Manager.
  - Imposta priorità app gaming su **Alta**.
  - Usa **Process Explorer** per analisi avanzata.
- **Gestione Disco**:
  - Deframmentazione SSD disabilitata, esegui TRIM: `Optimize-Volume -DriveLetter C -ReTrim -Verbose`.
  - Indicizzazione file: Mantiene un indice per ricerche rapide. Benefico per la velocità di ricerca su desktop moderni (SSD). Configura le "Opzioni di indicizzazione" per includere/escludere specifiche cartelle.
- **GPU Tweaks**:
  - Regola consumi e power limit via tool del vendor (NVIDIA/AMD).
  - Abilita riduzione latenza input nei driver.
  - Comprendi e scegli tra Fullscreen Esclusivo e Finestra Borderless per ottimizzare ulteriormente le performance e la latenza.
- **HPET** (⚠️ sconsigliato):
  - `bcdedit /set useplatformclock true/false`, testare per possibili miglioramenti di stabilità.
- **Impostazioni di Sistema**:
  - Disabilita app in background.
  - Usa il **Sensore di memoria** in Sicurezza di Windows.
  - Disattiva raccolta Telemetria superflua e colori non essenziali.
- **Opzioni Prestazioni**:
  - Configura Memoria Virtuale manualmente: dimensione iniziale e massima tra 1.5× RAM e 3.0x RAM. Assicurati di riservare abbastanza spazio libero sul disco (almeno 1,5x - 3x della RAM disponibile)
  - Ottimizza effetti visivi su **Prestazioni migliori**.
- **Programmi da Disinstallare**:
  - Rimuovi app preinstallate non necessarie dal Pannello di controllo.
- **Performance Monitor**:
  - Crea baseline di prestazioni e traccia counter critici.
- **Editor del Registro (Regedit)** (⚠️):
  - Abilita **Fast Startup**: `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\Power` → `HiberbootEnabled = 1`.
  - Disabilita GameDVR: `HKEY_CURRENT_USER\System\GameConfigStore` → `GameDVR_Enabled = 0`.
  - Imposta `SvcHostSplitThresholdInKB` e `Win32PrioritySeparation` per bilanciare avvio servizi e priorità.
  - Ottimizza la priorità per i giochi: `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Multimedia\SystemProfile\Tasks\Games` → imposta `GPU Priority = 8`, `Priority = 6` e `Scheduling Category = High` per migliorare FPS e reattività.
- **Resource Monitor**:
  - Monitora I/O, CPU, RAM e rete in tempo reale per individuare colli di bottiglia.
- **Servizi Windows**:
  - Disattiva servizi non essenziali (Fax, Print Spooler se non usati).
  - Mantieni attivo **Windows Update**, **Security Center** e **Driver Frameworks**.

### Personalizzazione 🎨
- **Installazione Personalizzata e Automatizzata (CleanOS)**:
  - Vuoi un'installazione di Windows 10/11 su misura, senza bloatware e con le tue configurazioni predefinite? Segui la guida **CleanOS.md** nella cartella **2_Personalizzazione/** per creare un supporto di installazione automatico e pulito usando l'Unattend Generator. Questo ti permette di definire lingua, regione, account utente, impostazioni di rete e privacy fin dal primo avvio del sistema.
- **Desktop Pulito**:
  - Mantieni il desktop il più sgombro possibile: sposta Documenti, Download e collegamenti in cartelle dedicate (`C:\Users\%USERNAME%\Documenti`, ecc.).  
  - Organizza i file con struttura gerarchica e usa **cartelle dei Preferiti** nel File Explorer.  
  - Riduci il caricamento di file all’avvio: rimuovi shortcut superflui dalla cartella `Startup` (`shell:startup`).
- **Mouse Migliorato**:
  - **DPI**: configura DPI e Polling Rate dal software del driver (Logitech G HUB, Razer Synapse, ecc.) per trovare il giusto compromesso tra precisione e velocità.
  - **Disabilitazione accelerazione**: apri **Pannello di controllo → Mouse → Opzioni puntatore** e deseleziona **Migliora precisione puntatore**.
  - **Modifiche al Registro** (⚠️)
- **Aggiustamenti dello Schermo**:
  - **Refresh Rate**: vai in **Impostazioni → Sistema → Schermo → Impostazioni schermo avanzate** e seleziona il massimo refresh supportato.
  - **Calibrazione Colori**: esegui **Calibra colori dello schermo** da **Pannello di controllo → Schermo** per regolare gamma, luminosità e contrasto.
  - **Scaling DPI**: in **Impostazioni → Sistema → Schermo**, regola lo **scaling** su percentuali personalizzate per evitare sfasamenti grafici su display ad alta risoluzione.

### Risoluzione Errori 🛠️

In questa sezione troverai strumenti e procedure per individuare e correggere problemi comuni su Windows 11. L’obiettivo è garantire **stabilità**, **ripristino rapido** e **prestazioni costanti** del sistema operativo.

#### 🧮 Comandi Utili da Terminale

- `CHKDSK`: verifica e corregge errori del file system.  
- `DISM /Online /Cleanup-Image /RestoreHealth`: ripara l'immagine di sistema danneggiata.  
- `SFC /scannow`: ripristina file di sistema corrotti.  
- `PowerCFG /energy`: analizza il consumo energetico e identifica inefficienze.  
- `Winsat formal`: aggiorna il punteggio prestazionale del sistema.

#### ⚙️ Configurazione di Sistema

- Rilevamento errato dei core logici:  
  1. Apri **msconfig**.  
  2. Vai in **Avvio** → **Opzioni avanzate**.  
  3. Imposta il numero di processori correttamente.

#### 💾 Disco: Deframmentazione e Ottimizzazione

- **HDD**: usa l’Utilità “Deframmenta e ottimizza unità”.  
- **SSD**: lascia attiva l’ottimizzazione automatica (no deframmentazione manuale!).

#### 🧠 Diagnostica della Memoria

- Avvia **Diagnostica memoria di Windows** (`mdsched.exe`) per testare eventuali problemi hardware nella RAM.

#### 🧾 Event Viewer

- Accedi con `eventvwr.msc`.  
- Analizza i log di **Sistema**, **Applicazione** e **Sicurezza** per identificare crash o errori ricorrenti.

#### ⚠️ Errori 2502 e 2503

- Cause: permessi mancanti nelle cartelle temporanee.  
- Soluzioni:
  1. Esegui **Esplora file** come amministratore.  
  2. Modifica permessi su `C:\Windows\Temp` e `C:\Temp`.  
  3. Avvia l’installazione con privilegi elevati (`.msi` da prompt).

#### 🧱 Driver Grafici

- Usa **DDU (Display Driver Uninstaller)** in modalità provvisoria per rimuovere completamente i driver.  
- Reinstalla l’ultima versione dal sito NVIDIA o AMD.

#### 📉 Monitoraggio Affidabilità

- Cerca **Affidabilità** nella barra di ricerca → **Visualizza cronologia affidabilità**.  
- Monitora crash, errori e warning per identificare pattern di instabilità.

#### 🔁 QMR (Quick Machine Recovery)

- Sistema di snapshot e backup automatico.  
- Ripristina lo stato precedente in pochi istanti in caso di problemi critici.

#### 🧼 Strumento di Pulizia

- Esegui **Pulizia disco** o usa comandi PowerShell/Batch per:
  - Eliminare file temporanei, cache e log non necessari.  
  - Liberare spazio e migliorare la reattività generale.

#### 🛠️ Strumento di Risoluzione dei Problemi

- Accesso rapido: `ms-settings:troubleshoot`.  
- Diagnostica guidata per audio, rete, aggiornamenti e periferiche.

#### 🔄 Script Batch: Reset Windows Update
In sintesi, lo script:

- Ferma i servizi di aggiornamento
- Elimina file e cache corrotti
- Ripara le registrazioni delle librerie critiche
- Ripristina componenti di rete
- Riavvia i servizi puliti

- Il risultato atteso è un ambiente Windows Update “resettato”, spesso risolutivo per errori come 0x80070005, download bloccati o aggiornamenti che non partono.

### Sicurezza 🔒
Questa sezione copre le **misure difensive** e le **best practice** per proteggere il tuo sistema, i dati e gli account.

#### 🛡️ Disattivare Recall
- Windows Analizza immagini localmente con AI e salva risultati in un DB SQLite non crittografato nella cartella utente.
- Disabilita in **Impostazioni → Privacy & sicurezza → AI e servizi multimediali → Recall**.

#### 🔄 Creazione Punto di Ripristino
> **PRIMA DI TUTTO**, crea sempre un punto di ripristino:  
1. Apri **Pannello di controllo → Sistema → Protezione sistema**.  
2. Seleziona l’unità di sistema e clicca **Crea…**.  
3. Nomina il punto e conferma.

#### 🔐 Gestione Disco: Crittografia
- **BitLocker On/Off**:
  - Attiva in **Pannello di controllo → Sistema e sicurezza → Crittografia unità BitLocker**.
  - Ricorda di salvare la chiave di ripristino.

#### ⏯️ Disabilitare Autoplay
- Prevenzione: un drive USB con firmware riprogrammabile può caricare malware automaticamente.
- Disattiva in **Impostazioni → Dispositivi → Autoplay → Disattiva per tutti i supporti**.

#### 🔒 Sicurezza Account Google
- **Dispositivo perso**: revoca sessioni da https://myaccount.google.com/security → **Gestisci dispositivi**.
- **Accesso software**: cambia password, abilita 2FA e rivedi app con accesso (OAuth).
- **Accesso fisico**: cancella token locali, modifica password e richiedi logout da tutti i dispositivi.

#### 🕵️‍♂️ Identificare e Rimuovere Virus
- **Task Manager**: processi sospetti, uso anomalo di CPU/RAM.
- **Windows Defender**: esegui scansione completa e offline.
- **App di avvio**: disabilita voci non riconosciute in `shell:startup` e Task Manager.
- **Traffico rete**: `netstat -abno` per connettere processi a porte.

#### 🖥️ Problemi MiniPC Modificati
- Virus “PuabundlerWIN32”: malware preinstallato su MiniPC cinesi.
- **Rimozione**: avvia Safe Mode, esegui scansione Malwarebytes e Defender.
- **Sysinternals**:
  - **Autoruns** per controllare esecuzioni all’avvio.
  - **Process Explorer** per ispezionare DLL/caricamenti.
  - **TCPView** per connessioni sospette.

#### 🛡️ Potenziare Windows Defender
- **Memory Integrity**: Attiva in **Sicurezza di Windows → Sicurezza dispositivo → Integrità memoria**.
- **Periodic Scanning**: abilita scansione offline in Defender.

#### 📑 Consigli Generali di Sicurezza
- Sistema operativo sempre aggiornato.  
- Usa password forti, 2FA e gestore di password.  
- Crittografa dischi e backup.  
- Scegli software open‑source e rispetta il minimalismo digitale.  
- Naviga con browser privacy‑oriented, VPN, DNS sicuri.  
- Imposta permessi restrittivi per app e servizi.  
- Disabilita Bluetooth/RF quando non in uso.  
- Valuta VM o OS alternativi per attività sensibili.  
- Hardening avanzato tramite Group Policy e registry tweak.
- Documenta tutte le modifiche e automatizza verifiche periodiche.

---

## Linee Guida di Stile

- **Numerazione Step**  
- **Avvertenze** evidenziate con emoji ⚠️ e box dedicati.  
- **Backup & Ripristino** all’inizio di ogni sezione critica.  
- **Nomenclatura** coerente con prefisso numerico per ordine logico.

