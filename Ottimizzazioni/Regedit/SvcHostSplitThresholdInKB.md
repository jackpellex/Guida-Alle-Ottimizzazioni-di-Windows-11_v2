# Ottimizzazione della Memoria di Sistema tramite il Registro di Sistema

## Editor del Registro di sistema

Per ottimizzare l'uso della memoria del sistema, è possibile regolare il valore della chiave `SvcHostSplitThresholdInKB`. 
Questo permette di riservare una quantità adeguata di memoria ai processi di sistema, 
migliorando la gestione della RAM e contribuendo a un sistema più reattivo e stabile.

### Passaggi per la modifica
1. Aprire l'**Editor del Registro di sistema**.  
   Premi `Win + R`, digita `regedit` e premi **Invio**.
2. Navigare fino alla chiave seguente:  
   `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control`
3. Cercare la voce **SvcHostSplitThresholdInKB**.
4. Modificare il valore predefinito (380000 KB) in base alla RAM installata sul sistema.

### Valori consigliati in base alla RAM installata
| **RAM Installata** | **Valore (KB)** |
|---------------------|-----------------|
| Predefinito         | 380000          |
| 4 GB                | 400000          |
| 6 GB                | 600000          |
| 8 GB                | 800000          |
| 12 GB               | c00000          |
| 16 GB               | 1000000         |
| 24 GB               | 1800000         |
| 32 GB               | 2000000         |
| 64 GB               | 4000000         |

---

## Benefici della Modifica
- **Ottimizzazione delle risorse**: Evita che i processi di sistema consumino troppa memoria, prevenendo rallentamenti.
- **Migliore stabilità**: Impedisce che un uso eccessivo della RAM causi crash o blocchi del sistema.
- **Prestazioni migliorate**: Aumenta la velocità e la reattività complessiva del sistema, rendendolo più fluido e veloce.

---

## Considerazioni
- **Sacrificare una piccola quantità di RAM** per i processi di sistema migliora la stabilità e le prestazioni complessive.
- Valori troppo bassi potrebbero liberare più memoria per altre applicazioni, ma rischiano di rallentare il sistema a lungo termine.
- Esempio: Con 32 GB di RAM, impostare 2000000 KB (circa 2 GB) garantisce che i processi di sistema 
  possano operare senza compromettere le prestazioni generali del sistema.

---

## Conclusione
Modificare il valore di `SvcHostSplitThresholdInKB` in base alla quantità di RAM installata è una tecnica di ottimizzazione utile 
per bilanciare meglio la memoria tra il sistema e le applicazioni. 
Questo porta a prestazioni più elevate e a una gestione più efficiente delle risorse di sistema.
