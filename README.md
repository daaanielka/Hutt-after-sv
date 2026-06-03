# HUTT Decision Support

Streamlit aplikácia pre predikciu výsledku Head-Up Tilt Testu (HUTT) z klinických údajov dostupných pred vyšetrením.

🔗 **Live demo:** [hutt-predictor.streamlit.app](https://hutt-predictor.streamlit.app)

---

## Popis

Aplikácia porovnáva dva predikčné modely postavené na algoritme Extra Trees, trénované na datasete 351 pacientov z VÚSCH Košice:

| Model | Vstup | AUC |
|-------|-------|-----|
| P1 | Pohlavie, vek, TK, pulz | 78,9 % |
| P3 | P1 + dotazníkové údaje (13 premenných) | 81,7 % |

Výber atribútov bol realizovaný pomocou ConsensusFeatureSelector (kombinácia Chi², Random Forest importance a RFE) vnútri 5-fold stratifikovanej krížovej validácie.

---

## Spustenie lokálne

```bash
pip install -r requirements.txt
streamlit run app.py
```

---

## Štruktúra projektu

```
├── app.py                  # Streamlit aplikácia
├── analyza.py              # Trénovanie modelov a ConsensusFS
├── eda.py                  # Exploratórna analýza dát
├── validacia.py            # Kalibrácia, SHAP, DCA, fairness
├── model_components.py     # ConsensusFeatureSelector
├── requirements.txt
├── data/                   # Vstupné dáta a výstupy analýz (.csv, .xlsx)
├── models/                 # Natrénované modely (.joblib)
└── outputs/                # Grafy a vizualizácie (.png)
```

---

## Upozornenie

Výskumný prototyp. Výstup nie je klinicky validovaný diagnostický nástroj a nenahrádza odborné posúdenie lekára. Modely boli validované iba interne na jednocentrovom retrospektívnom datasete.

---

## Autor

Bakalárska práca · FEI TUKE · 2026  
Daniela Pracková
