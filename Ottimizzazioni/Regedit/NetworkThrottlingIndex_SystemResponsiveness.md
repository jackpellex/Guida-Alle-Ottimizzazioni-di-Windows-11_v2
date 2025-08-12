# Ottimizzazione delle Prestazioni di Rete e Reattività del Sistema con `NetworkThrottlingIndex` e `SystemResponsiveness`

## Introduzione

Le chiavi di registro `NetworkThrottlingIndex` e `SystemResponsiveness` controllano rispettivamente la gestione della velocità di elaborazione dei pacchetti di rete e la quantità di risorse riservate alle attività multimediali e di background su Windows. La loro configurazione può ridurre la latenza, migliorare la reattività del sistema e ottimizzare le prestazioni in gioco, nello streaming o nella produzione multimediale.

## Percorso

```
Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Multimedia\SystemProfile
```

## Come modificarle

1. Premi **Win + R**, digita `regedit` e premi **Invio**.
2. Vai al percorso indicato sopra.
3. Nella finestra di destra individua le voci `NetworkThrottlingIndex` e `SystemResponsiveness`.
4. Fai doppio clic sul valore da modificare, seleziona **Esadecimale** o **Decimale** e imposta il nuovo valore.
5. Riavvia il sistema per applicare le modifiche.

---

## `NetworkThrottlingIndex`

| **Valore** (formato) | **Significato**                                                                              |
| -------------------- | -------------------------------------------------------------------------------------------- |
| `0xffffffff` (hex)   | Disattiva il throttling della rete (massime prestazioni).                                    |
| `1` – `70` (dec)     | Limita la frequenza di elaborazione dei pacchetti (valori più alti indicano più throttling). |
| `10` (dec)           | Valore predefinito bilanciato.                                                               |

### Note su `NetworkThrottlingIndex`

* Impostando `0xffffffff` si rimuove la limitazione lato OS sul processamento dei pacchetti multimediali, utile per ridurre la latenza in gaming/streaming.
* Valori decimali intermedi riducono il carico CPU ma possono aumentare la latenza percepita dalle applicazioni in tempo reale.

---

## `SystemResponsiveness`

| **Valore** (decimale) | **Significato**                                                                                                                                             |
| --------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `0`                   | Nessuna CPU riservata a servizi multimediali/background (priorità massima al foreground).                                                                   |
| `10`                  | Valore predefinito su sistemi client (10% riservato a processi multimediali/background).                                                                    |
| `20`–`100`            | Percentuale maggiore di CPU riservata a processi multimediali/background (valori più alti riducono le risorse disponibili per applicazioni in primo piano). |

### Note su `SystemResponsiveness`

* Un valore basso (es. `0`) favorisce la massima reattività delle applicazioni in primo piano (utile per gaming competitivo).
* Valori più alti aiutano la riproduzione multimediale e i processi in background a rimanere stabili sotto carico CPU elevato.

---

## Valori consigliati per scenari comuni

| **Scenario**                | `NetworkThrottlingIndex` | `SystemResponsiveness` |
| --------------------------- | ------------------------ | ---------------------- |
| Gaming competitivo          | `0xffffffff`             | `0`                    |
| Streaming / Live            | `0xffffffff` o `10`      | `0`–`10`               |
| Uso generale / multitasking | `10`                     | `10`                   |
| Produzione multimediale     | `10`                     | `20` o superiore       |

---

## Consigli di utilizzo

* Per ridurre la latenza di rete e aumentare la reattività in gioco, disattiva il throttling impostando `NetworkThrottlingIndex` su `0xffffffff` e porta `SystemResponsiveness` a `0`.
* Per un bilanciamento tra stabilità e prestazioni quotidiane mantieni entrambi i valori su `10`.
* Per lavori di produzione (editing audio/video) aumenta `SystemResponsiveness` a `20` o più per garantire risorse costanti ai processi multimediali.

---

## Avvertenze

* Modificare il registro di sistema è un'operazione avanzata. Crea un punto di ripristino e fai un backup del registro prima di procedere.
* Disattivare il throttling (`0xffffffff`) può aumentare l’uso della CPU in presenza di traffico di rete elevato.
* Impostare `SystemResponsiveness` a valori molto bassi può causare glitch o instabilità per processi multimediali in background.
* Gli effetti variano in base a hardware, driver di rete e software in uso; testa le impostazioni per trovare il miglior equilibrio sul tuo sistema.

---

## Conclusione

La regolazione di `NetworkThrottlingIndex` e `SystemResponsiveness` consente un controllo fine sulla gestione delle risorse di rete e CPU di Windows. Sperimenta i valori suggeriti in base allo scenario d'uso per trovare la configurazione ottimale per il tuo sistema.

---

**Nota:** Questa guida è destinata a utenti avanzati. Non mi assumo responsabilità per eventuali danni o malfunzionamenti causati dalle modifiche al registro di sistema.
