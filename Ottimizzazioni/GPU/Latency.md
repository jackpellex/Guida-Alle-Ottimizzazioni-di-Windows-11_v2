
# Problema della Latenza dei Frame nei Videogiochi

## Cos'è la latenza dei frame?

Nel contesto dei videogiochi, la latenza dei frame si riferisce al ritardo che può verificarsi tra il rendering e 
la visualizzazione di un frame sullo schermo. Questo fenomeno si verifica quando i frame non vengono visualizzati a 
intervalli regolari, creando un'esperienza di gioco che può sembrare meno fluida, nonostante il gioco stia girando a un buon numero di FPS (Frames Per Second). 

Ad esempio, in un gioco che gira a 110 FPS, potrebbe sembrare che ci sia un "lag" o che il movimento non sia fluido come dovrebbe essere. 
Questo accade quando i frame non sono visualizzati in modo stabile: ad esempio, un frame potrebbe apparire dopo solo 11 millisecondi, 
mentre il successivo potrebbe impiegare 50 millisecondi. Questa variazione tra i frame genera un'esperienza visiva non stabile, che può risultare fastidiosa durante il gioco.

## Il ruolo della latenza e dei bottleneck

La latenza dei frame può essere influenzata anche dalla presenza di un bottleneck tra la CPU e la GPU. Idealmente, 
la GPU dovrebbe essere utilizzata al massimo delle sue capacità, mentre la CPU dovrebbe rimanere a un livello di utilizzo più basso. 
Tuttavia, quando la CPU è sotto sforzo e non riesce a tenere il passo con la GPU, la latenza aumenta e la fluidità del gioco ne risente.

## Soluzioni per ridurre la latenza

Un metodo per ridurre la latenza dei frame è limitare il numero di FPS. Ad esempio, se un gioco a impostazioni ultra raggiunge 110 FPS, 
potrebbe essere utile limitare i frame a 90 o 75 FPS. In questo modo si ottengono diversi benefici:

- Riduzione del carico sulla CPU e sulla GPU, che verranno meno stressate e riscaldate.
- Maggiore stabilità nella latenza, con una migliore esperienza visiva e meno "lag".

Questa tecnica è utilizzata anche dalle console moderne (PS5, Xbox, Nintendo Switch), che limitano i giochi a 60 o 45 FPS 
per garantire una latenza stabile, nonostante il limite imposto dalla CPU.

## Monitoraggio della latenza e delle risorse di sistema

Per verificare la presenza di problemi di latenza e ottimizzare la tua esperienza di gioco, puoi utilizzare strumenti che 
ti forniscono statistiche dettagliate sulle prestazioni del sistema. Alcuni strumenti consigliati includono:

- **RTSS - RivaTuner Statistics Server**: [Link al download](https://www.guru3d.com/download/rtss-rivatuner-statistics-server-download)
- **MSI AfterBurner**: [Link al download](https://www.msi.com/Landing/afterburner/graphics-cards)

Con questi strumenti, dovrai concentrarti su queste informazioni:

- **Utilizzo CPU**: Verifica se la CPU è sotto sforzo.
- **Utilizzo GPU**: Assicurati che la GPU non sia sovraccarica.
- **FPS**: Controlla che il numero di FPS sia stabile.
- **FrameTime**: Misura il tempo necessario per elaborare un frame.
- **Latency**: Controlla la latenza tra i frame.
- **Temperature**: Mantieni la temperatura della GPU e CPU sotto gli 80 gradi, evitando di superare i 85 gradi per prevenire danni ai componenti.
