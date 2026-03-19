Python version 3.14.2

# Hur man kör projektet

1. Klona repot:
```bash```
git clone <https://github.com/JakobWorkingHard/ML-Gruppuppgift.git>

- Syfte:
Projektet styftar till att bygga en beslutsstödsmodell för Trust & Safety-teamet på en marknadsplats-app. 
Modellen ska prioritera misstänkta annonser och meddelanden för manuell granskning.

cd ML-Gruppuppgift

2. Installera nödvändiga bibliotek som pandas, numpy, scikit-learn, matplotlib, seaborn, scikit-learn.
pip install -r requirements.txt
3. Öppna notebooken:
Final_Report.ipynb
4. Kör notebooken från början:
Restart & Run All

**Notebooken innehåller hela workflowet:**
- EDA
- preprocessing
- modellträning
- modelljämförelse
- hyperparameter-optimering

# Kravkort

- Stakeholder: Maja, Head of Trust & Safety.
-Prioritet: Maximera recall (fånga så många misstänkta fall som möjligt).

Top-X prioritering
**Trust & Safety — “Vi får inte missa de värsta”**
Head of Trust & Safety Maja har suttit med när en användare blivit lurad och polisanmält. Hon är inte intresserad av att “optimera en siffra”, hon vill se att ni fångar farliga fall och att ni har tänkt igenom konsekvenserna när något missas. Hon accepterar att teamet får titta på fler fall om det innebär att de riktigt riskabla inte glider igenom. Det viktigaste för henne är att lösningen känns som en trygghetsfunktion – inte som ett experiment.

Det viktigaste är att inte missa de värsta fallen. Det innebär att modellen bör prioritera att hitta så många verkligt misstänkta aktiviteter som möjligt, även om det innebär att vissa normala fall flaggas för granskning.

Modellen ska därför fungera som ett trygghetsverktyg som hjälper teamet att identifiera riskabla aktiviteter tidigt.

# Vår strategi

Vi behandlade problemet som en binär klassificering där målet är att förutsäga om en aktivitet är misstänkt eller inte.
Vi började med en explorativ dataanalys (EDA) för att förstå datasetet, identifiera saknade värden och undersöka feature-fördelningar.
Därefter skapade vi en preprocessing pipeline som hanterar numeriska och kategoriska variabler separat (imputation, scaling och encoding).
Vi jämförde flera modeller (DummyClassifier, Logistic Regression och Random Forest) med hjälp av stratified cross-validation.
Eftersom vårt kravkort prioriterar att fånga misstänkta fall valde vi att optimera modellen för recall, vilket minimerar False Negatives.
Slutligen implementerade vi en Top-X prioriteringsstrategi, där Trust & Safety-teamet granskar de aktiviteter som modellen bedömer som mest riskabla först.

# Ansvarsfördelning
| Person   | Ansvar                                                                                            |
| -------- | ------------------------------------------------------------------------------------------------- |
| Jacob    | Data & EDA - analys av dataset, visualiseringar och insikter                                      |
| Katarina | Pipeline & preprocessing - hantering av numeriska/kategoriska features och leakage-säker pipeline |
| Miralem  | Modelljämförelse - baseline, modellträning och cross-validation                                   |
| Marziyeh | Hyperparameter-optimering - tuning av vald modell                                                 |
| Katarina | Threshold/prioritering - Top-X strategi och analys av trade-offs  
| Irfan    | Risk & Pitch                       |
| Alla     | Testar new_data och fixar buggar                                                                  |
| Alla     | Presentation - sammanställning av resultat, rekommendationer                 |
