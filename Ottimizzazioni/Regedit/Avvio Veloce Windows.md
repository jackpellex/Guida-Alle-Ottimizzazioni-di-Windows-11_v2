
# Ottimizzazione Avvio Veloce di Windows con Modifiche ai Registri

## Introduzione
Le seguenti impostazioni di registro migliorano la velocità e la reattività del sistema operativo Windows. 
Esse possono essere applicate manualmente o utilizzando uno script `.reg`.

## Dettaglio delle Impostazioni
### Cosa fanno queste modifiche:
- **AutoEndTasks**: Termina automaticamente le attività che non rispondono quando si spegne o si esce dal sistema.
- **HungAppTimeout**: Riduce il tempo di attesa prima che Windows consideri un’applicazione come "non rispondente".
- **MenuShowDelay**: Diminuisce il ritardo prima che i menu appaiano quando ci si passa sopra con il mouse.
- **LowLevelHooksTimeout**: Riduce il tempo di attesa per completare le procedure di hook a basso livello.

### Valori applicati:
```plaintext
Windows Registry Editor Version 5.00

[HKEY_CURRENT_USER\Control Panel\Desktop]
"AutoEndTasks"="1"
"HungAppTimeout"="1000"
"MenuShowDelay"="8"
"LowLevelHooksTimeout"="1000"
```

## Come Applicare Manualmente le Modifiche
1. Aprire **Editor del Registro di sistema**:
   - Premere `Win + R` e digitare `regedit`, quindi premere **Invio**.
2. Navigare alla seguente chiave:
   ```
   HKEY_CURRENT_USER\Control Panel\Desktop
   ```
3. Modificare o creare i seguenti valori:
   - **AutoEndTasks**: Impostare a `1`.
   - **HungAppTimeout**: Impostare a `1000`.
   - **MenuShowDelay**: Impostare a `8`.
   - **LowLevelHooksTimeout**: Impostare a `1000`.
4. Salvare le modifiche e riavviare il sistema per applicarle.

## Avvertenze Importanti
- **Punto di Ripristino**: Prima di modificare il registro, è essenziale creare un punto di ripristino del sistema per garantire il recupero in caso di problemi.
   - Per farlo:
     1. Cercare "Punto di Ripristino" nella barra di ricerca di Windows.
     2. Selezionare "Crea un punto di ripristino" e seguire le istruzioni.
- **Riavvio Necessario**: Alcune modifiche ai registri non hanno effetto immediato e richiedono un riavvio per essere applicate.

## Conclusione
Queste impostazioni sono utili per migliorare la reattività del sistema e ridurre i tempi di attesa nelle operazioni quotidiane. Si consiglia di utilizzarle con cautela e di mantenere sempre una copia di backup del registro.
