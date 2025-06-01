Ecco il testo completamente tradotto in italiano, con i comandi tra virgolette mantenuti invariati:

### Gestire le Impostazioni di Alimentazione con PowerCFG

**PowerCFG** è uno strumento integrato in Windows che consente di configurare e visualizzare 
le impostazioni di alimentazione del sistema, diagnosticare problemi energetici e ottimizzare le prestazioni della batteria.

---

#### **Cos'è PowerCFG?**
PowerCFG è un'utilità da riga di comando utilizzata per gestire le impostazioni di alimentazione in Windows. 
Può configurare il comportamento del sistema relativo al consumo energetico, come l'ibernazione, gli stati di sospensione e i report sull'efficienza energetica.

---

#### **Panoramica dei Comandi di PowerCFG**

1. **`/?`** - Visualizza le informazioni sui parametri della riga di comando.
   - **Quando usarlo**: Quando hai bisogno di vedere l'elenco completo dei parametri disponibili e del loro utilizzo.
   - **Come usarlo**:  
     ```cmd
     powercfg /?
     ```

2. **`/list`, `/L`** - Elenca tutti gli schemi di alimentazione.
   - **Quando usarlo**: Per visualizzare tutti i piani di alimentazione disponibili nel sistema.
   - **Come usarlo**:  
     ```cmd
     powercfg /list
     ```

3. **`/query`, `/Q`** - Interroga il contenuto di uno schema di alimentazione.
   - **Quando usarlo**: Per visualizzare le impostazioni specifiche dello schema di alimentazione attivo.
   - **Come usarlo**:  
     ```cmd
     powercfg /query
     ```

4. **`/change`, `/X`** - Modifica una impostazione nel piano di alimentazione corrente.
   - **Quando usarlo**: Quando devi regolare una specifica impostazione di alimentazione come la sospensione, il timeout del display, ecc.
   - **Come usarlo**:  
     ```cmd
     powercfg /change setting_name value
     ```

5. **`/changename`** - Cambia il nome e la descrizione di uno schema di alimentazione.
   - **Quando usarlo**: Per rinominare un piano di alimentazione per una migliore organizzazione.
   - **Come usarlo**:  
     ```cmd
     powercfg /changename old_name new_name
     ```

6. **`/duplicatescheme`** - Duplica uno schema di alimentazione.
   - **Quando usarlo**: Quando hai bisogno di una copia di uno schema di alimentazione da modificare senza influenzare l'originale.
   - **Come usarlo**:  
     ```cmd
     powercfg /duplicatescheme scheme_guid
     ```

7. **`/delete`, `/D`** - Elimina uno schema di alimentazione.
   - **Quando usarlo**: Quando non hai più bisogno di uno schema di alimentazione.
   - **Come usarlo**:  
     ```cmd
     powercfg /delete scheme_guid
     ```

8. **`/deletesetting`** - Elimina una impostazione di risparmio energetico.
   - **Quando usarlo**: Per rimuovere una specifica impostazione di alimentazione.
   - **Come usarlo**:  
     ```cmd
     powercfg /deletesetting setting_guid
     ```

9. **`/setactive`, `/S`** - Imposta uno schema di alimentazione come attivo.
   - **Quando usarlo**: Quando desideri passare a un piano di alimentazione specifico.
   - **Come usarlo**:  
     ```cmd
     powercfg /setactive scheme_guid
     ```

10. **`/getactivescheme`** - Recupera lo schema di alimentazione attivo.
    - **Quando usarlo**: Per verificare quale piano di alimentazione è attualmente in uso.
    - **Come usarlo**:  
      ```cmd
      powercfg /getactivescheme
      ```

11. **`/setacvalueindex`** - Imposta il valore associato a una impostazione di alimentazione quando il sistema è collegato alla corrente.
    - **Quando usarlo**: Per configurare le impostazioni di alimentazione specifiche quando il sistema è collegato a una presa elettrica.
    - **Come usarlo**:  
      ```cmd
      powercfg /setacvalueindex scheme_guid setting_guid value
      ```

12. **`/setdcvalueindex`** - Imposta il valore associato a una impostazione di alimentazione quando il sistema è alimentato a batteria.
    - **Quando usarlo**: Per configurare le impostazioni di alimentazione quando il sistema è alimentato a batteria.
    - **Come usarlo**:  
      ```cmd
      powercfg /setdcvalueindex scheme_guid setting_guid value
      ```

13. **`/import`** - Importa tutte le impostazioni di alimentazione da un file.
    - **Quando usarlo**: Quando desideri applicare le impostazioni di alimentazione da un file di configurazione.
    - **Come usarlo**:  
      ```cmd
      powercfg /import file_path
      ```

14. **`/export`** - Esporta uno schema di alimentazione in un file.
    - **Quando usarlo**: Quando desideri salvare lo schema di alimentazione corrente per un uso futuro o per il backup.
    - **Come usarlo**:  
      ```cmd
      powercfg /export file_path scheme_guid
      ```

15. **`/Alias`** - Elenca tutti gli alias e i loro GUID associati.
    - **Quando usarlo**: Per visualizzare gli alias degli schemi di alimentazione e i loro GUID.
    - **Come usarlo**:  
      ```cmd
      powercfg /Alias
      ```

16. **`/getsecuritydescriptor`** - Recupera un descrittore di sicurezza associato a una impostazione di alimentazione, schema di alimentazione o azione.
    - **Quando usarlo**: Per verificare le impostazioni di sicurezza per le configurazioni di alimentazione.
    - **Come usarlo**:  
      ```cmd
      powercfg /getsecuritydescriptor scheme_guid
      ```

17. **`/setsecuritydescriptor`** - Imposta un descrittore di sicurezza per una impostazione di alimentazione, schema di alimentazione o azione.
    - **Quando usarlo**: Quando devi modificare i permessi di sicurezza per una impostazione di alimentazione.
    - **Come usarlo**:  
      ```cmd
      powercfg /setsecuritydescriptor scheme_guid new_descriptor
      ```

18. **`/hibernate`, `/H`** - Abilita o disabilita la funzione di ibernazione.
    - **Quando usarlo**: Per attivare o disattivare la modalità di ibernazione del sistema.
    - **Come usarlo**:  
      ```cmd
      powercfg /hibernate on
      ```

19. **`/availablesleepstates`, `/A`** - Elenca gli stati di sospensione disponibili nel sistema.
    - **Quando usarlo**: Per verificare quali stati di sospensione sono supportati dal sistema.
    - **Come usarlo**:  
      ```cmd
      powercfg /availablesleepstates
      ```

20. **`/devicequery`** - Restituisce un elenco di dispositivi che soddisfano i criteri specificati.
    - **Quando usarlo**: Per trovare dispositivi che supportano comportamenti di alimentazione specifici.
    - **Come usarlo**:  
      ```cmd
      powercfg /devicequery criteria
      ```

21. **`/deviceenablewake`** - Consente a un dispositivo di risvegliare il sistema dalla sospensione.
    - **Quando usarlo**: Per abilitare la funzione di risveglio per un dispositivo.
    - **Come usarlo**:  
      ```cmd
      powercfg /deviceenablewake device_name
      ```

22. **`/devicedisablewake`** - Disabilita un dispositivo dal risvegliare il sistema dalla sospensione.
    - **Quando usarlo**: Per impedire a un dispositivo di risvegliare il sistema.
    - **Come usarlo**:  
      ```cmd
      powercfg /devicedisablewake device_name
      ```

23. **`/lastwake`** - Riporta informazioni su cosa ha risvegliato il sistema dall'ultima transizione di sospensione.
    - **Quando usarlo**: Per verificare cosa ha causato il risveglio del sistema dalla sospensione.
    - **Come usarlo**:  
      ```cmd
      powercfg /lastwake
      ```

24. **`/waketimers`** - Elenca i timer di risveglio attivi.
    - **Quando usarlo**: Per visualizzare eventuali eventi pianificati che potrebbero risvegliare il sistema.
    - **Come usarlo**:  
      ```cmd
      powercfg /waketimers
      ```

25. **`/requests`** - Elenca tutte le richieste di alimentazione attive fatte dalle applicazioni o dai driver.
    - **Quando usarlo**: Per vedere quali processi stanno richiedendo modifiche all'alimentazione.
    - **Come usarlo**:  
      ```cmd
      powercfg /requests
      ```

26. **`/requestsoverride`** - Imposta una sovrascrittura di una richiesta di alimentazione per un processo, servizio o driver specifico.
    - **Quando usarlo**: Per modificare o sovrascrivere le richieste di alimentazione da applicazioni o servizi specifici.
    - **Come usarlo**:  
      ```cmd
      powercfg /requestsoverride process_name
      ```

27. **`/energy`** - Analizza il sistema per problemi comuni di efficienza energetica e durata della batteria.
    - **Quando usarlo**: Quando devi diagnosticare problemi energetici nel sistema.
    - **Come usarlo**:  
      ```cmd
      powercfg /energy
      ```

28. **`/batteryreport`** - Genera un report sull'uso della batteria.
    - **Quando usarlo**: Per ottenere un report dettagliato sull'uso della batteria nel tempo.
    - **Come usarlo**:  
      ```cmd
      powercfg /batteryreport
      ```

29. **`/sleepstudy`** - Genera un report sulle transizioni di sospensione del sistema per la diagnostica.
    - **Quando usarlo**: Per analizzare come il sistema gestisce le transizioni di sospensione.
    - **Come usarlo**:  
      ```cmd
      powercfg /sleepstudy
      ```

30. **`/srumutil`** - Scarica i dati di stima sull'uso dell'energia dal Monitor delle Risorse di Sistema (SRUM).
    - **Quando usarlo**: Per analizzare l'uso delle risorse del sistema e il suo impatto sul consumo energetico.
    - **Come usarlo**:  
      ```cmd
      powercfg /srumutil
      ```

31. **`/systemsleepdiagnostics`** - Genera un report diagnostico sulle transizioni di sospensione del sistema.
    - **Quando usarlo**: Per ottenere una visione dettagliata delle transizioni di sospensione e dei problemi potenziali.
    - **Come usarlo**:  
      ```cmd
      powercfg /systemsleepdiagnostics
      ```

32. **`/systempowerreport`** - Genera un report diagnostico sulle transizioni di alimentazione del sistema.
    - **Quando usarlo**: Per visualizzare il consumo di energia e le transizioni del sistema.
    - **Come usarlo**:  
      ```cmd
      powercfg /systempowerreport
      ```

---

## Casi d'Uso Comuni
Ottimizzazione dell'Uso Energetico  
Usa **`/energy`** per analizzare il sistema e individuare inefficienze energetiche, o **`/batteryreport`** per monitorare la salute e l'utilizzo della batteria.

# Gestire le Impostazioni di Sospensione e Ibernazione  
Abilita o disabilita l'ibernazione e gestisci le impostazioni di sospensione utilizzando comandi come **`/hibernate`** e **`/availablesleepstates`**.

# Risoluzione dei Problemi di Alimentazione  
Genera report diagnostici con **`/systempowerreport`** o **`/systemsleepdiagnostics`** per identificare le transizioni di alimentazione e 
i problemi relativi al comportamento del sistema durante la sospensione.

## Note Importanti
Considerazioni sulla Sicurezza  
Gli schemi di alimentazione e le impostazioni possono essere associati a descrittori di sicurezza. Fai attenzione quando modifichi 
queste impostazioni in un ambiente multi-utente.

# Impatto sulla Durata della Batteria  
Alcune impostazioni di alimentazione, come l'abilitazione degli stati di sospensione e l'ottimizzazione delle impostazioni del display, 
possono estendere significativamente la durata della batteria, specialmente sui laptop.

# Generazione di Report  
I report generati con comandi come **`/energy`**, **`/batteryreport`** e **`/sleepstudy`** potrebbero richiedere del tempo a seconda 
della configurazione del sistema e delle sue dimensioni.

#### **Quando usare PowerCFG?**
- **Personalizzare le impostazioni di alimentazione** per soddisfare esigenze specifiche (ad esempio, prestazioni vs. durata della batteria).
- **Diagnosticare problemi di alimentazione** relativi all'efficienza energetica e al consumo della batteria.
- **Gestire il comportamento di sospensione e ibernazione** per ottimizzare i tempi di risveglio del sistema.

---

#### **Vantaggi dell'uso di PowerCFG**
- Permette una personalizzazione profonda delle impostazioni di alimentazione in base alle preferenze di utilizzo.
- Aiuta a identificare e risolvere problemi relativi all'alimentazione per ottimizzare le prestazioni del sistema e la durata della batteria.
- Fornisce report dettagliati per monitorare e risolvere problemi sul consumo energetico dei vari componenti del sistema.