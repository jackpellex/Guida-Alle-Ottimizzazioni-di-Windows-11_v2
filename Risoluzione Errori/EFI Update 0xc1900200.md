# **Guida alla Risoluzione degli Errori di Aggiornamento Windows 11 24H2: EFI Insufficiente (Codici 0xc1900200 / 0xc1900201)**

Questo documento fornisce una guida tecnica approfondita per affrontare gli errori di installazione di aggiornamenti massivi (Feature Updates) di Windows 11, in particolare la versione 24H2, identificati dai codici 0xc1900200 e 0xc1900201. Tali errori indicano una carenza critica di spazio disponibile nella Partizione di Sistema EFI (ESP).

---

## **I. Introduzione: La Sfida dell'Aggiornamento 24H2 e l'ESP Insufficiente**

Gli errori 0xc1900200 e 0xc1900201 si manifestano tipicamente quando il sistema operativo tenta di eseguire un aggiornamento di funzionalità significativo, come l'aggiornamento alla versione 24H2 di Windows 11, ma non riesce a completare la fase di preparazione o staging dei file nella partizione di avvio.[1]

### **1.1. Sintomi e Correlazioni degli Errori**

Quando l'aggiornamento fallisce, il sistema restituisce uno dei codici sopra citati. Questi sono sintomi moderni di un problema storico già noto in Windows 10 e nelle versioni precedenti, spesso identificato con gli errori 0xc1900104 o 0x800f0922, dove il messaggio diagnostico indicava: "Non è stato possibile aggiornare la partizione riservata del sistema" (System Reserved Partition, SRP).[2]

La SRP, nei sistemi più datati basati su MBR, o la sua equivalente moderna, la Partizione di Sistema EFI (ESP) nei sistemi GPT/UEFI, ha il compito cruciale di ospitare i file di avvio essenziali che consentono al firmware UEFI di caricare il sistema operativo Windows.3 La carenza di spazio in questa partizione è la causa radice del blocco dell'aggiornamento.

### **1.2. Meccanismo del Fallimento: Il Ruolo Critico dell'ESP**

La Partizione di Sistema EFI (ESP) è una partizione specializzata, formattata in FAT32, che agisce come interfaccia tra il firmware UEFI del computer e il bootloader di Windows. Durante un Feature Update di Windows, il sistema operativo necessita di spazio libero all'interno dell'ESP per eseguire il *staging* (preparazione) dei nuovi file di avvio e per aggiornare l'archivio di configurazione di avvio (BCD).[4]

L'aggiornamento richiede una quantità minima di spazio libero, storicamente quantificata in circa 13–15 MB, per poter scrivere i file temporanei necessari al completamento dell'installazione.5 Se questo spazio non è disponibile, il processo si interrompe nella fase iniziale, restituendo l'errore.

Inoltre, il problema è aggravato dal fatto che l'ESP può essere riempita non solo da Windows, ma anche da file lasciati dagli aggiornamenti del firmware (BIOS/UEFI) rilasciati dai produttori di hardware (OEM) come Dell o HP.7 Questi file, se non puliti automaticamente, saturano ulteriormente la partizione.

### **1.3. Requisiti di Dimensione e Raccomandazioni Attuali**

Il problema della saturazione è sistemico e deriva da un conflitto tra gli standard minimi e le necessità operative moderne. Microsoft stabilisce che l'ESP sui dischi GPT deve avere una dimensione minima di 200 MB ed essere formattata in FAT32.[3]

Tuttavia, molti produttori di PC preinstallano sistemi con un ESP di soli 100 MB.6 Sebbene 100 MB potessero essere sufficienti al momento dell'installazione iniziale, essi si rivelano insufficienti per gestire i successivi aggiornamenti di Windows 11 e i file temporanei del firmware.[6]

Per garantire la stabilità futura e prevenire la ricorrenza di questi errori, gli esperti raccomandano di aumentare proattivamente la dimensione dell'ESP. La dimensione ideale consigliata è di almeno 256 MB, e preferibilmente **500 MB** o addirittura **1 GB**, per fornire un margine di sicurezza a lungo termine per tutti i futuri aggiornamenti del sistema operativo e del firmware.[7]

Tabella 1: Dimensioni Ottimali della Partizione di Sistema EFI (ESP)

| Parametro | Requisito Minimo (Microsoft GPT) | Raccomandazione Ottimale (Windows 11 24H2) | Motivazione |
| :---- | :---- | :---- | :---- |
| Dimensione Partizione | 200 MB | 500 MB – 1 GB | Garantire spazio sufficiente per staging di Windows e aggiornamenti firmware. |
| Formato File | FAT32 | FAT32 | Obbligatorio per il firmware UEFI. |
| Spazio Libero Richiesto | Circa 15 MB | Maggiore è il margine, meglio è | Quantità minima necessaria per il completamento del *feature update*. |

### **1.4. Preparazione Preliminare e Avvertenze CRITICHE**

Prima di intraprendere qualsiasi procedura di modifica delle partizioni di sistema, è indispensabile prendere le seguenti precauzioni:

1. **Backup Dati Completo:** La manipolazione delle partizioni di sistema, specialmente l'ESP, comporta un rischio elevato di rendere il sistema non avviabile (*no-boot*). È obbligatorio eseguire un backup completo dei dati essenziali.[4]  
2. **Sospensione di BitLocker:** Se il sistema utilizza la crittografia BitLocker, questa deve essere Sospesa (non disattivata) prima di qualsiasi operazione di ridimensionamento o ricreazione. La modifica della struttura di avvio while BitLocker è attivo causerà il blocco del sistema all'avvio.[9]  
3. **Verifica Tipo di Disco:** Questa guida si applica ai sistemi moderni (Windows 11\) che utilizzano il partizionamento **GPT** e il firmware **UEFI**.2 I sistemi MBR utilizzano un approccio leggermente diverso per la Partizione Riservata del Sistema (SRP).

---

## **II. Soluzione 1: Pulizia della Partizione EFI Esistente (Rischio Basso)**

Il metodo meno rischioso è tentare di liberare lo spazio minimo richiesto (13–15 MB) eliminando file obsoleti, come i font di avvio o le cartelle lingua non utilizzate, che possono saturare l'ESP.[2]

### **2.1. Come Accedere e Montare la Partizione EFI (ESP)**

Poiché l'ESP è nascosta per motivi di sicurezza e non ha una lettera di unità assegnata in Gestione Disco, è necessario montarla temporaneamente.

1. Aprire il Prompt dei Comandi (CMD) come Amministratore.  
2. Digitare il seguente comando per assegnare una lettera di unità temporanea (ad esempio, Y:) alla Partizione di Sistema:  
```   mountvol Y: /s  ```
   Questo comando rende la partizione accessibile.2

### **2.2. Esecuzione della Pulizia**

La saturazione dell'ESP è spesso dovuta a file di font residui lasciati dagli aggiornamenti.

3. Passare all'unità appena montata:  
```   Y:  ```
4. Navigare nella directory dei Font di Avvio di Windows:  
```   cd EFI\\Microsoft\\Boot\\Fonts  ```
5. Eliminare i file dei tipi di carattere non necessari (si noti che molti di questi sono file non essenziali per l'avvio di base):  
```   del \*.\*  ```
   Il sistema richiederà una conferma; premere Y e poi Invio per continuare.[2]  
6. *Passaggio Opzionale:* Se lo spazio è ancora insufficiente, si può tornare alla cartella Y:\\EFI\\Microsoft\\Boot\\ e rimuovere manualmente le sottocartelle relative alle lingue inutilizzate, se presenti.[5]  
7. Dopo aver liberato lo spazio desiderato, smontare la partizione:  
```   mountvol Y: /d  ```
8. Riprovare l'aggiornamento di Windows 11\. Se sono stati liberati almeno 15 MB, l'aggiornamento dovrebbe procedere.[5]

---

## **III. Soluzione 2: Ridimensionamento Non Distruttivo (Rischio Medio)**

Se la pulizia non libera spazio sufficiente, è necessario ingrandire l'ESP. Poiché gli strumenti nativi di Windows (Gestione Disco) non consentono di spostare le partizioni per creare spazio contiguo, questa operazione richiede software di terze parti.

### **3.1. Prerequisiti: Software di Terze Parti e Limitazioni**

Strumenti come MiniTool Partition Wizard, AOMEI Partition Assistant o EaseUS Partition Master sono necessari per eseguire operazioni di spostamento partizioni.10 Tali operazioni comportano un rischio aggiuntivo, poiché vengono eseguite al di fuori dell'ambiente operativo standard di Windows, quindi il rischio di corruzione dei dati in caso di interruzione (ad esempio, mancanza di corrente) aumenta.[4]

### **3.2. Scenario 1: Spazio Non Allocato Contiguo**

Questo è il caso più semplice: lo spazio non allocato si trova immediatamente a destra dell'ESP.

* **Procedura:** Utilizzare il software di terze parti, selezionare la Partizione di Sistema EFI e utilizzare l'opzione "Estendi" o "Ridimensiona/Sposta" per includere lo spazio non allocato adiacente.14 L'obiettivo è portare l'ESP a 500 MB o 1 GB.

### **3.3. Scenario 2: Spostamento di Partizioni Ostruttive**

Nella maggior parte dei casi, lo spazio libero o non allocato è separato dall'ESP (che si trova all'inizio del disco) dalla partizione principale di Windows (C: ) o da altre partizioni di servizio.

* **Limitazione di Windows:** La Gestione Disco di Windows non può estendere un volume a meno che lo spazio non allocato sia immediatamente contiguo.[15]  
* **Procedura con Strumento Terzo:**  
  1. **Riduzione:** Utilizzare la funzione "Shrink" (Riduci) sulla Partizione C: per creare almeno 500 MB di spazio non allocato (se non è già presente).  
  2. **Spostamento (Cruciale):** Utilizzare la funzione "Ridimensiona/Sposta" del software di terze parti per spostare fisicamente la partizione C: verso destra. Questo sposta lo spazio non allocato creato in precedenza, rendendolo adiacente (contiguo) all'ESP.[10]  
  3. **Estensione:** Estendere l'ESP nel nuovo spazio non allocato contiguo.

Un ostacolo comune, spesso riscontrato in sistemi OEM, è la Partizione Riservata Microsoft (MSR). Se la MSR (di 16 MB) si trova tra l'ESP e lo spazio non allocato e non può essere spostata o eliminata dagli strumenti di terze parti, il ridimensionamento è strutturalmente impossibile. In tal caso, si rende necessaria la Soluzione 3\.

---

## **IV. Soluzione 3: Ricreazione Totale della Partizione EFI (Rischio ALTISSIMO)**

Questa procedura è il piano di emergenza (Scenario 3\) e viene intrapresa solo quando la pulizia e il ridimensionamento non distruttivo sono falliti, spesso a causa della presenza di partizioni inamovibili (come la MSR) che impediscono l'estensione dell'ESP. Questa tecnica comporta la cancellazione e la ricreazione dell'intera struttura di avvio.

### **4.1. ALLARME CRITICO: Procedura Altamente Pericolosa**

**ATTENZIONE:** La cancellazione della Partizione di Sistema EFI comporterà l'immediata perdita dell'avviabilità del sistema operativo fino a quando la nuova partizione non sarà stata ricreata e il bootloader ricaricato correttamente. Un errore in questa fase, come l'omissione di un comando o l'errata selezione del disco, renderà il PC incapace di avviarsi senza un supporto di ripristino o installazione di Windows.[5]

### **4.2. Giustificazione della Ricreazione**

Se la partizione ESP esistente da 100 MB è circondata da partizioni che non possono essere né spostate né eliminate (come la Partizione Riservata Microsoft o la partizione di Recovery), la ricreazione completa è l'unico modo per creare un ESP più grande e funzionale nello spazio non allocato precedentemente liberato.

### **4.3. L'Approccio Metodologico (Creazione Prima, Distruzione Dopo)**

Per minimizzare il rischio, la procedura descritta di seguito segue una metodologia precauzionale: **la nuova partizione EFI funzionante viene creata, formattata e testata *prima* di eliminare quella vecchia.** In questo modo, il sistema avrà due potenziali partizioni di avvio, garantendo un percorso di fallback temporaneo.

---

## **V. Guida Operativa Dettagliata: Ricreazione EFI Passo Passo (DiskPart e BCDboot)**

Questa sezione descrive la sequenza esatta di comandi per ricreare la partizione ESP. È fondamentale eseguire i comandi con precisione.

### **V.I. Preparazione Spazio e Ingresso in DiskPart**

Assicurarsi che esista uno spazio non allocato di almeno 500 MB (o 1 GB) sul disco di sistema.

1. Aprire il Prompt dei Comandi (CMD) come Amministratore.  
2. Avviare l'utility di gestione del disco integrata:  
```   DiskPart ```

### **V.II. Selezione, Creazione e Formattazione del Nuovo ESP**

3. Elencare i dischi fisici:  
```   list disk  ```
   Identificare l'indice del disco di sistema (solitamente Disco 0).  
4. Selezionare il disco target:  
```   sel disk X  ``` (sostituire X con l'indice del disco corretto, es. sel disk 0\)  
5. Visualizzare le partizioni presenti per confermare lo spazio non allocato e l'indice dell'ESP vecchia (tipo "System"):  
```   list part  ```
6. Creare la nuova partizione EFI nello spazio non allocato disponibile. Si consiglia di utilizzare 500 MB:  
```  create partition efi size=500  ```
   (Utilizzare size=1000 per 1 GB, se si preferisce un margine maggiore).[16]  
7. Formattare rapidamente la partizione, obbligatoriamente in FAT32 per UEFI:  
```   format quick fs=fat32  ```
8. Assegnare una lettera di unità temporanea (ad esempio, Y:) per consentire la copia dei file di avvio:  
```   assign letter=Y  ```
9. Verificare che la nuova partizione (Volume Y:) sia stata creata correttamente come FAT32:  
```   list volume  ```
10. Uscire dall'utility DiskPart, ma mantenere aperto il Prompt dei Comandi:  
```    exit ```

## **V.III. Caricamento del Bootloader Windows (BCDBoot)**

In questa fase, i file di avvio essenziali vengono copiati dalla directory di Windows (`C:\Windows`) alla partizione EFI (ESP) appena creata (`Y:`) e il sistema operativo viene registrato nel firmware UEFI.

11. **Eseguire il comando BCDBoot:**

    ```
    bcdboot C:\Windows /s Y: /f UEFI
    ```

      * **`C:\Windows`**: Specifica la **directory sorgente** dell'installazione di Windows da cui copiare i file di avvio critici.
      * **`/s Y:`**: Specifica la **partizione di destinazione** (**System Partition**), che in questo caso è la nuova Partizione di Sistema EFI (ESP) identificata dalla lettera **`Y:`**.
      * **`/f UEFI`**: Specifica il **tipo di firmware** (`firmware type`). Il valore **`UEFI`** assicura che il bootloader sia configurato correttamente per gli ambienti basati su UEFI/GPT.

12. **Verifica Esito:** Se l'operazione è andata a buon fine, il messaggio visualizzato sarà: **`File di avvio creati con successo.`**

### **V.IV. Cancellazione del Vecchio ESP e Riavvio**

Una volta che il nuovo ESP è stato popolato e registrato, è sicuro eliminare il vecchio, piccolo ESP.

**Nota sulla Gestione Disco:** La Partizione di Sistema EFI (ESP) è una partizione protetta e **non può essere eliminata** tramite lo strumento grafico di Gestione Disco di Windows; l'opzione "Elimina volume" risulterà disattivata. L'eliminazione deve essere eseguita tramite l'utility DiskPart o tramite un software di terze parti.

13. Rientrare nell'utility DiskPart:  
```    DiskPart  ```
14. Selezionare nuovamente il disco di sistema:  
```    sel disk X  ``` (usando l'indice corretto)  
15. Visualizzare le partizioni:  
```    list part  ```
    Identificare l'indice (Z) della vecchia partizione ESP (tipicamente 100 MB, tipo "System")  
16. Selezionare e forzare la cancellazione della vecchia partizione ESP:  
```    sel part Z ``` (sostituire Z con l'indice corretto)  
```    delete partition override  ```
    L'opzione override è necessaria per eliminare partizioni di sistema protette.  
17. Uscire dal terminale e riavviare il PC:  
```    exit  ```
```    shutdown /r /t 0 (o semplicemente riavviare) ```

**Sequenza di Avvio Post-Cancellazione:**

Al riavvio, il sistema potrebbe tentare di avviare l'ESP predefinito appena eliminato, visualizzando un messaggio di errore (es. "media not found"). Questo è normale e non deve destare preoccupazione. Dopo questo fallimento, il firmware UEFI ricercherà automaticamente le voci di avvio valide e troverà il nuovo ESP (registrato tramite BCDboot), avviando il sistema operativo normalmente. Windows riconoscerà e utilizzerà ufficialmente il nuovo, più grande ESP.

---

## **VI. Troubleshooting e Considerazioni Aggiuntive**

### **6.1. Cosa fare in caso di fallimento del boot**

Se, dopo la cancellazione del vecchio ESP e il riavvio, il PC non riesce ad avviarsi (ad esempio, a causa di un messaggio persistente di "Boot Manager Missing"), è necessario avviare il sistema da un supporto di installazione o ripristino di Windows 11 (Windows PE).

Una volta entrati nell'Ambiente di Ripristino (accedendo al Prompt dei Comandi), è possibile tentare di riparare la configurazione di avvio:

1. Eseguire nuovamente la sequenza DiskPart e BCDboot descritta sopra, assicurandosi che il nuovo ESP sia stato selezionato e che il bootloader sia stato ricaricato.  
2. Se il problema persiste, si possono usare i comandi legacy di riparazione del boot:  

```   bootrec /FixBoot   ```
```   bootrec /FixMBR 18 ```

### **6.2. La Partizione di Ripristino (WinRE)**

È importante notare che l'insufficienza di spazio non riguarda solo l'ESP, ma in molti sistemi anche la Partizione di Ripristino di Windows (WinRE). Microsoft ha riconosciuto che gli aggiornamenti cumulativi, a partire da giugno 2023, richiedono spazio aggiuntivo (fino a 250 MB) nella partizione di ripristino per completare l'aggiornamento di WinRE.[19]

Se l'aggiornamento fallisce nonostante l'ingrandimento dell'ESP, il problema potrebbe essere la WinRE. In questo caso, Microsoft ha fornito istruzioni per ridimensionare la WinRE, spesso situata alla fine delle partizioni logiche, creando 250 MB di spazio non allocato immediatamente prima di essa.[19]

La necessità di ingrandire sia l'ESP che la WinRE per l'aggiornamento 24H2 sottolinea una tendenza generale: i Feature Updates di Windows 11 richiedono partizioni di servizio più generose rispetto al passato. Per le future installazioni pulite, l'adozione di un ESP di almeno 500 MB è un requisito fondamentale per garantire la longevità e la compatibilità con i futuri cicli di aggiornamento.[7]

---

## **VII. Conclusioni e Raccomandazioni**

La risoluzione degli errori 0xc1900200 e 0xc1900201 è un esercizio di gestione avanzata delle partizioni, reso necessario dalla configurazione sub-ottimale di molte installazioni OEM preesistenti. L'approccio dovrebbe sempre essere gerarchico, partendo dalla pulizia a basso rischio prima di passare al ridimensionamento non distruttivo e, in ultima istanza, alla ricreazione completa.

Si raccomanda vivamente di non ignorare il problema, poiché la saturazione dell'ESP impedirà qualsiasi Feature Update futuro, compromettendo la sicurezza e l'accesso alle nuove funzionalità del sistema operativo. La creazione di un ESP di 500 MB o 1 GB risolve il problema alla radice, fornendo la capacità necessaria per tutti i processi di staging di Windows e di aggiornamento del firmware. Data l'alta sensibilità dell'ESP, la preparazione di un backup completo è il prerequisito più critico per qualsiasi intervento.

#### **Bibliografia**

1. Windows 11, version 24H2 Install error \- 0xc1900201 \- HP Support Community \- 9399787, accesso eseguito il giorno ottobre 10, 2025, [https://h30434.www3.hp.com/t5/Notebook-Operating-System-and-Recovery/Windows-11-version-24H2-Install-error-0xc1900201/td-p/9399787](https://h30434.www3.hp.com/t5/Notebook-Operating-System-and-Recovery/Windows-11-version-24H2-Install-error-0xc1900201/td-p/9399787)  
2. Errore "Impossibile aggiornare la partizione riservata del sistema" durante l'installazione Windows 10 \- Microsoft Support, accesso eseguito il giorno ottobre 10, 2025, [https://support.microsoft.com/it-it/topic/errore-impossibile-aggiornare-la-partizione-riservata-del-sistema-durante-l-installazione-windows-10-46865f3f-37bb-4c51-c69f-07271b6672ac](https://support.microsoft.com/it-it/topic/errore-impossibile-aggiornare-la-partizione-riservata-del-sistema-durante-l-installazione-windows-10-46865f3f-37bb-4c51-c69f-07271b6672ac)  
3. UEFI/GPT-based hard drive partitions \- Microsoft Learn, accesso eseguito il giorno ottobre 10, 2025, [https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions?view=windows-11](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions?view=windows-11)  
4. Windows 11 24H2 Updated Failed: Partition error \- Microsoft Q\&A, accesso eseguito il giorno ottobre 10, 2025, [https://learn.microsoft.com/en-gb/answers/questions/2236282/windows-11-24h2-updated-failed-partition-error](https://learn.microsoft.com/en-gb/answers/questions/2236282/windows-11-24h2-updated-failed-partition-error)  
5. “We couldn't update system reserved partition” error installing Windows 10, accesso eseguito il giorno ottobre 10, 2025, [https://support.microsoft.com/en-us/topic/-we-couldn-t-update-system-reserved-partition-error-installing-windows-10-46865f3f-37bb-4c51-c69f-07271b6672ac](https://support.microsoft.com/en-us/topic/-we-couldn-t-update-system-reserved-partition-error-installing-windows-10-46865f3f-37bb-4c51-c69f-07271b6672ac)  
6. Windows 11 "new" EFI System Partition requirement. Autounattend.xml warning. \- Reddit, accesso eseguito il giorno ottobre 10, 2025, [https://www.reddit.com/r/sysadmin/comments/13yeh3d/windows\_11\_new\_efi\_system\_partition\_requirement/](https://www.reddit.com/r/sysadmin/comments/13yeh3d/windows_11_new_efi_system_partition_requirement/)  
7. Enlarging EFI partition / Windows 11 \- Super User, accesso eseguito il giorno ottobre 10, 2025, [https://superuser.com/questions/1902955/enlarging-efi-partition-windows-11](https://superuser.com/questions/1902955/enlarging-efi-partition-windows-11)  
8. Non siamo riusciti ad aggiornare la partizione di sistema riservata, errore di Windows 11 24H2. : r/WindowsHelp \- Reddit, accesso eseguito il giorno ottobre 10, 2025, [https://www.reddit.com/r/WindowsHelp/comments/1g3lnwu/we\_couldnt\_update\_system\_reserved\_partition/?tl=it](https://www.reddit.com/r/WindowsHelp/comments/1g3lnwu/we_couldnt_update_system_reserved_partition/?tl=it)  
9. Windows 11 Upgrade Fails – EFI/System Reserved Partition Too Small (100MB) \- Reddit, accesso eseguito il giorno ottobre 10, 2025, [https://www.reddit.com/r/sysadmin/comments/1mtu501/windows\_11\_upgrade\_fails\_efisystem\_reserved/](https://www.reddit.com/r/sysadmin/comments/1mtu501/windows_11_upgrade_fails_efisystem_reserved/)  
10. qualcuno può aiutarmi a spiegare come posso spostare parte dello spazio non allocato sull'unità C:? non mi permette di estendere il volume. : r/techsupport \- Reddit, accesso eseguito il giorno ottobre 10, 2025, [https://www.reddit.com/r/techsupport/comments/z6bj8x/can\_anyone\_help\_explain\_how\_i\_can\_move\_some\_of/?tl=it](https://www.reddit.com/r/techsupport/comments/z6bj8x/can_anyone_help_explain_how_i_can_move_some_of/?tl=it)  
11. Strumento gratuito da estendere EFI/Ripristino partizione in Windows 11, accesso eseguito il giorno ottobre 10, 2025, [https://www.hdd-tool.com/it/windows-11/extend-efi-and-recovery-partition.html](https://www.hdd-tool.com/it/windows-11/extend-efi-and-recovery-partition.html)  
12. Come Aumentare Dimensione della Partizione di Windows 10,11 in modo Facile e Sicuro?, accesso eseguito il giorno ottobre 10, 2025, [https://www.diskpart.com/it/windows-10/aumentare-partizione-windows-10.html](https://www.diskpart.com/it/windows-10/aumentare-partizione-windows-10.html)  
13. Come Ridimensionare le Partizioni su Windows 11 Senza Perdere Dati \- EaseUS, accesso eseguito il giorno ottobre 10, 2025, [https://it.easeus.com/partition-manager-tips/ridimensionare-le-partizioni-su-windows-11.html](https://it.easeus.com/partition-manager-tips/ridimensionare-le-partizioni-su-windows-11.html)  
14. Estendere/ridimensionare partizione di sistema EFI in Windows \[2020\] \- EaseUS, accesso eseguito il giorno ottobre 10, 2025, [https://it.easeus.com/partition-manager-tips/ridimensionare-partizione-di-sistema-efi-in-windows.html](https://it.easeus.com/partition-manager-tips/ridimensionare-partizione-di-sistema-efi-in-windows.html)  
15. Come posso estendere il volume usando lo spazio non allocato? : r/WindowsHelp \- Reddit, accesso eseguito il giorno ottobre 10, 2025, [https://www.reddit.com/r/WindowsHelp/comments/1hu8udc/how\_do\_i\_extend\_the\_volume\_using\_the\_unallocated/?tl=it](https://www.reddit.com/r/WindowsHelp/comments/1hu8udc/how_do_i_extend_the_volume_using_the_unallocated/?tl=it)  
16. creare la partizione efi \- Microsoft Learn, accesso eseguito il giorno ottobre 10, 2025, [https://learn.microsoft.com/it-it/windows-server/administration/windows-commands/create-partition-efi](https://learn.microsoft.com/it-it/windows-server/administration/windows-commands/create-partition-efi)  
17. BCDBoot Command-Line Options \- Microsoft Learn, accesso eseguito il giorno ottobre 10, 2025, [https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/bcdboot-command-line-options-techref-di?view=windows-11](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/bcdboot-command-line-options-techref-di?view=windows-11)  
18. Come riparare il bootloader EFI su un disco rigido GPT per sistemi operativi Windows, accesso eseguito il giorno ottobre 10, 2025, [https://www.dell.com/support/kbdoc/it-it/000124331/come-riparare-il-bootloader-efi-su-un-disco-rigido-gpt-per-sistemi-operativi-windows](https://www.dell.com/support/kbdoc/it-it/000124331/come-riparare-il-bootloader-efi-su-un-disco-rigido-gpt-per-sistemi-operativi-windows)  
19. KB5028997: Instructions to manually resize your partition to install the WinRE update \- Microsoft Support, accesso eseguito il giorno ottobre 10, 2025, [https://support.microsoft.com/en-us/topic/kb5028997-instructions-to-manually-resize-your-partition-to-install-the-winre-update-400faa27-9343-461c-ada9-24c8229763bf](https://support.microsoft.com/en-us/topic/kb5028997-instructions-to-manually-resize-your-partition-to-install-the-winre-update-400faa27-9343-461c-ada9-24c8229763bf)