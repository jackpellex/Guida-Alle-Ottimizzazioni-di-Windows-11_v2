# Guida educativa per disattivare/riattivare HyperThreading/SMT tramite BIOS

In generale, **è sconsigliato disattivare questa funzione** per garantire una migliore gestione del multitasking e una maggiore reattività del sistema. 
La modifica può essere utile solo in casi particolari, ad esempio per tentare di aumentare gli FPS in alcuni giochi, 
se si sospetta che HyperThreading stia interferendo con le prestazioni.

## 1. Accesso al BIOS/UEFI

- **Quando accedere:**  
  Durante l’avvio del computer (prima che il sistema operativo si carichi) bisogna premere un tasto specifico. 
  I tasti più comuni sono **F2**, **Canc (Del)**, o **Esc**, a seconda del produttore.

- **Suggerimento:**  
  Se non sei sicuro di quale tasto usare, controlla il manuale del tuo computer o cerca online "come accedere al BIOS" seguito dal modello del tuo PC o scheda madre.

## 2. Navigare nelle Impostazioni Relative a HyperThreading/SMT

### Per CPU Intel:
- **Ricerca dell'opzione:**  
  Una volta nel BIOS, cerca una sezione come **“Advanced”** o **“CPU Configuration”**.
- **Opzione specifica:**  
  Dovresti trovare un’impostazione denominata **“Intel HyperThreading Technology”**.
- **Cosa fare:**  
  - **Per disattivare:** Seleziona l’opzione e imposta su "Disabled".  
  - **Per riattivare:** Imposta nuovamente su "Enabled".

### Per CPU AMD:
- **Ricerca dell'opzione:**  
  Le CPU AMD solitamente utilizzano la dicitura **“Simultaneous Multithreading (SMT)”**. Cerca la sezione **“Advanced”** o simile all’interno delle impostazioni del processore.
- **Cosa fare:**  
  - **Per disattivare:** Imposta l’opzione SMT su "Disabled".  
  - **Per riattivare:** Seleziona "Enabled".

> **Nota:** Le voci e l’organizzazione del BIOS possono variare a seconda del produttore della scheda madre. 
Se non riesci a trovare l’opzione, consulta il manuale della tua scheda madre o cerca online “disattivare HyperThreading [nome modello]”.

## 3. Salvare le Modifiche e Riavviare

- Dopo aver effettuato le modifiche, cerca l’opzione per **“Save and Exit”** (solitamente premendo **F10**) e conferma le modifiche.
- Il computer si riavvierà applicando le nuove impostazioni.

## 4. Verifica dello Stato di HyperThreading/SMT

### Su Windows:
- **Task Manager:**  
  Premi **Ctrl+Shift+Esc** per aprire il Task Manager e vai nella scheda **“Prestazioni”**.  
  Se vedi che il numero dei “Logical Processors” è il doppio dei “Physical Cores”, significa che HyperThreading/SMT è attivo.
- **Software di terze parti:**  
  Programmi come **CPU-Z** o **HWiNFO** possono mostrarti dettagli approfonditi sulla configurazione del processore.

### Su Linux:
- **Terminale:**  
  Apri il terminale e digita il comando `lscpu` per visualizzare le informazioni relative al numero di core e thread.
- **File di sistema:**  
  Puoi anche controllare il file `/proc/cpuinfo` per verificare quante “processor” sono elencate.

## 5. Software Affidabili per il Monitoraggio

Oltre al Task Manager e ai comandi su Linux, ecco alcuni software affidabili:
- **CPU-Z:** Offre informazioni dettagliate sulla CPU, inclusi core e thread.
- **HWiNFO:** Fornisce una panoramica completa dell’hardware installato, utile per monitorare lo stato in tempo reale.

## Conclusioni e Avvertenze

- **Prestazioni:**  
  Disattivare HyperThreading o SMT può ridurre la capacità del processore di gestire più attività contemporaneamente, 
  incidendo negativamente sul multitasking e sulla reattività generale del sistema.
- **Utilizzo Specifico:**  
  Alcuni utenti disattivano questa funzione per cercare di aumentare gli FPS in specifici giochi o applicazioni, 
  ma questa soluzione può risultare controproducente in molti scenari.
- **Consiglio:**  
  Procedi con questa modifica solo se hai ben chiari i motivi e dopo aver eseguito un backup o verificato che la modifica possa essere facilmente invertita 
  seguendo i passaggi sopra descritti.

---

Questa guida è stata pensata per essere semplice e intuitiva. Se incontri difficoltà o dubbi, rivolgiti a forum o manuali specifici per il modello della tua scheda madre.
