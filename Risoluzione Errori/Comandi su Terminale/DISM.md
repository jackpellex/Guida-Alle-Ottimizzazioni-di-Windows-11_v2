
# Utilizzo di DISM (Deployment Image Servicing and Management)

DISM è uno strumento integrato in Windows per la manutenzione e la gestione delle immagini di sistema. 
Può essere utilizzato per riparare file di sistema corrotti o per gestire le immagini di installazione di Windows.

---

## Quando utilizzare DISM
- Per risolvere errori di sistema non risolti da **SFC /SCANNOW**.
- Per riparare l'immagine di sistema corrotta.
- Per preparare immagini di Windows (es. file WIM o VHD).

---

## Comandi principali di DISM

### 1. Verifica dello stato dell'immagine
Prima di riparare, verifica lo stato dell'immagine di sistema con il comando:

```cmd
DISM /Online /Cleanup-Image /CheckHealth
```

- **Descrizione**: Controlla se l'immagine di sistema è danneggiata e se può essere riparata.

---

### 2. Scansione per individuare problemi
Per una scansione approfondita dell'immagine, usa:

```cmd
DISM /Online /Cleanup-Image /ScanHealth
```

- **Descrizione**: Analizza l'immagine per trovare eventuali danni o problemi.

---

### 3. Riparazione dell'immagine
Per riparare automaticamente i problemi trovati, esegui:

```cmd
DISM /Online /Cleanup-Image /RestoreHealth
```

- **Descrizione**: Ripristina l'immagine utilizzando file di riparazione scaricati dai server di Windows Update.

---

## Riparazione avanzata con sorgente specifica
Se non hai accesso a Internet o desideri specificare un file sorgente locale, utilizza:

```cmd
DISM /Online /Cleanup-Image /RestoreHealth /Source:X:\Percorso\della\Sorgente /LimitAccess
```

- **`/Source`**: Specifica la posizione dei file di sistema corretti.
- **`/LimitAccess`**: Evita di connettersi a Windows Update.

---

## Riparare file di sistema utilizzando SFC dopo DISM
Dopo aver utilizzato DISM per riparare l'immagine di sistema, esegui il comando:

```cmd
sfc /scannow
```

Questo garantisce che i file di sistema siano stati completamente ripristinati.

---

## Note importanti
1. **Permessi**: È necessario eseguire DISM in un terminale con privilegi di amministratore.
2. **Online vs Offline**:
   - **`/Online`**: Agisce sul sistema operativo attualmente in uso.
   - **Offline**: Per agire su immagini di sistema non in esecuzione.
3. **Risorse aggiuntive**: Puoi utilizzare un'unità di installazione di Windows per fornire i file di riparazione.

---

## Esempio pratico
Riparazione completa con connessione Internet:

```cmd
DISM /Online /Cleanup-Image /RestoreHealth
sfc /scannow
```

Riparazione utilizzando una sorgente locale:

```cmd
DISM /Online /Cleanup-Image /RestoreHealth /Source:D:\Sources /LimitAccess
sfc /scannow
```

---

Utilizza DISM per garantire che il tuo sistema operativo funzioni senza problemi e in modo affidabile!
