# Guida: Disabilitare l'accensione automatica del PC per aggiornamenti notturni (Windows 11)

## 1. Contesto e problema
Molti PC Windows 11 si riattivano automaticamente durante la notte (spesso attorno alle 3:00) per installare gli aggiornamenti di sistema. Questo comportamento può avere diverse conseguenze negative:

- **Sicurezza e privacy**: il PC potrebbe accendersi in un momento in cui non siete presenti, esponendo dati o file aperti.
- **Usura dell’hardware**: accensioni e cicli di sospensione ripetuti possono incrementare lo stress termico e deteriorare componenti nel lungo periodo.
- **Consumo energetico**: il dispositivo si riattiva senza necessità, generando spreco di energia.

## 2. Obiettivo della guida
Disabilitare i timer di riattivazione (Wake timers) per evitare che Windows 11 accenda automaticamente il PC per gli aggiornamenti notturni.


## 3. Procedura passo-passo

1. **Apri il Pannello di controllo**
   - Premi Win + R, digita `control` e premi Invio.

2. **Accedi alle Opzioni risparmio energia**
   - Seleziona **Hardware e suoni** → **Opzioni risparmio energia**.

3. **Modifica impostazioni del piano attivo**
   - Accanto al piano selezionato (ad esempio, Bilanciato), clicca su **Modifica impostazioni combinazione**.

4. **Cambia impostazioni avanzate**
   - Clicca su **Modifica impostazioni avanzate risparmio energia**.

5. **Disabilita i timer di riattivazione**
   - Nella finestra di dialogo, espandi **Sospensione** → **Consenti timer di riattivazione**.
   - Imposta entrambe le voci:
     - **Alimentazione a batteria**: **Disabilitata**
     - **Alimentazione da rete elettrica**: **Disabilitata**

6. **Conferma e applica**
   - Clicca su **Applica** e poi su **OK** per salvare le modifiche.


## 4. Verifica e consigli aggiuntivi

- **Controlla le attività pianificate**: apri **Utilità di pianificazione** e verifica che non ci siano attività impostate per riattivare il computer.
- **Mantieni aggiornato il sistema**: dopo aver riattivato manualmente il PC, esegui gli aggiornamenti in un orario a te comodo.
- **Modalità di ibernazione**: se desideri ridurre ulteriormente i consumi, valuta l’uso dell’ibernazione anziché la sospensione.
