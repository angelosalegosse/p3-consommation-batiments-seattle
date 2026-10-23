# Anticipez les besoins en consommation de bâtiments

Projet 3 du parcours Data Scientist d'OpenClassrooms.

La ville de Seattle vise la neutralité carbone en 2050. Mesurer la consommation d'un bâtiment coûte cher. L'objectif est donc de **prédire la consommation d'énergie totale** (`SiteEnergyUse(kBtu)`) des bâtiments **non résidentiels** à partir de leur seule fiche : surface, usage, âge, quartier, nombre d'étages. C'est un problème de **régression supervisée**, entraîné sur les relevés de 2016.

> **Travail en cours.** Les notebooks 1 et 2 sont avancés, le notebook 3 (modélisation) reste à faire.

## Notebooks, à lancer dans l'ordre

| Notebook | Contenu | Lit | Écrit |
|---|---|---|---|
| `01_exploration.ipynb` | Périmètre non résidentiel, relevés fiables, choix des colonnes | `data/2016_Building_Energy_Benchmarking.csv` | `data/batiments_nettoyes.csv` |
| `02_cible.ipynb` | Choix de la cible, distribution en log10, bâtiments incohérents | `data/batiments_nettoyes.csv` | `data/batiments_cible.csv` |
| `03_modelisation.ipynb` | Feature engineering, comparaison de modèles, optimisation, interprétation | `data/batiments_cible.csv` | — |

Chaque notebook enregistre ses données dans un CSV que le suivant relit. Après une modification, il faut relancer ce notebook et les suivants.

## Traçabilité des filtres

| Étape | Avant | Après | Raison |
|---|---|---|---|
| Périmètre non résidentiel (`BuildingType`) | 3 376 | 1 668 | Les logements sont hors mission |
| Relevés fiables (`ComplianceStatus == "Compliant"`) | 1 668 | 1 548 | Qualité de la donnée |

## Lancer le projet

Il faut [uv](https://docs.astral.sh/uv/), qui installe Python 3.12 et les paquets du projet (versions figées dans `uv.lock`) :

```
uv sync
uv run jupyter lab
```

Puis ouvrir chaque notebook et faire **Run → Run All Cells**.

## Données

`data/2016_Building_Energy_Benchmarking.csv` : relevés 2016 de la ville de Seattle (3 376 bâtiments × 46 colonnes), fournis par OpenClassrooms.
