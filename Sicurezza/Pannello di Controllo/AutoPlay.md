# Problema di Sicurezza: Disattivare AutoPlay per Proteggersi dagli Attacchi USB

## 📚 **Contesto**
Le chiavette USB rappresentano uno dei principali vettori di attacco nel mondo informatico. 
Come dimostrato nel video esperimento sociale del canale YouTube **nFire** intitolato *"Ho hackerato 100 persone con una chiavetta USB"* 
([Guarda il video](https://www.youtube.com/watch?v=CV8rr7hED2Q)), molte persone sottovalutano i rischi associati all'utilizzo di dispositivi USB sconosciuti.

## ⚠️ **Il Pericolo delle Chiavette USB**
- Le chiavette USB con un **chip di controllo riprogrammabile** possono essere trasformate in dispositivi pericolosi.
- Una USB può funzionare come un dispositivo HID (**Human Interface Device**), simulando una tastiera che invia comandi malevoli al sistema.
- In alcuni casi, può agire come una *backdoor*, consentendo accessi non autorizzati al sistema.

## 🔒 **Come Mitigare il Rischio: Disattivare AutoPlay**
AutoPlay è una funzionalità di Windows che permette di eseguire automaticamente il contenuto di un dispositivo esterno appena collegato. 
Questa funzione rappresenta un rischio significativo.

### **Passaggi per Disattivare AutoPlay:**
1. Aprire il **Pannello di Controllo**.
2. Navigare su **Hardware e suoni > AutoPlay**.
3. Disattivare l'opzione **"Usa AutoPlay per tutti i supporti e tutti i dispositivi"**.
4. Salvare le modifiche.

### **Perché è importante?**
- Blocca l'esecuzione automatica di script malevoli presenti su dispositivi USB.
- Impedisce a dispositivi HID compromessi di eseguire comandi senza l'intervento dell'utente.

## 🛡️ **Ulteriori Misure di Sicurezza**
- Non collegare mai dispositivi USB di origine sconosciuta.
- Utilizzare soluzioni di sicurezza avanzate che monitorano i dispositivi USB.
- Abilitare policy di sicurezza specifiche tramite **Criteri di gruppo** su Windows.

## 🎯 **Conclusione**
La disattivazione di AutoPlay è un primo passo fondamentale per proteggere il proprio sistema da attacchi basati su dispositivi USB. 
La prudenza e la consapevolezza giocano un ruolo cruciale nella sicurezza informatica.