# **MiniPC Windows - Checklist per Malware e Backdoor**

**📅 Informazioni aggiornate al 29/12/2024**
*Basate su analisi di video e report tra Febbraio e Aprile 2024.*

## ⚠️ **Premessa**
I MiniPC Windows, indipendentemente dal produttore, possono presentare malware preinstallati o backdoor che mettono a rischio la sicurezza dei vostri dati. 
Questa guida fornisce i controlli di base da effettuare al primo avvio.

---

## 🛡️ **1. Controllo Iniziale del Sistema**
- Windows, per impostazione predefinita, ha **Microsoft Edge** come unico browser.
- **Se trovi Google Chrome o Firefox già installati**, potrebbe trattarsi di software malevolo.

## 🔍 **2. Analisi con Windows Defender**
- Apri **Sicurezza di Windows (Windows Defender)**.
- Assicurati che tutto sia aggiornato e che lo stato del sistema sia "Protetto".
- Esegui una **Analisi Veloce** per rilevare eventuali minacce.

**🔗 Esempio di Malware Rilevato:**
```
Nome: Backdoor:Win32/bladabindi|ml
Gravità: Grave
Stato: Attivo
Categoria: Backdoor
Dettagli: Questo programma fornisce accesso remoto al computer su cui è installato.
Percorso: C:\Recovery\OEM\OsVer\ENDIDEV.exe
```

---

## 📂 **3. Controllo dei File Nascosti**
- Abilita **"Visualizza cartelle, file e unità nascosti"** dalle opzioni di Esplora File.
- Anche con questa opzione abilitata, alcuni percorsi potrebbero restare invisibili.
- Nella barra degli indirizzi di Esplora File, incolla il seguente percorso:
  ```
  C:\Recovery
  ```
- Se la cartella sembra non esistere o contiene file sospetti, analizza i file con **VirusTotal**.
- **Consiglio:** Se VirusTotal segnala anche un minimo rischio, elimina la cartella.

---

## 🛠️ **4. Controllo delle Applicazioni Installate**
- Vai su **Impostazioni > App > App installate**.
- Verifica la presenza di applicazioni sconosciute o sospette.
- Disinstalla tutto ciò che sembra anomalo.

---

## 🔑 **5. Altri Controlli di Sicurezza**
- Aggiorna **Windows** all'ultima versione disponibile.
- Disabilita **Servizi o Attività Pianificate** sospette.
- Esegui periodicamente una **Scansione Completa** con Windows Defender.

---

## 💡 **Riflessione Finale**
Un MiniPC può essere economico, ma il vero prodotto **sei tu** e i tuoi dati.
Proteggi la tua privacy e sicurezza seguendo attentamente questa guida.

🔗 Strumenti utili:
- [VirusTotal](https://www.virustotal.com)
- Windows Defender

**📝 Nota:** Se il sospetto persiste, valuta un ripristino completo del sistema operativo... 
...anche se perderai la versione di Windows con la sua chiave (esempio con Windows Professional), 
e dovrai attivarla ottenendo una chiave di windows, ma almeno sei al sicuro e non ci saranno più dubbi, sei al sicuro.

---

**🛡️ Sicurezza prima di tutto!**
