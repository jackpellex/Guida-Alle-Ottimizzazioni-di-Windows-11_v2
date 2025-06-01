# Gestione della Memoria con la Compresssione

Se desideri aumentare la capacità della RAM, puoi attivare la compressione della memoria. 
Questo processo consente di immagazzinare più dati nella RAM, ma a discapito dell'uso della CPU, che sarà più impegnata 
nella compressione e decompressione dei dati.

## Considerazioni

- **Più RAM disponibile:** Aumenta la capacità della RAM, ma la CPU sarà più impegnata nel gestire la compressione.
- **Più CPU libera:** La RAM immagazzinerà la sua dimensione originale senza compressione, ma la CPU avrà meno lavoro da fare.

## Come attivare la compressione della memoria

1. Apri un terminale di **PowerShell** in modalità amministratore.
2. Digita il seguente comando per **attivare** la compressione della memoria:
   ```powershell
   Enable-MMAgent -mc
   ```

## Come disattivare la compressione della memoria

1. Apri un terminale di **PowerShell** in modalità amministratore.
2. Digita il seguente comando per **disattivare** la compressione della memoria:
   ```powershell
   Disable-MMAgent -mc
   ```

Scegli se attivare o disattivare la compressione in base alle tue esigenze di performance tra RAM e CPU.
