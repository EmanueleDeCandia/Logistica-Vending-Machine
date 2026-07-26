# 🚛 Simulatore Logistica Distributori Automatici

Simulazione parametrica e analisi multi-scenario della logistica per la gestione di una rete di distributori automatici (vending machines). Questo progetto fornisce una toolkit completa per ottimizzare i costi operativi e le strategie di distribuzione.

## 📋 Panoramica

Il simulatore analizza i costi logistici annuali per una rete di distributori automatici, considerando:

- **Costi Variabili**: Carburante, manutenzione, svalutazione dei veicoli
- **Costi Fissi**: Ammortamento della flotta
- **Costi del Personale**: Stipendi, contributi, straordinari
- **Ottimizzazione dei Percorsi**: Riduzione chilometrica tramite software GPS
- **Analisi di Sensibilità**: Impatto di variabili critiche sui costi

---

## 📊 Contenuti del Notebook

### 1. **Simulatore Logistica Base**
Blocco indipendente che calcola i costi logistici totali senza considerare il costo del personale.

**Parametri principali:**
- Numero distributori: 12.000
- Chilometraggio medio mensile per distributore: 30 km
- Costo variabile per km: €0.50/km
- Capacità annuale furgone: 30.000 km

**Output:**
- Chilometraggio totale annuale
- Numero furgoni necessari
- Costo totale logistica (escluso personale)

---

### 2. **Analisi di Sensibilità: Numero Distributori**
Visualizza come il numero di distributori influenza i costi totali e il costo per singolo distributore.

**Range di simulazione:**
- Da 100 a 13.000 distributori
- Incremento: 100 unità

**KPI Principali:**
- Costo totale rete (aumenta linearmente)
- Costo per distributore (tende a stabilizzarsi - economie di scala)

**Insight:**
L'aumento dei distributori riduce il costo per singolo punto, evidenziando economie di scala significative nei costi fissi.

---

### 3. **Ripartizione Attività Logistiche**
Grafici che mostrano:
- **Pie Chart**: Ripartizione chilometrica tra rifornimento (75%) e assistenza (25%)
- **Bar Chart**: Confronto tra costi fissi e costi variabili

---

### 4. **Analisi di Sensibilità: Chilometri Medi Mensili**
Analizza l'impatto dei chilometri medi per distributore sui costi logistici.

**Range di simulazione:**
- Da 5 a 50 km mensili per distributore
- Incremento: 5 km

**Risultati:**
- Relazione lineare tra km e costi totali
- Effetto diretto sul numero di furgoni necessari e sulle ore di lavoro

---

### 5. **Confronto Scenario: Flotta Vecchia vs. Flotta Nuova**
Comparazione economica tra due tipologie di veicoli:

| Parametro | Furgoni Vecchi | Furgone Nuovi |
|-----------|-------------|-------------------|
| Carburante | €0.25/km | €0.15/km |
| Manutenzione | €0.15/km | €0.05/km |
| Svalutazione | €0.03/km | €0.10/km |
| **Costo Totale** | **€1.239.400** | **€865.000** |

**Conclusione:** Il furgone nuovo riduce i costi del **~30%** rispetto all'auto vecchia.

---

### 6. **Simulatore Logistico Avanzato con Ottimizzazione**
Modello evoluto che include il costo del personale e l'ottimizzazione dei percorsi.

**Nuove variabili:**
- **Costo orario personale**: €25.00/ora
- **Velocità media urbana**: 25 km/h
- **Tempo totale intervento**: 2 ore/anno per distributore
- **Efficienza percorsi**: 90% (riduzione del 10% dei km tramite GPS)

**Output KPI:**
- Km dopo ottimizzazione: 2.592.000 km
- Costo del personale: €3.192.000 (l'80% dei costi totali)
- **Costo totale logistica**: €3.970.600
- **Costo medio per distributore**: €330.88

**Grafico dei Costi:**
Visualizza l'incidenza reale di:
- Ammortamento mezzi (2,5%)
- Carburante/Manutenzione (20%)
- Personale (77,5%)

---

### 7. **Analisi della Frequenza di Visita**
Studio sull'impatto della frequenza di rifornimento sui costi per distributore.

**Range di simulazione:**
- Da 1 a 10 visite mensili per distributore

**Insights:**
- Frequenza ridotta = costi inferiori ma rischio di esaurimento scorte
- Frequenza elevata = costi superiori ma migliore disponibilità di prodotto
- Identificazione del punto di equilibrio economico

---

## 🎯 KPI Principali

| Metrica | Valore | Unità |
|---------|--------|-------|
| Numero Distributori | 12.000 | pz |
| Chilometraggio Annuale | 2.880.000 | km |
| Costo del Personale | 3.192.000 | € |
| Costo Totale (con personale) | 3.970.600 | € |
| **Costo per Distributore** | **330,88** | €/anno |

---

## 📈 Come Usare il Simulatore

### Prerequisiti
```bash
pip install numpy matplotlib pandas jupyter
```

### Esecuzione
```bash
jupyter notebook simulazione_scenari_logistica_distributori.ipynb
```

### Personalizzazione
Modifica i parametri nelle celle di input:

```python
NUM_DISTRIBUTORI = 12000  # Numero distributori
KM_MEDI_PER_DISTRIBUTORE_MESE = 20  # Km medi mensili
COSTO_ORARIO_PERSONALE = 25.0  # €/ora
EFFICIENZA_PERCORSI = 0.9  # 90% = riduzione 10% km
VELOCITA_MEDIA_URBANA = 25.0  # km/h
```

---

## 💡 Caso d'Uso: Optimizzazione Strategica

Il simulatore può supportare decisioni come:

1. **Numero ottimale di distributori** per minimizzare il costo per punto
2. **Frequenza di visita ideale** bilanciando costi e disponibilità prodotto
3. **Valutazione upgrade flotta** (confronto auto vecchia vs. furgone nuovo)
4. **Investimento in software GPS** per ridurre i chilometri (+ROI del 10%)
5. **Stratificazione rete** (distributori alta/bassa rotazione con frequenze diverse)

---

## 📊 Interpretazione dei Risultati

### Economie di Scala
L'aumento da 100 a 12.000 distributori prima riduce i costi poi li aumenta grazie in quando la riduzione dei costi fissi ha forti vincoli nel personale necessario per la copertura del servizio. Diverso per i costi per singolo OCS: si riducono quando la concentrazione è determinata da un maggior numero di macchine OCS per cliente.

### Incidenza del Personale
Con l'inclusione del costo orario, **il personale rappresenta il 77,5%** del costo totale logistica. Le azioni di ottimizzazione dovrebbero prioritizzare:
- Riduzione tempo per intervento
- Ottimizzazione percorsi (GPS + AI routing)
- Maggiore efficienza nelle visite

### Sensibilità ai Chilometri
Ogni aumento di 1 km medio mensile per distributore genera ~€1.728 di costo addizionale annuale per la rete.

---

## 🔧 Variabili di Input Critiche

| Variabile | Intervallo Suggerito | Impatto |
|-----------|---------------------|--------|
| NUM_DISTRIBUTORI | 100 - 15.000 | Alto |
| KM_MEDI_PER_DISTRIBUTORE | 10 - 50 km | Alto |
| COSTO_ORARIO_PERSONALE | €15 - €35 | Critico |
| EFFICIENZA_PERCORSI | 0.80 - 0.95 | Medio |
| VELOCITA_MEDIA_URBANA | 15 - 30 km/h | Basso |

---

## 📋 Note di Implementazione

### Blocchi Autonomi
I blocchi di simulazione sono **indipendenti** e possono essere eseguiti in qualsiasi ordine. Ogni blocco ridefinisce localmente le variabili necessarie per garantire coerenza.

### Conversione Formato Numerico
Il codice utilizza formattazione numerica italiana (virgola decimale, punto come separatore di migliaia) per migliorare la leggibilità nei rapporti.

### Costo Ammortamento Furgone
Attualmente impostato a €1.000 annuali. Verificare con i dati aziendali per precisione (può incluedere solo ammortamento capitale oppure anche assicurazione e tasse).

---

## 🎓 Prossimi Passi per Migliorare il Modello

1. **Capacità di Carico**: Quanti distributori per giro? → Determina numero di mezzi reale
2. **Frequenza Dinamica**: Distributori "alta rotazione" vs. "bassa rotazione" con frequenze diverse
3. **Costi Previsibili**: Integrare variabilità stagionale e fluttuazioni prezzo carburante
4. **Manutenzione Predittiva**: Modellare il risparmio da guasti evitati
5. **Vincoli Geografici**: Raggruppamento per zona per ottimizzare percorsi

---

## 📝 Autore

**EmanueleDeCandia**  
Simulazione multi-parametrica della logistica per distributori automatici

---

## 📄 Licenza

Questo progetto è fornito come-è per scopi analitici e decisionali.

---

## 📞 Contatti e Domande

Per domande, suggerimenti o miglioramenti, consultare la documentazione del progetto o i commenti nel notebook.

---

**Last Updated**: Luglio 2026  
**Notebook Version**: Python 3 (Google Colab compatible)
