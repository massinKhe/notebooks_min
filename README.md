# Modélisation des Résultats d'Arsenal (notebooks_min)

Ce dossier contient un notebook autonome pour charger les données scrappées, préparer un dataset, entraîner Random Forest et XGBoost, et produire des visualisations et métriques utiles pour un portfolio data science.

## Contenu
- `Arsenal_Predictions_Minimal.ipynb` : notebook principal (code + explications + visualisations)
- `Arsenal_Predictions_Minimal_executed.ipynb` : version exécutée avec sorties intégrées (lecture immédiate sur GitHub)
- `data/` : CSV utilisés par le notebook (copie des scrapes)

## Données
Placez trois fichiers CSV dans `notebooks_min/data/` (déjà fournis si vous avez copié depuis `data/raw/`) :
- `understat_arsenal_matches.csv`
- `fbref_arsenal_match_stats.csv`
- `fbref_arsenal_team_stats.csv`

Astuce: si le repo doit rester léger, gardez un échantillon (`sample_*.csv`) et documentez le chemin pour regénérer les données complètes.

## Installation
```bash
python -m venv .venv
.venv\Scripts\activate    # Windows
# source .venv/bin/activate # macOS/Linux
pip install -r notebooks_min/requirements.txt
```

## Exécution
- Option 1 (Jupyter Lab/Notebook) :
```bash
jupyter notebook notebooks_min/Arsenal_Predictions_Minimal.ipynb
# ou
jupyter lab
```
Puis "Run All" depuis le menu.

- Option 2 (non interactif, export notebook exécuté) :
```bash
python -m jupyter nbconvert \
  --to notebook \
  --execute notebooks_min/Arsenal_Predictions_Minimal.ipynb \
  --output Arsenal_Predictions_Minimal_executed.ipynb \
  --output-dir notebooks_min \
  --ExecutePreprocessor.timeout=1200
```

## Notes
- Le notebook inclut : préparation des données, features, cross-validation, courbes ROC (One-vs-Rest), learning curves, importances RF vs XGB, EDA ciblée et conclusions.
- Si l’alignement Understat/FBref n’est pas possible pour certains matchs, le pipeline s’adapte (fallback) afin de rester reproductible.
