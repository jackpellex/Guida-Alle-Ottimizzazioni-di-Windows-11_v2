# Ottimizzazione della Priorità GPU e CPU per i Giochi

## Introduzione

La sezione del registro di sistema relativa a
`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Multimedia\SystemProfile\Tasks\Games`
contiene parametri utilizzati da Windows per gestire la priorità e la pianificazione delle risorse (CPU e GPU) nei giochi.

Queste impostazioni possono influire sulla latenza, sugli FPS e sulla fluidità generale, soprattutto nei sistemi Windows ottimizzati per il gaming.

### Come Modificarlo

1. Premi **Win + R**, digita `regedit` e premi **Invio**.

2. Naviga fino al percorso:

   ```
   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Multimedia\SystemProfile\Tasks\Games
   ```

3. Nella parte destra troverai le seguenti chiavi principali:

   * **GPU Priority**
   * **Priority**
   * **Scheduling Category**
   * **SFIO Priority**
   * (Eventualmente anche Clock Rate, Affinity, ecc.)

4. Fai doppio clic sulla chiave che vuoi modificare, scegli **Decimale** o **Esadecimale**, imposta il valore e conferma.

## Valori Importanti

### 1. GPU Priority (`REG_DWORD`)

Determina la priorità dei carichi grafici rispetto ad altre operazioni.

| **Valore** | **Effetto**                                     |
| ---------- | ----------------------------------------------- |
| `1–7`      | Priorità bassa (meno risorse GPU per il gioco). |
| `8`        | Priorità massima (consigliato per il gaming).   |

### 2. Priority (`REG_DWORD`)

Gestisce la priorità del thread del gioco lato CPU.

| **Valore** | **Effetto**                                                     |
| ---------- | --------------------------------------------------------------- |
| `1–5`      | Bassa priorità.                                                 |
| `6`        | Alta priorità per processi di gioco (predefinito raccomandato). |

### 3. Scheduling Category (`REG_SZ`)

Definisce la categoria di pianificazione.

| **Valore** | **Effetto**                                   |
| ---------- | --------------------------------------------- |
| `Low`      | Bassa priorità di pianificazione.             |
| `Medium`   | Equilibrato.                                  |
| `High`     | Priorità alta per massimizzare la reattività. |

### 4. SFIO Priority (`REG_SZ`)

Imposta la priorità delle operazioni di I/O.

| **Valore** | **Effetto**                            |
| ---------- | -------------------------------------- |
| `Normal`   | Predefinito.                           |
| `High`     | Riduce la latenza di I/O per i giochi. |

---

## Consigli di Utilizzo

* **Gaming competitivo:**

  * GPU Priority = `8`
  * Priority = `6`
  * Scheduling Category = `High`
  * SFIO Priority = `High`
* **Uso generale / multitasking:**

  * Mantieni i valori predefiniti o leggermente più bassi per evitare di sottrarre risorse ad altre applicazioni.

## Avvertenze

* Modificare queste chiavi influisce sulla gestione interna delle risorse di Windows: usa cautela.
* Effetti e benefici possono variare in base all’hardware e al sistema operativo.
* Crea sempre un **punto di ripristino** prima di effettuare modifiche.

## Conclusione

Regolare **GPU Priority**, **Priority** e le impostazioni di scheduling nella sezione *Games* può aiutare a ottenere prestazioni migliori nei giochi, soprattutto in termini di FPS stabili e minore latenza.
