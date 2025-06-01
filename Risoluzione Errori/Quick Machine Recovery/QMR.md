# Guida a Quick Machine Recovery (QMR)

Il **Quick Machine Recovery (QMR)** è una funzionalità di Windows Resiliency introdotta nelle versioni Insider Preview di Windows 11. Permette di **ripristinare automaticamente** il sistema in caso di problemi critici, riducendo i tempi di inattività e migliorando la stabilità del PC.

---

## 1. Panoramica

- QMR fa parte dell’iniziativa **Windows Resiliency**.  
- Automatico: rileva crash ripetuti all’avvio e avvia la procedura di recovery.  
- Riduce la necessità di interventi manuali e facilita la gestione dei crash di sistema.

---

## 2. Come funziona

### 2.1 Cloud Remediation

- Quando abilitata, la macchina si connette a **Windows Update** durante la fase di recovery per scaricare patch o fix disponibili.  
- Se **disabilitata**, Windows utilizza **Startup Repair** in locale.

### 2.2 Auto Remediation

- Quando abilitata, il sistema:  
  1. Tenta automaticamente di connettersi a Windows Update.  
  2. Se non trova subito una soluzione, riprova più volte senza richiedere interventi.  
- Se disabilitata o non configurata, richiede intervento manuale per proseguire.

---

## 3. Processo di QMR

1. **Device crash**  
   Windows rileva ripetuti fallimenti di avvio.  
2. **Boot to recovery**  
   Il PC avvia l’ambiente di recovery (Windows RE).  
3. **Network connection**  
   Una volta stabilita la rete, inizia la ricerca di remediation su Windows Update.  
4. **Remediation**  
   - Se non trova soluzioni, riprova secondo i parametri di retry e timeout configurati.  
   - Se trova una soluzione, la scarica e applica.  
5. **Reboot**  
   - Se il fix ha successo, il sistema ritorna in Windows.  
   - Altrimenti, riavvia nuovamente in recovery e ripete il ciclo.

---

## 4. File di configurazione: `QMR.xml`

Posiziona in `C:\QMR\QMR.xml` il seguente file XML:

```xml
<?xml version='1.0' encoding='utf-8'?>
<WindowsRE>
    <WifiCredential>
        <Wifi ssid="NomeDelTuoWiFi" password="PasswordDelTuoWiFi" />
    </WifiCredential>
    <CloudRemediation state="1" />
    <AutoRemediation state="1" totalwaittime="120" waitinterval="2"/>
</WindowsRE>
```

- **WifiCredential**: credenziali Wi‑Fi per connettersi alla rete in recovery.  
- **CloudRemediation state**: `1` = abilitato, `0` = disabilitato.  
- **AutoRemediation state**: `1` = abilitato, `0` = disabilitato.  
- **totalwaittime**: tempo massimo (in secondi) per i retry.  
- **waitinterval**: intervallo (in secondi) tra ogni tentativo.

---

## 5. Comandi per il terminale

- **Applica le impostazioni**  
  ```powershell
  reagentc.exe /setrecoverysettings /path C:\QMR\QMR.xml
  ```
- **Rimuovi le impostazioni**  
  ```powershell
  reagentc.exe /clearrecoverysettings
  ```
- **Verifica le impostazioni**  
  ```powershell
  reagentc.exe /getrecoverysettings
  ```

---

## 6. Configurazione predefinita

- **Windows Home**:  
  - Cloud Remediation = abilitato  
  - Auto Remediation = disabilitato

- **Windows Pro & Enterprise**:  
  - Cloud Remediation = disabilitato  
  - Auto Remediation = disabilitato

Le organizzazioni possono modificare queste opzioni in base alle proprie esigenze.

---

## 7. Test Mode

QMR offre una **modalità di test** per simulare il processo di recovery senza causare un crash reale. 
Utile per validare le configurazioni prima del deployment in ambiente di produzione.

---

## 8. Riferimenti

Per maggiori dettagli, consultare la documentazione ufficiale Microsoft:  
https://learn.microsoft.com/en-us/windows/configuration/quick-machine-recovery/?tabs=cmd
