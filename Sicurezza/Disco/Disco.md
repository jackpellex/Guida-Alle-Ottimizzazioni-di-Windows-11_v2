### 🛠️ **Crittografia del Disco con BitLocker**

La crittografia del disco con **BitLocker** serve a garantire la protezione dei dati sensibili in caso di furto o smarrimento del dispositivo, impedendo l'accesso non autorizzato ai file.

---

## 📝 **Prerequisiti**

- Edizione Windows Pro, Enterprise o Education.
- TPM (Trusted Platform Module) versione 1.2 o superiore consigliato, ma non obbligatorio.
- Account amministratore.
- Backup della chiave di ripristino (su file, account Microsoft o stampato).

---

## 🔐 **1. Attivazione di BitLocker**

1. Apri **Pannello di controllo** → **Sistema e sicurezza** → **Crittografia unità BitLocker**.
2. Seleziona l'unità da criptare (es. `C:`) e clicca su **Attiva BitLocker**.
3. Scegli il metodo di sblocco:
   - **Password** all'avvio.
   - **PIN** con TPM.
   - **Smart card**.
4. Salva la **chiave di ripristino**:
   - Su file `.txt` (in un supporto esterno).
   - Sul tuo account Microsoft.
   - Stampala e conservala in un luogo sicuro.
5. Scegli la modalità di crittografia:
   - **Nuova modalità di crittografia** (migliore per unità fisse in Windows 10/11).
   - **Compatibile con versioni precedenti** (per dispositivi mobili o altri PC).
6. Seleziona **Cripta solo lo spazio utilizzato** (più veloce) oppure **Cripta l'intera unità** (più sicuro).
7. Avvia la crittografia e attendi il completamento (può richiedere tempo in base alle dimensioni del disco).

---

## 🔓 **2. Disattivazione di BitLocker**

1. Apri **Pannello di controllo** → **Sistema e sicurezza** → **Crittografia unità BitLocker**.
2. Trova l'unità criptata e clicca su **Disattiva BitLocker**.
3. Conferma l’operazione: BitLocker decifrerà il disco riportandolo allo stato originale.

---

## ⚙️ **3. Funzionalità Avanzate**

- **Auto-Unlock**: sblocca automaticamente unità secondarie dopo l'accesso al sistema.
- **Network Unlock**: sblocco automatico quando connessi a rete aziendale (richiede configurazione AD e PKI).
- **Crittografia di unità rimovibili** (BitLocker To Go).
- **Protezione TPM**: lega la chiave al TPM per rafforzare la sicurezza.

---

## 📊 **4. Impatto sulle Prestazioni**

- Tipico impatto: **2–5%** in lettura/scrittura su SSD e HDD.
- Processori moderni (AES-NI) riducono al minimo l'overhead.
- Su hardware più vecchio, la cifratura può causare ritardi più evidenti durante avvio e operazioni I/O intensive.

---

## 🧠 **5. Crittografia della RAM**

> **Nota:** la memoria volatile (RAM) **non** è criptata da BitLocker. Dopo lo spegnimento o la sospensione, i dati in memoria possono essere recuperati da attacchi di cold boot.

**Consigli per la RAM**:

- Attiva **Protezione integrità memoria** (Memory Integrity) in **Sicurezza di Windows → Sicurezza dispositivo → Integrità memoria**.
- Valuta soluzioni di terze parti come **TRESOR** o **PureBoot** per cifratura e protezione avanzata.
- Verifica in più, di bloccare l’avvio non autorizzato (su BIOS/UEFI) e usare la modalità di sospensione ibrida.

---

## 📚 **Riferimenti**

- Documentazione ufficiale Microsoft BitLocker: https://docs.microsoft.com/bitlocker
- Approfondimenti performance AES-NI su Windows 10.

---

