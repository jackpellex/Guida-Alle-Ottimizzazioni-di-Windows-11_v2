## Winget: Comandi Principali

Winget è un gestore di pacchetti a riga di comando che ti permette di scoprire, installare, aggiornare, rimuovere e configurare le applicazioni sul tuo sistema Windows 10 e 11.

-----

### 1\. Cercare un pacchetto

Trova le applicazioni disponibili nel repository Winget.

```powershell
winget search <keyword>
# Esempio:
winget search vscode
```

-----

### 2\. Installare un'app

Installa una specifica applicazione. Puoi trovare il `PackageIdentifier` usando il comando `winget search`.

```powershell
winget install <PackageIdentifier>
# Esempio:
winget install Microsoft.VisualStudioCode
```

-----

### 3\. Elencare le app installate

Visualizza un elenco di tutte le applicazioni installate sul tuo sistema che Winget può gestire.

```powershell
winget list
```

-----

### 4\. Aggiornare un singolo pacchetto

Aggiorna una specifica applicazione alla sua ultima versione disponibile.

```powershell
winget upgrade --id <PackageIdentifier>
# Esempio:
winget upgrade --id Mozilla.Firefox
```

-----

### 5\. Aggiornare tutti i pacchetti

Aggiorna tutte le applicazioni installate che Winget rileva come non aggiornate.

```powershell
winget upgrade --all
```

-----

### 6\. Aggiornamento Avanzato di Tutti i Pacchetti

Questo comando rappresenta un modo più "aggressivo" o automatico per aggiornare tutti i pacchetti installati sul tuo sistema tramite Winget. È particolarmente utile in scenari di automazione o quando desideri che Winget gestisca il maggior numero possibile di aggiornamenti senza interruzioni.

```powershell
winget upgrade --all --include-unknown --accept-source-agreements --accept-package-agreements --silent
```

#### Spiegazione dei Flag

Vediamo a cosa serve ciascun componente aggiuntivo in questo comando:

  * **`--all`**: Questo è il flag principale per indicare a Winget di tentare di **aggiornare tutti i pacchetti** che trova sul sistema e che sono gestiti da Winget. Senza questo, dovresti specificare ogni singolo pacchetto da aggiornare.

  * **`--include-unknown`**: Di default, Winget è piuttosto cauto e potrebbe non aggiornare applicazioni la cui origine non è chiaramente identificabile o che sono state installate manualmente al di fuori dei canali Winget. Il flag `--include-unknown` indica a Winget di **includere nel processo di aggiornamento anche i pacchetti di cui non conosce l'origine esatta**. Questo può aumentare il numero di app aggiornate, ma comporta anche un minimo rischio aggiuntivo, dato che Winget ha meno informazioni sulla provenienza del software.

  * **`--accept-source-agreements`**: Quando aggiungi una nuova "sorgente" (repository di pacchetti) a Winget, o quando una sorgente ha dei termini e condizioni specifici, Winget normalmente ti chiede di accettare questi accordi. Usando questo flag, stai dicendo a Winget di **accettare automaticamente qualsiasi accordo relativo alle sorgenti** senza chiedere conferma. È utile per l'automazione, ma significa anche che stai accettando potenziali termini e condizioni senza leggerli.

  * **`--accept-package-agreements`**: Simile al flag precedente, alcune applicazioni o pacchetti specifici potrebbero avere i propri termini di licenza o accordi da accettare prima dell'installazione o dell'aggiornamento. Questo flag istruisce Winget a **accettare automaticamente tutti gli accordi specifici dei pacchetti**. Ancora una volta, ottimo per l'automazione, ma fai attenzione a ciò che accetti\!

  * **`--silent`**: Questo è un flag molto utile per l'automazione. Quando Winget installa o aggiorna applicazioni, di solito mostra una finestra di avanzamento o un output dettagliato nella console. Il flag `--silent` fa sì che l'operazione venga eseguita in **modalità silenziosa**, il che significa che Winget tenterà di non mostrare alcuna interfaccia utente o output verboso durante il processo. L'aggiornamento avverrà "dietro le quinte", rendendolo ideale per script o operazioni programmate.

#### Perché sono stati messi insieme?

Questi flag sono stati combinati per creare un **comando di aggiornamento completo e non interattivo**. L'obiettivo è permettere a Winget di:

  * **Aggiornare il maggior numero possibile di applicazioni** (grazie a `--all` e `--include-unknown`).
  * **Procedere senza interruzioni** dovute a richieste di accettazione di accordi (grazie a `--accept-source-agreements` e `--accept-package-agreements`).
  * **Eseguire il tutto in background** senza disturbare l'utente (grazie a `--silent`).

Questo lo rende un comando potente per la manutenzione automatizzata del sistema, ma è cruciale capire le implicazioni di ogni flag prima di usarlo frequentemente, specialmente quelle legate all'accettazione automatica di accordi.

-----

### 7\. Disinstallare un'app

Rimuove un'applicazione dal tuo sistema.

```powershell
winget uninstall <PackageIdentifier>
# Alias: winget remove, winget rm
```

-----

### 8\. Esportare la lista dei pacchetti

Crea un file JSON con l'elenco di tutte le applicazioni installate che possono essere gestite da Winget. Utile per configurare un nuovo sistema.

```powershell
winget export -o packages.json
```

-----

### 9\. Importare i pacchetti da un file

Installa tutte le applicazioni elencate in un file JSON creato precedentemente con il comando `export`.

```powershell
winget import -i packages.json
```

-----

### 10\. Mostrare i dettagli di un pacchetto

Visualizza informazioni dettagliate su una specifica applicazione, inclusa la versione, il produttore e l'URL.

```powershell
winget show <PackageIdentifier>
```

-----

### 11\. Informazioni sul client Winget

Mostra i dettagli della versione e altre informazioni relative al client Winget.

```powershell
winget --info
```

-----
