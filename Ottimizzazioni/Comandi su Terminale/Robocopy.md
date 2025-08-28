## **Guida a Robocopy (Robust File Copy)**

Robocopy, abbreviazione di **Robust File Copy**, è un'utility da riga di comando integrata in Windows che offre una copia di file e directory molto più potente e affidabile rispetto al tradizionale "copia e incolla". È particolarmente utile per operazioni complesse come backup, sincronizzazione e migrazione di grandi volumi di dati, specialmente su reti.

-----

### **A cosa serve**

Robocopy è uno strumento versatile utilizzato per:

  * **Backup incrementale**: copia solo i file nuovi o modificati, risparmiando tempo e risorse.
  * **Sincronizzazione di directory**: mantiene una copia speculare (mirror) tra due percorsi, assicurando che siano sempre identici.
  * **Migrazione dati**: sposta grandi quantità di dati da un'unità all'altra mantenendo intatte le proprietà dei file (come permessi e timestamp).
  * **Gestione degli errori**: può riprovare a copiare i file che falliscono inizialmente, rendendolo ideale per le copie su connessioni di rete instabili.

-----

### **Sintassi di base e parametri comuni**

La sintassi di base è `robocopy [origine] [destinazione] [opzioni]`.

Ecco alcuni dei parametri più comuni e utili:

  * `/S`: copia le sottodirectory, ma esclude quelle vuote.
  * `/E`: copia le sottodirectory, incluse quelle vuote.
  * `/MIR`: esegue la sincronizzazione, copiando i file nuovi e modificati e **eliminando** quelli che non sono più presenti nel percorso di origine. È un comando molto potente, da usare con cautela.
  * `/Z`: esegue la copia in "modalità riavviabile", permettendo a Robocopy di riprendere la copia di un file interrotta.
  * `/DCOPY:T`: mantiene i timestamp delle directory.
  * `/MT[:n]`: abilita la copia multi-thread. Aumenta la velocità di copia usando più thread contemporaneamente, con `n` che indica il numero di thread da usare (default 8, max 128).
  * `/R:n`: imposta il numero di tentativi per ogni file fallito (default 1.000.000). Usa `/R:1` per un solo tentativo aggiuntivo.
  * `/W:n`: imposta il tempo di attesa tra i tentativi in secondi (default 30).
  * `/L`: esegue una **simulazione** dell'operazione, mostrando cosa verrebbe copiato senza effettivamente copiare nulla.
  * `/LOG:file`: salva l'output del comando in un file di log. Usa `/LOG+:file` per aggiungere l'output a un file esistente.
  * `/NP`: non mostra l'avanzamento della copia in percentuale per una maggiore leggibilità del log.

-----

### **Esempio di utilizzo pratico**

Il comando `robocopy.exe "Percorso\origine" "Percorso\destinazione" /COPY:DATSOU /e /r:1` è un ottimo esempio di comando di backup robusto. Analizziamo le opzioni:

  * `robocopy.exe`: richiama l'eseguibile.
  * `"Percorso\origine"` e `"Percorso\destinazione"`: specificano le cartelle. Le virgolette sono necessarie se i percorsi contengono spazi.
  * `/COPY:DATSOU`: specifica gli attributi da copiare: **D**ati, **A**ttributi, **T**imestamp, **S**icurezza (permessi NTFS), **O**wner (proprietario) e **U**dit (informazioni di controllo).
  * `/e`: include tutte le sottocartelle, anche quelle vuote.
  * `/r:1`: riprova a copiare un file fallito solo una volta, evitando di bloccare l'operazione in caso di errori persistenti.

Per usarlo, apri il **Prompt dei comandi** (o Windows Terminal) come amministratore e inserisci il comando sostituendo i percorsi con i tuoi.

> "Robocopy è un'utility della riga di comando versatile e potente per copiare file e directory." — [Microsoft Learn](https://learn.microsoft.com/it-it/windows-server/administration/windows-commands/robocopy)

\<br\>

\<br\>
Il video [Robocopy, the Ultimate Guide](https://www.youtube.com/watch?v=_jco9nMMPr8) fornisce una guida completa e visiva all'utilizzo di Robocopy.
http://googleusercontent.com/youtube_content/0
