# Ottimizzazione della Connessione Internet: Ethernet e Wi-Fi

## A.1) Ottimizzare Ethernet (Cablato)

1. **Accedi alle proprietà di Ethernet**:  
   Consente di modificare le impostazioni della connessione Ethernet per migliorarne le prestazioni.  
   - Vai su **Ethernet** e clicca su **Proprietà**.
   - Seleziona **Protocollo Internet versione 4 (TCP/IPv4)** e clicca su **Proprietà**.

2. **Modifica i DNS**:  
   I server DNS predefiniti possono essere sostituiti con server più veloci e sicuri.  
   - Imposta come predefinito: **Ottieni indirizzo server DNS automaticamente**.
   - Cambia l'opzione a **Utilizza i seguenti indirizzi DNS**.
     - **Server DNS preferito**: `1.1.1.1`
     - **Server DNS alternativo**: `1.0.0.1`
   > **Nota**: I server DNS **1.1.1.1** e **1.0.0.1** sono offerti da Cloudflare e noti per la velocità e sicurezza.

3. **Configura la Velocità di Connessione**:  
   Regolare la velocità e duplex della scheda di rete può migliorare la stabilità della connessione.  
   - Clicca su **OK** per salvare le modifiche.
   - Vai su **Configura...**.
   - Nella scheda **Generale**, clicca su **Avanzate**.
   - Sotto **Velocità e duplex**, cambia l'impostazione da **Negoziazione automatica** a **1 Gbps Full Duplex**.

4. **Abilita Flow Control**  
   - Sempre in **Avanzate**, cerca **Flow Control** o **Controllo di flusso** e attivalo.  
   - Migliora la stabilità in caso di congestione del network o buffer overflow.
---

## A.2) Ottimizzare Wi-Fi (Wireless)

1. **Accedi alle proprietà di Wi-Fi**:  
   Analogamente alla connessione Ethernet, qui si configurano i parametri di rete Wi-Fi.  
   - Clicca con il tasto destro sul **Wi-Fi** e seleziona **Proprietà**.
   - Seleziona **Protocololo Internet versione 4 (TCP/IPv4)** e clicca su **Proprietà**.

2. **Modifica i DNS**:  
   Modifica i server DNS per ottenere prestazioni migliori.  
   - Imposta come predefinito: **Ottieni indirizzo server DNS automaticamente**.
   - Cambia l'opzione a **Utilizza i seguenti indirizzi DNS**.
     - **Server DNS preferito**: `1.1.1.1`
     - **Server DNS alternativo**: `1.0.0.1`  

   > **Nota**: I server DNS **1.1.1.1** e **1.0.0.1** sono offerti da Cloudflare e noti per la velocità e sicurezza.

3. **Clicca su OK** per salvare le modifiche.

---

## B) Ottimizzare la Larghezza di Banda con QoS

1. **Apri l'Editor Criteri di Gruppo**:  
   Permette di configurare l'utilizzo della larghezza di banda riservata al sistema operativo.  
   - Premi `Windows + R`, digita `gpedit.msc` e premi **Invio**.
   - Vai a **Modelli amministrativi** > **Rete** > **Utilità di pianificazione pacchetti QoS**.
   - Seleziona **Limita larghezza di banda riservabile**.

2. **Abilita e Modifica la Larghezza di Banda**:  
   Rimuovendo la riserva di larghezza di banda, puoi sfruttare il 100% della connessione.  
   - Di default, questa opzione è **Non configurata** o **Disattivata**, e il sistema utilizza solo l'80% della larghezza di banda.
   - Imposta l'opzione su **Attivata** e inserisci **0%** di larghezza di banda per utilizzare il 100% del potenziale della tua connessione.  

   > **Nota Importante**: Se più utenti utilizzano questa configurazione sulla stessa rete Wi-Fi o Hotspot, si potrebbe verificare instabilità o rallentamenti nella rete.

---

## C) Comandi per Ripristinare e Migliorare la Rete

1. **Prompt dei comandi (amministratore)**  
   ```bat
   ipconfig /flushdns
   ipconfig /registerdns
   ipconfig /release
   ipconfig /renew
   netsh winsock reset
   netsh interface tcp set global autotuninglevel=normal
   netsh interface tcp set global chimney=disabled
   netsh interface tcp set global ecncapability=disabled
   ```

2. **Esegui tutto in un’unica riga**  
   ```bat
   ipconfig /flushdns && ipconfig /registerdns && ipconfig /release && ipconfig /renew && netsh winsock reset
   ```

3. **Riavvia il PC**  
   - Applica le modifiche di Winsock e TCP/IP al riavvio.

---

1. **Esegui i seguenti comandi nel Prompt dei Comandi con privilegi di amministratore**:  
   Questi comandi risolvono problemi comuni di rete e aggiornano la configurazione.  
   - Apri il **Prompt dei Comandi** come amministratore e digita i seguenti comandi:

   ```bash
   ipconfig /flushdns
   ipconfig /registerdns
   ipconfig /release
   ipconfig /renew
   netsh winsock reset

   - Per eseguire tutti i comandi in una sola riga:

   ipconfig /flushdns && ipconfig /registerdns && ipconfig /release && ipconfig /renew && netsh winsock reset


2. **Applica le modifiche e riavvia il computer**.

---

## D) Firmware obsoleto

**Descrizione del problema**  
Il firmware è l’“sistema operativo” interno del router: versioni datate possono contenere bug, falle di sicurezza e non beneficiare delle ultime ottimizzazioni per stabilità e throughput :contentReference[oaicite:0]{index=0}.

**Effetti sulla connessione**  
- Cadute improvvise del segnale  
- Latenza variabile e packet loss  
- Prestazioni inferiori al potenziale dell’hardware :contentReference[oaicite:1]{index=1}

**Soluzione**  
1. **Controlla la versione attuale**  
   - Accedi all’interfaccia web del router (es. `192.168.1.1`) → Stato → Versione firmware.  
2. **Scarica l’ultimo firmware**  
   - Vai al sito ufficiale del produttore e scarica il firmware esatto per il tuo modello (hardware revision) :contentReference[oaicite:2]{index=2}.  
3. **Backup della configurazione**  
   - In **System Tools → Backup & Restore**, esporta le impostazioni.  
4. **Aggiorna il firmware**  
   - In **System Tools → Firmware Upgrade**, carica il file scaricato e avvia l’aggiornamento.  
5. **Riavvia il router**  
   - Attendi il riavvio automatico, verifica che la versione sia aggiornata e ripristina il backup se necessario.

---

## D) Cambiare canale

**Perché**  
Le reti Wi‑Fi nelle vicinanze possono interferire se trasmettono sullo stesso canale, soprattutto in 2.4 GHz dove i canali non si sovrappongono sono solo 1, 6 e 11. Cambiare su un canale meno congestionato riduce interferenze e migliora throughput e latenza :contentReference[oaicite:3]{index=3}.

**Effetti sulla connessione**  
- Velocità minori in presenza di molte reti vicine  
- Aumento di ritrasmissioni e ritardi  
- Possibili disconnessioni sporadiche :contentReference[oaicite:4]{index=4}

**Soluzione**  
1. **Analizza il panorama Wi‑Fi**  
   - Usa un’app “Wi‑Fi analyzer” (Android, iOS o PC) per identificare i canali meno usati.  
2. **Accedi all’interfaccia del router**  
   - Apri il browser su `http://192.168.1.1` (o IP del tuo gateway).  
3. **Modifica il canale**  
   - Vai in **Wireless Settings → Channel**.  
   - Seleziona, su 2.4 GHz, un canale libero (1, 6 o 11) con minori reti rilevate.  
   - Su 5 GHz scegli un canale 36–48 o, se supportato, un DFS (52–64) per meno congestione.  
4. **Salva e riavvia**  
   - Applica le modifiche e, se richiesto, riavvia il router per rendere effettive le nuove impostazioni.

> **Suggerimento**: ripeti l’analisi ogni pochi mesi, poiché nuove reti vicine potrebbero cambiare lo scenario.


---

## E) Utilizzare l'App TCP Optimizer

1. **Scarica e installa TCP Optimizer**:
   - Per scaricare l'applicazione, vai su [TCP Optimizer - Download](https://www.speedguide.net/downloads.php).

2. **Impostazioni di TCP Optimizer**:
   - Apri l'app e regola lo **Slider della "Connection Speed"** al massimo.
   - Imposta **MTU** a **1500**.
   - Configura i seguenti parametri:
     - **TCP WINDOW Auto-Tuning**: Normal
     - **Windows Scaling Heuristics**: Disabilitato
     - **Congestion Control Provider**: Ctcp
     - **Receive-Side Scaling (RSS)**: Abilitato
     - **R Segment Coalescing (RSC)**: Abilitato
     - **Time To Live (TTL)**: 64
     - **ECN Capability**: Disabilitato
     - **Checksum Offloading**: Disabilitato
     - **TCP Chimney Offload**: Disabilitato
     - **Large Send Offload (LSO)**: Disabilitato
     - **TCP 1323 Timestamps**: Disabilitato

3. **Avanzate Impostazioni**:
   - Vai su **Advanced Settings** e modifica i seguenti valori:
     - **MaxConnectionsPer1_0Server**: 10
     - **MaxConnectionsPerServer**: 10
     - **LocalPriority**: 4
     - **HostPriority**: 5
     - **DnsPriority**: 6
     - **NetbtPriority**: 7
     - **Max SYN Retransmissions**: 2
     - **NonSackRttResilency**: Disabilitato
     - **Initial RTO**: 2000
     - **Min RTO**: 300
     - **QoS NonBestEffortLimit**: 0
     - **QoS: Do not use NLA**: Ottimale
     - **NetworkThrottlingIndex**: Disabilitato
     - **SystemResponsiveness**: Gaming
     - **TcpAckFrequency**: Disabilitato
     - **TCPNoDelay**: Abilitato
     - **TcpDelAck Ticks**: Disabilitato
     - **LargeSystemCache**: Default
     - **TcpTimedWatDelay**: 30

4. **Applica le modifiche e riavvia il computer**.


Rispetto a questa Guida, ho preso spunto da questo video:
[nFire][https://www.youtube.com/watch?v=XmCSsr3Ei6o]