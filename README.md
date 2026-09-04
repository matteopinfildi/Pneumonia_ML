# Pneumonia_ML
Progetto di Machine Learning. Progetto accademico realizzato per il corso di Laurea Magistrale in Cybersecurity presso l'Università di Roma Tor Vergata.

## Panoramica
Questo repository contiene il codice sorgente e la relazione tecnica realizzati per il progetto dell'insegnamento di Machine Learning (A.A. 2025/2026). Il documento e il notebook forniscono una soluzione completa per la classificazione supervisionata di radiografie toraciche per la diagnosi automatizzata (Sano vs Polmonite). 

Il progetto unisce l'addestramento di reti neurali convoluzionali (CNN) in ambito medico all'applicazione di tecniche di Explainable AI, al fine di comprendere e validare le regioni dell'immagine che contribuiscono alle predizioni, superando la natura "Black Box" del modello.

## Principali Tecniche Implementate
*   **Pre-Processing e Bilanciamento:** Implementazione della strategia di *Class Weighting* per mitigare lo sbilanciamento nativo del dataset. L'analisi documenta l'applicazione di tecniche di pre-processing spaziale (Central Crop al 78% e Resizing a 224x224) per prevenire fenomeni di *Shortcut Learning* dovuti ad artefatti testuali sui bordi delle lastre.
*   **Transfer Learning e Fine-Tuning:** Adattamento dell'architettura ResNet50 al dominio clinico tramite la rimozione della testa originale e l'inserimento di una Custom Classification Head (Global Average Pooling 2D, Dense 512, Dropout 0.5). Il flusso di lavoro spiega l'addestramento in due fasi, evidenziando lo scongelamento dei layer profondi e l'uso di un Learning Rate microscopico (1e-5) per evitare il *Catastrophic Forgetting* dei pesi pregressi.
*   **Explainable AI (Grad-CAM):** Analisi dettagliata dell'interpretabilità del modello. Il documento descrive l'estrazione dei gradienti dall'ultimo strato convoluzionale e il riallineamento spaziale della heatmap sull'immagine originale croppata, confermando la coerenza diagnostica sulle opacità alveolari e individuando bias legati alla presenza di dispositivi medici.

## Strumenti Utilizzati
*   **Machine Learning & Deep Learning:** TensorFlow, Keras (ResNet50), Scikit-Learn
*   **Explainable AI:** tf-keras-vis (Grad-CAM), OpenCV, Matplotlib
*   **Ambiente di Sviluppo:** Jupyter Notebook / Google Colab (GPU)

## Contenuto del Repository
*   `Relazione_Pinfildi_ML.pdf` - Il documento completo dell'analisi, delle scelte progettuali e delle metriche di valutazione.
*   `Pneumonia_Pinfildi.ipynb` - Il codice sorgente documentato contenente la pipeline di training, validazione e inferenza con Explainable AI.

## Avvertenza
*Questo repository contiene esclusivamente il codice sorgente e la documentazione analitica. **Nessun dataset di immagini mediche o file dei pesi del modello addestrato (.keras) è stato caricato qui a causa delle dimensioni elevate.** Il dataset originale "Chest X-Ray Images (Pneumonia)" utilizzato per questo progetto è disponibile pubblicamente ed è scaricabile tramite Kaggle al seguente link: [Chest X-Ray Images (Pneumonia)](https://www.kaggle.com/datasets/paultimothymooney/chest-xray-pneumonia).*
