# **Ottimizzazione del Mouse in Windows**

Ottimizzare le impostazioni del mouse è fondamentale per migliorare la precisione, il controllo e la reattività.  
Queste modifiche sono particolarmente utili per chi utilizza il computer per il **gaming competitivo** o per il **design grafico**.  

L'ottimizzazione delle seguenti aree chiave ti permetterà di avere il pieno controllo del movimento del cursore:  
- **DPI (Dots Per Inch) del mouse**  
- **Disabilitazione dell'accelerazione del mouse**  
- **Modifica delle chiavi di registro di Windows**  

---

## **🖱️ DPI del Mouse: Cosa Sono e Come Influiscono?**
Il **DPI** (Dots Per Inch) definisce la sensibilità del mouse, ovvero la quantità di pixel che il cursore 
   si sposta sullo schermo per ogni pollice (2,54 cm) di movimento fisico del mouse.  
- **DPI più alto**: il cursore si muove più velocemente.  
- **DPI più basso**: il cursore si muove più lentamente ma con maggiore precisione.  

### **📋 Consigli sul DPI**
- **Alta precisione**: Utilizzare un **DPI più alto** riduce il rischio di "pixel skipping" (salti di pixel) e migliora la **latenza** del cursore.  
- **Impatto sulle prestazioni**: Usare DPI troppo alti (come **8000 DPI**) può ridurre il **frame rate (FPS)**, soprattutto nei giochi, 
   poiché il sistema deve elaborare i movimenti con una frequenza maggiore.  
- **Valore consigliato**: Un'impostazione di **1000 DPI** offre un buon compromesso tra velocità, precisione e prestazioni.  

| **DPI**          | **Precisione** | **Velocità** | **Impatto su FPS** | **Consigliato per...**                    |
|------------------|----------------|--------------|--------------------|-------------------------------------------|
| **400 DPI**      | 🔥 Alta        | 🐢 Lenta     | 🟢 Nessun impatto  | Precisione massima (design, editing)      |
| **800-1000 DPI** | 👍 Buona       | 🚶 Media     | 🟢 Nessun impatto  | Uso generale e gaming standard            |
| **1600-2000 DPI**| 😐 Accettabile | 🚀 Veloce    | ⚠️ Leggero impatto | Gaming frenetico, FPS o MOBA              |
| **> 4000 DPI**   | 😕 Bassa       | ⚡ Iperveloce | 🔴 Impatto elevato | Non consigliato, tranne in casi specifici |

> 💡 **Consiglio:** Se sei un gamer o un utente avanzato, **1000 DPI** è la scelta migliore per un controllo stabile e un consumo minimo di risorse.  

---

## **📋 Passaggi per Ottimizzare il Mouse**

### **1️⃣ Disabilitare "Aumenta precisione puntatore"**
La funzione "Aumenta precisione puntatore" aggiunge **accelerazione dinamica** ai movimenti del mouse, ma questo rende i movimenti meno prevedibili.  
Per un'esperienza lineare e costante, è consigliabile **disattivarla**.  

**📌 Procedura:**
1. **Apri le impostazioni del mouse**:  
   - Premi **Windows + I** per aprire le **Impostazioni**.  
   - Vai su **Dispositivi** > **Mouse**.  
   - Clicca su **Opzioni aggiuntive del mouse**.  
   - Nella finestra che si apre, vai alla scheda **Opzioni puntatore**.  

2. **Disabilita "Aumenta precisione puntatore"**:  
   - Nella sezione **Movimento**, **deseleziona la casella** **"Aumenta precisione puntatore"**.  
   - Clicca su **Applica** e poi su **OK**.  

> 🛑 **Importante**: La precisione del mouse dipenderà solo dal DPI e dalla sensibilità impostata nelle applicazioni (come nei giochi).  

---

### **2️⃣ Modificare le Impostazioni del Registro Manualmente**
Per disabilitare ulteriormente l'accelerazione e garantire una risposta più lineare, è necessario modificare alcune chiavi di registro.  

**⚠️ Attenzione:** Modificare il registro di sistema può causare problemi se fatto in modo errato. Segui con attenzione i passaggi.  

#### **📋 Passaggi per modificare manualmente il registro**
1. **Apri l'Editor del Registro di Sistema**:  
   - Premi **Windows + R**, digita **regedit** e premi **Invio**.  
   - Se richiesto, conferma l'operazione come amministratore.  

2. **Modifica le chiavi di registro**:  
   - Vai a **HKEY_CURRENT_USER\Control Panel\Mouse**.  
   - Modifica o crea i seguenti valori:  
     - **MouseSensitivity** = **10**  
     - **MouseSpeed** = **0**  
     - **MouseThreshold1** = **0**  
     - **MouseThreshold2** = **0**  

   - Modifica i valori delle curve del mouse:  
     - **SmoothMouseXCurve** e **SmoothMouseYCurve**:  
       ```plaintext
       SmoothMouseXCurve: 
       00,00,00,00,00,00,00,00,\
       C0,CC,0C,00,00,00,00,00,\
       80,99,19,00,00,00,00,00,\
       40,66,26,00,00,00,00,00,\
       00,33,33,00,00,00,00,00
       
       SmoothMouseYCurve: 
       00,00,00,00,00,00,00,00,\
       00,00,38,00,00,00,00,00,\
       00,00,70,00,00,00,00,00,\
       00,00,A8,00,00,00,00,00,\
       00,00,E0,00,00,00,00,00
       ```

3. **Salva le modifiche**:  
   - Dopo aver effettuato le modifiche, chiudi l'Editor del Registro e **riavvia il PC** per applicare i cambiamenti.  

---

## **🎮 Benefici delle Ottimizzazioni**
| **Ottimizzazione**                      | **Effetto**                                                 |
|-----------------------------------------|-------------------------------------------------------------|
| **DPI a 1000**                          | Migliora la precisione e riduce la latenza.                 |
| **Disattivazione "Aumenta precisione"** | Rende il movimento più prevedibile.                         |
| **Modifiche al registro**               | Disattiva l'accelerazione dinamica e stabilizza il cursore. |

---

## **📈 Confronto delle Impostazioni**
| **Impostazione**    | **Precisione** | **Velocità** | **Prestazioni (FPS)**| **Consigliata?**|
|---------------------|----------------|--------------|----------------------|-----------------|
| **DPI 1000**        | 👍 Buona       | 🚶 Media     | 🟢 Nessun impatto    | ✅ **Sì**       |
| **DPI 8000**        | 😕 Bassa       | ⚡ Iperveloce | 🔴 Riduce FPS        | ❌ **No**        |
| **Accel. attiva**   | 😕 Variabile   | 😕 Variabile | ⚠️ Impatto medio     | ❌ **No**        |
| **Accel. disattiva**| 🔥 Prevedibile | 🚶 Media     | 🟢 Nessun impatto    | ✅ **Sì**       |

---

## **🛠️ Conclusione**
- Imposta il **DPI a 1000** per garantire **precisione, bassa latenza e prestazioni ottimali**.  
- **Disattiva "Aumenta precisione puntatore"** per garantire movimenti costanti e lineari.  
- Se sei un gamer o un utente avanzato, le modifiche al **registro di Windows** ti garantiranno **controllo totale** sul mouse.  

> 💡 **Suggerimento finale:** Se usi il mouse per gaming competitivo (come FPS), un valore DPI tra **800 e 1600** è il migliore, ma dipende anche dalla sensibilità in-game.  