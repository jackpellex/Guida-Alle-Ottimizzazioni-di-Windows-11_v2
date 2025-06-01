# Diagnostica della Memoria di Windows

La **Diagnostica della Memoria di Windows** è uno strumento integrato nel sistema operativo che consente di identificare e
risolvere problemi legati alla RAM (memoria ad accesso casuale). È particolarmente utile in caso di crash del sistema, 
schermate blu (BSOD) o instabilità del sistema.

## Procedura

1. **Avviare la Diagnostica della Memoria**:
   - Premi la combinazione di tasti `Windows + S` per aprire la barra di ricerca.
   - Digita **Diagnostica memoria di Windows** e seleziona l’applicazione corrispondente.

2. **Scelta delle Opzioni di Diagnostica**:
   - Verrà visualizzato un messaggio con due opzioni:
     - **Riavvia ora e individua i problemi (scelta consigliata)**: Il sistema verrà riavviato immediatamente per eseguire i test.
     - **Individua i problemi al successivo avvio del computer**: I test verranno eseguiti alla prossima accensione del sistema.

3. **Esecuzione del Test**:
   - Durante il riavvio, il sistema entrerà in una schermata blu con il **test di memoria** in corso.
   - Verranno eseguite due passate standard per individuare eventuali problemi. Puoi monitorare l’avanzamento e lo stato dei test sulla schermata.

4. **Analisi dei Risultati**:
   - Dopo il completamento del test, il sistema si riavvierà automaticamente.
   - Una volta effettuato l’accesso a Windows, i risultati del test saranno visibili in una notifica. Se non appare, 
       puoi controllarli nel **Visualizzatore eventi**:
     - Premi `Windows + R`, digita `eventvwr` e premi `Invio`.
     - Naviga fino a **Registri di Windows > Sistema**.
     - Cerca un evento con origine **MemoryDiagnostics-Results**.

## Opzioni Avanzate

Durante il test, puoi accedere alle **opzioni avanzate** premendo il tasto `F1`:
- **Mix del test**: Puoi scegliere tra test Base, Standard o Avanzato per una maggiore accuratezza.
- **Cache**: Puoi decidere se disabilitare o meno la cache della CPU durante il test.
- **Numero di passate**: Puoi aumentare il numero di passate per test più approfonditi.

## Quando Utilizzarlo?

- Sospetti problemi con la RAM (ad esempio, crash, BSOD o errori casuali).
- Riscontri rallentamenti significativi nelle prestazioni del sistema.
- Vuoi verificare l’integrità della memoria dopo un aggiornamento hardware.

## Note Importanti

- **Tempo del Test**: Un test approfondito può richiedere tempo, in base alla quantità di RAM installata.
- **Backup dei Dati**: Anche se il test non comporta rischi per i dati, è buona pratica eseguire un backup 
    prima di avviare diagnostiche di sistema.
- **Hardware Difettoso**: Se vengono rilevati problemi, potrebbe essere necessario sostituire uno o più moduli di RAM.

Questo strumento è un metodo affidabile per identificare potenziali problemi di memoria che possono 
influire negativamente sulle prestazioni del tuo sistema.
