# Analyse de Survie en Oncologie — Cancer du poumon

## Description

Ce projet présente une analyse de survie complète sur des données de cancer du poumon avancé (cohorte NCCTG, 228 patients), réalisée en R. Il couvre l'ensemble du workflow biostatistique classique en oncologie, de l'exploration descriptive à la modélisation multivariée.

## Méthodes

- **Tableau descriptif** (Table 1) avec comparaison par sexe
- **Courbes de Kaplan-Meier** avec tests du log-rank (survie globale, par sexe, par score ECOG, par groupe d'âge)
- **Modèle de Cox** univarié et multivarié avec estimation des Hazard Ratios
- **Forest plot** des Hazard Ratios ajustés
- **Vérification de l'hypothèse de proportionnalité** des risques (résidus de Schoenfeld)

## Données

Le jeu de données `lung` est inclus dans le package R `survival`. Il provient du North Central Cancer Treatment Group (NCCTG) et contient 228 patients atteints de cancer du poumon avancé.

Variables principales :
| Variable | Description |
|----------|-------------|
| `time` | Temps de survie (jours) |
| `status` | Statut vital (1 = censuré, 2 = décédé) |
| `age` | Âge au diagnostic |
| `sex` | Sexe (1 = Homme, 2 = Femme) |
| `ph.ecog` | Score de performance ECOG (0–4) |
| `wt.loss` | Perte de poids dans les 6 derniers mois |

Source : Loprinzi CL et al. *Journal of Clinical Oncology*, 1994.

## Structure du projet

```
survival_project/
├── R/
│   └── 01_survival_analysis.R    # Script principal
├── output/                        # Figures générées
│   ├── 01_km_global.png
│   ├── 02_km_sexe.png
│   ├── 03_km_ecog.png
│   ├── 04_km_age.png
│   ├── 05_forest_plot.png
│   └── 06_schoenfeld_residuals.png
├── docs/
│   └── guide_github.md           # Guide pour publier sur GitHub
└── README.md
```

## Résultats principaux

1. La survie médiane globale est de **310 jours**.
2. Les **femmes** ont une survie significativement meilleure que les hommes.
3. Le **score ECOG** est le facteur pronostique le plus fort : les patients avec un ECOG élevé ont un risque de décès significativement accru.
4. Dans le modèle de Cox multivarié, le sexe et le score ECOG restent des **prédicteurs indépendants** après ajustement.
5. L'hypothèse de **proportionnalité des risques** est respectée.

## Packages R utilisés

- `survival` — modèles de survie
- `survminer` — visualisation des courbes de Kaplan-Meier
- `gtsummary` — tableaux descriptifs et de régression
- `dplyr`, `tidyr` — manipulation de données
- `ggplot2` — visualisation
- `broom` — extraction des résultats de modèles

## Comment exécuter

```r
# Depuis le dossier du projet
source("R/01_survival_analysis.R")
# Les figures sont sauvegardées dans output/
```

## Auteur

**Killian Foubert, Ph.D.**
Statisticien | Économiste quantitatif
- PhD en Économie (Ghent University / UNU-CRIS)
- 3 publications en revues internationales à comité de lecture
- Expérience en analyse de données de santé (27 000 dossiers patients, EUSTAR/CHU Bordeaux)

## Licence

Ce projet est sous licence MIT. Les données proviennent du package R `survival` et sont librement disponibles.
