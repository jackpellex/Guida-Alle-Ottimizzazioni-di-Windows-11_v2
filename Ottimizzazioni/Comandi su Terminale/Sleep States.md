
# Guida agli Sleep States (Stati di Sospensione) nei Sistemi Windows

I computer moderni dispongono di diverse modalità di risparmio energetico chiamate "Sleep States" (Stati di sospensione), che determinano il comportamento del sistema quando va in standby. Ecco una panoramica dei principali stati e di come configurare la modalità più efficiente per il tuo PC.

---

## Stati di Sospensione Disponibili

- **S0 (Low Power Idle)**:
  - È lo stato più recente, progettato per mantenere una connessione costante a internet anche durante la sospensione.
  - Ideale per dispositivi che richiedono aggiornamenti in tempo reale o notifiche, come tablet e ultrabook.
  - Potrebbe consumare molta batteria se non gestito correttamente.

- **S1 (Standby leggero)**:
  - CPU e RAM rimangono attive ma funzionano a una frequenza ridotta.
  - Consumo energetico basso, ma non significativamente diverso dallo stato normale.

- **S2 (Standby avanzato)**:
  - La CPU viene completamente spenta, mentre la RAM rimane alimentata per mantenere i dati.
  - Raro nei dispositivi moderni.

- **S3 (Standby tradizionale)**:
  - La CPU e la maggior parte dei componenti hardware vengono disattivati, lasciando attiva solo la RAM per mantenere i dati in memoria.
  - Consuma pochissima energia ed è ottimo per i laptop.
  - Considerato il miglior compromesso tra risparmio energetico e tempi di riattivazione.

- **S4 (Ibernazione)**:
  - I dati della RAM vengono salvati su disco rigido o SSD, e il sistema viene completamente spento.
  - Consumo energetico nullo ma tempi di riavvio più lenti rispetto a S3.

- **S5 (Spento)**:
  - Il computer è completamente spento. Non c'è consumo energetico, ma il sistema non conserva alcun dato per il riavvio.

---

## Come Verificare gli Stati Supportati dal Sistema

1. **Aprire il Prompt dei Comandi come Amministratore**:
   Premi `Win + R`, digita `cmd`, quindi premi `Ctrl + Shift + Invio` per aprire il prompt in modalità amministratore.

2. **Eseguire il comando per verificare gli stati supportati**:
   ```bash
   powercfg /a
   ```
   Questo comando elencherà tutti gli stati di sospensione disponibili per il tuo PC.

3. **Analizzare i risultati**:
   - Se trovi "Il firmware del sistema non supporta lo stato di standby (S3)", significa che il tuo hardware non supporta questa modalità.

---

## Come Abilitare S3 (se disponibile)

1. **Accedere al BIOS**:
   - Riavvia il PC e premi ripetutamente uno dei seguenti tasti (dipende dal produttore):
     `F2`, `F10`, `F11`, `F12`, o `DEL`.

2. **Cercare le impostazioni di sospensione**:
   - Naviga nelle opzioni come *Power Management*, *Sleep State*, o simili.
   - Abilita la modalità **S3** (Standby).

3. **Salvare le modifiche**:
   - Salva ed esci dal BIOS. Il sistema si riavvierà con le nuove impostazioni applicate.

---

## Cosa Fare se S3 Non È Disponibile

Se il tuo PC non supporta S3, puoi utilizzare l'ibernazione come alternativa.

### Come Abilitare l'Ibernazione (se disattivata)

1. **Aprire l'Editor del Registro di Sistema**:
   - Premi `Win + R`, digita `regedit`, e premi `Invio`.

2. **Navigare nel seguente percorso**:
   ```plaintext
   Computer\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Power
   ```

3. **Modificare i seguenti valori**:
   - `HibernateEnabled`: Imposta il valore su `1`.
   - `HibernateEnabledDefault`: Imposta il valore su `1`.

4. **Controllare anche**:
   ```plaintext
   Computer\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Power\ForceHibernateDisabled
   ```
   - Modifica il valore `GuardedHost` su `0`.

5. **Riavviare il PC**:
   - Dopo le modifiche, riavvia per garantire che l'ibernazione sia attivata.

---

## Consigli Finali

- Se possibile, utilizza S3 per ottenere il miglior risparmio energetico con un rapido riavvio.
- Se S3 non è disponibile, abilita e utilizza l'ibernazione per garantire che il sistema sia completamente inattivo quando non in uso.
- Tieni sempre d'occhio il consumo della batteria e le impostazioni di rete se utilizzi S0 (Low Power Idle).
