
# HPET (High Precision Event Timer)

## Cos'è HPET?
HPET, acronimo di *High Precision Event Timer*, è un timer hardware progettato per fornire una sincronizzazione precisa tra il software e l'hardware del sistema. 
Questo timer è spesso utilizzato in applicazioni che richiedono una temporizzazione accurata, come il gaming, le simulazioni, sincronizzazione, o altre attività di alta precisione.

## È necessario HPET su un PC portatile?
L'utilità di HPET varia a seconda del tipo di utilizzo del sistema:
- **Sistemi generici o portatili:** HPET può essere disattivato per risparmiare energia, specialmente sui laptop. 
   Questo è utile per prolungare la durata della batteria quando non è necessaria una sincronizzazione ad alta precisione.
- **Applicazioni specifiche:** Se utilizzi applicazioni che richiedono una temporizzazione estremamente accurata, come strumenti di benchmarking, 
   gaming di livello competitivo o software specifici per simulazioni, è preferibile mantenere HPET abilitato.

## Come verificare se HPET è attivo o disattivarlo?

### Metodo 1: Utilizzare il Prompt dei comandi
### Controllare lo stato di HPET
1. Apri **Prompt dei comandi** o **PowerShell** in modalità amministratore.
2. Digita il comando:
   ```bash
   bcdedit /enum
   ```
   Cerca una voce chiamata `useplatformclock`. Se è presente e impostata su `Yes`, HPET è abilitato.

### Disattivare HPET
1. Apri **Prompt dei comandi** o **PowerShell** in modalità amministratore.
2. Digita il seguente comando per disabilitare HPET:
   ```bash
   bcdedit /deletevalue useplatformclock
   ```
3. Riavvia il sistema per applicare le modifiche.

### Abilitare HPET
1. Apri **Prompt dei comandi** o **PowerShell** in modalità amministratore.
2. Digita il comando:
   ```bash
   bcdedit /set useplatformclock yes
   ```
3. Riavvia il sistema per applicare le modifiche.

### Metodo 2: Utilizzare il BIOS/UEFI
La maggior parte delle modifiche a HPET devono essere fatte tramite il BIOS/UEFI del sistema. Ecco come fare:
1. Riavvia il computer.
2. Accedi al BIOS premendo uno dei tasti come F2, F12, o DEL (dipende dalla marca e modello del tuo PC).
3. Naviga tra le opzioni avanzate fino a trovare la voce relativa a HPET. Può essere sotto "Advanced", "Power Management", o "CPU Configuration".
4. Disabilita l'opzione HPET (se disponibile).
5. Salva e esci dal BIOS.

### Metodo 3: Utilizzare il "Gestione Dispositivi" di Windows
Se HPET non è disponibile nel BIOS o non riesci a trovarlo, puoi provare a disabilitarlo attraverso "Gestione Dispositivi":
1. Premi `Win + X` e seleziona **Gestione Dispositivi**.
2. Nella finestra **Gestione Dispositivi**, espandi la sezione **Dispositivi di sistema**.
3. Cerca la voce **High Precision Event Timer**.
4. Fai clic con il tasto destro su di essa e seleziona **Disabilita dispositivo** per disattivarlo.


## Considerazioni finali
- **Disattivare HPET** può ridurre il consumo energetico e migliorare le prestazioni generali su sistemi che non ne necessitano.
- **Abilitare HPET** è consigliato solo se hai applicazioni specifiche che richiedono un'alta precisione temporale.
- Prima di apportare modifiche, è sempre consigliato creare un punto di ripristino per poter tornare indietro in caso di problemi.

### Nota
Alcuni sistemi potrebbero richiedere l'accesso al BIOS/UEFI per disattivare o abilitare HPET. 
Consulta il manuale del tuo dispositivo per maggiori dettagli su come accedere e modificare le impostazioni nel BIOS.
