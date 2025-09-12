# Disattivare Recall su Windows 11 (Versione 24H2)

La funzione **Recall** di Windows 11 memorizza automaticamente tutte le schermate catturate ogni 5 secondi. 
Queste immagini vengono analizzate localmente tramite algoritmi di intelligenza artificiale per estrarre testo e immagini e 
archiviate in un database SQLite non crittografato nella cartella dell'utente.

## Comandi per Gestire Recall

Puoi controllare, abilitare o disabilitare Recall utilizzando il terminale (CMD o PowerShell) in modalità amministratore. 
Ecco i comandi:

### 1. Controllare se Recall è abilitato:
```cmd
Dism /Online /Get-FeatureInfo /FeatureName:Recall
```

### 2. Disabilitare Recall:
```cmd
Dism /Online /Disable-Feature /FeatureName:Recall
```

### 3. Abilitare Recall:
```cmd
Dism /Online /Enable-Feature /FeatureName:Recall
```

## Che Cos’è Recall?

**Recall** è una funzione introdotta con Windows 11 versione 24H2, progettata per migliorare la produttività degli utenti, 
    ma con alcune implicazioni significative per la privacy e la sicurezza:

- Memorizza automaticamente tutte le schermate catturate ogni 5 secondi.
- Analizza le schermate con algoritmi di intelligenza artificiale per estrarre testo e immagini.
- Salva i dati in un database SQLite **non crittografato** nella cartella locale dell'utente.
- Indicizza le informazioni, rendendole sempre disponibili all'utente.

### Problemi di Sicurezza e Privacy

Nonostante i benefici in termini di accessibilità e produttività, Recall comporta rischi significativi per la sicurezza e la privacy:

- **Accessibilità non protetta**: Il database SQLite creato da Recall non è protetto da alcuna crittografia o restrizione di accesso.
- **Rischio di furto di dati**: Un componente malevolo in esecuzione sul sistema potrebbe accedere facilmente al database locale, 
    acquisendo tutte le informazioni archiviate.
- **Valutazioni regolamentari**: Sarebbe opportuno che questa funzione fosse attentamente valutata dalle autorità per la 
    protezione dei dati personali e della cybersicurezza prima della sua adozione diffusa.

## Conclusione

Disabilitare Recall è consigliato se si desidera proteggere la propria privacy e ridurre i rischi di esposizione 
non autorizzata delle proprie informazioni. 
I comandi sopra indicati ti permettono di gestire questa funzione in modo semplice ed efficace.

