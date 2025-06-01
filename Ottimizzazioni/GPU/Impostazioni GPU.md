# 🖥️ **Ottimizzazione NVIDIA APP e Pannello di Controllo NVIDIA**  

Questa guida fornisce le istruzioni essenziali per ottimizzare le impostazioni grafiche utilizzando **NVIDIA APP** e il **Pannello di Controllo NVIDIA**. 
Queste configurazioni mirano a bilanciare qualità grafica, prestazioni e fluidità, ideali per gaming, editing video e utilizzo quotidiano.  

---

## 🚀 **1. Aggiornamento dei Driver NVIDIA**  

Prima di tutto, assicurati di avere i driver grafici più recenti:  
1. Scarica e installa **NVIDIA APP** da [qui](https://www.nvidia.com/en-us/software/nvidia-app/).  
2. Apri l'app, vai nella sezione **Drivers** e installa l'ultima versione del driver disponibile.  

---

## 🎮 **2. Configurazioni Essenziali nel Pannello di Controllo NVIDIA**  

### 🔧 **Accesso al Pannello di Controllo NVIDIA**  
1. Clic con il tasto destro sul desktop.  
2. Seleziona **Pannello di Controllo NVIDIA**.  
> Se non trovi questa opzione, scaricala dal Microsoft Store.  

---

## ⚙️ **3. Impostazioni nel Pannello di Controllo NVIDIA**  

### **3D Settings → Adjust Image Settings with Preview**  
- Seleziona **Usa le impostazioni avanzate per l'immagine 3D**.  
- Clicca su **Take me there** per accedere a **Manage 3D Settings**.  

---

### 🔥 **Configurazioni Globali (Manage 3D Settings)**  

| **Impostazione**                          | **Valore consigliato**            | **Spiegazione** |
|-------------------------------------------|-----------------------------------|-----------------|
| **Image Scaling**                         | **Attiva (solo se necessario)**   | Riduce la qualità grafica di oggetti distanti per aumentare gli FPS. Utile per FPS più elevati. |
| **DSLL (Deep Learning Super Sampling)**   | **Attiva (se disponibile)**       | Migliora la qualità visiva e le prestazioni. Preferibile rispetto a Image Scaling. |
| **Ambient Occlusion**                     | **Disattiva**                     | Disabilitare per ottenere più FPS. Aggiunge ombre in tempo reale, ma pesa sulle prestazioni. |
| **Anisotropic Filtering**                 | **16x (o personalizzato)**        | Migliora la qualità delle texture viste da angolazioni ripide. Disattivandolo, il pavimento sarà sfocato. |
| **Antialiasing**                          | **Disattiva (se non necessario)** | Arrotonda le linee "seghettate". Se disattivato, si ottengono più FPS, ma le linee appaiono più spigolose. |
| **Background Application Max Frame Rate** | **Disattiva**                     | Limita gli FPS delle app in background, utile per risparmiare energia. |
| **CUDA - GPUs**                           | **All**                           | Se hai più GPU, questa opzione permette di sfruttarle insieme. |
| **DSR (Dynamic Super Resolution)**        | **Disattiva (se hai DLSS)**       | Aumenta la risoluzione virtuale per migliorare la qualità grafica, ma usa molte risorse. |
| **Low Latency Mode**                      | **On**                            | Riduce la latenza tra input e output, migliorando la reattività di mouse e tastiera. |
| **NVIDIA G-Sync**                         | **Attiva**                        | Sincronizza la frequenza di aggiornamento del monitor con la GPU per ridurre il tearing. |
| **Power Management Mode**                 | **Normal**                        | Evita di usare la modalità "Massime Prestazioni" per non surriscaldare la GPU inutilmente. |
| **Shader Cache Size**                     | **Driver Default**                | Memorizza le shader precompilate, riducendo i tempi di caricamento nei giochi. |
| **Texture Filtering**                     | **Personalizzato**                | Migliora la qualità delle texture a distanza. |
| **Threaded Optimisation**                 | **Auto**                          | Rileva automaticamente il numero di core della CPU e li usa per gestire i thread. |
| **Preferred Refresh Rate**                | **Highest Available**             | Assicurati che la frequenza di aggiornamento dello schermo sia la più alta possibile. |
| **Multi-Frame Sampled AA (MFAA)**         | **Attiva**                        | Ottimizza l'antialiasing per migliorare la qualità visiva senza perdere troppi FPS. |
| **OpenGL GDI Compatibility**              | **Auto**                          | Lascia l'opzione su "Auto" per una migliore compatibilità grafica. |
| **Change ECC State**                      | **Disattivato**                   | Usato solo su GPU professionali, disattivato è sufficiente per gli utenti comuni. |

> ✨ **Suggerimento:** Puoi resettare tutte le impostazioni globali cliccando su **Restore Defaults**.  

---

## 📺 **4. Configurazioni Schermo**  

### 🔥 **Configure Surround, PhysX**  
- **PhysX Processor**: Imposta su **Auto-Select**.  
- **Surround**: Togli il flag su **Span Displays with Surround** (a meno che non utilizzi più schermi).  

---

### 📏 **Change Resolution**  
- Imposta la risoluzione **nativa** dello schermo.  
- Imposta il refresh rate massimo (Hz) supportato dal monitor.  

---

### 🎉 **Adjust Desktop Colour Settings**  
- Aumenta la **Digital Vibrance** al **+75%** per ottenere colori più vivaci e brillanti.  

---

### 🖼️ **Adjust Desktop Size and Position**  
- Seleziona **Full Screen** per la modalità di scaling.  
- **Perform scaling on**: Imposta su **GPU** per una migliore qualità dello scaling.  

---

## 🕹️ **5. Configurazioni NVIDIA APP**  

Le impostazioni elencate sopra possono essere replicate anche su **NVIDIA APP**:  
1. Apri **NVIDIA APP**.  
2. Vai su **Graphics** → **Global Settings**.  
3. Imposta le stesse configurazioni descritte nella sezione **3D Settings**.  

---

## 📋 **Riepilogo delle Impostazioni Essenziali**  

| **Funzione**                  | **Stato**         | **Motivazione**                            |
|-------------------------------|------------------|-------------------------------------------|
| **Image Scaling**               | ❌ Disattiva     | Se hai DLSS, meglio usarlo.               |
| **DLSS**                        | ✅ Attiva       | Migliore qualità e prestazioni.           |
| **Low Latency Mode**            | ✅ Attiva       | Migliora la reattività.                   |
| **G-Sync**                      | ✅ Attiva       | Evita tearing dello schermo.              |
| **Preferred Refresh Rate**      | ✅ Massimo      | Maggiore fluidità visiva.                 |
| **Digital Vibrance**            | 🔥 +75%         | Colori più vivaci.                        |

---

## 📣 **Consigli Finali**  
- Mantieni i **driver aggiornati** con NVIDIA APP.  
- Sperimenta le configurazioni e monitora FPS e temperature.  
- Se noti lag o scatti, prova a disattivare **Antialiasing**, **DSR** e **Ambient Occlusion**.  
- Se hai una GPU recente, usa **DLSS** invece di **Image Scaling**.  

Con queste impostazioni, puoi ottenere un mix di qualità grafica e FPS elevati. Adatta le impostazioni in base al tipo di utilizzo 
(gaming, editing video o uso quotidiano) per ottenere la miglior esperienza possibile.  

---
