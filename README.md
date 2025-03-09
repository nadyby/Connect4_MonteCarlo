# Comparaison d'algorithmes Monte Carlo dans le jeu Puissance 4

## Introduction
Ce projet vise à comparer plusieurs algorithmes d'apprentissage par renforcement basés sur les méthodes de Monte Carlo dans le contexte du jeu de Puissance 4. Nous avons implémenté et évalué les algorithmes suivants :

- **Monte Carlo Tree Search (MCTS) standard**
- **UCB1-Tuned Search**
- **Rapid Action Value Estimation (RAVE)**
- **Nested Rollout Policy Adaptation (NRPA)**

Notre objectif est d'évaluer les performances relatives de ces algorithmes, leur capacité à exploiter l'avantage du premier joueur, et leur efficacité computationnelle.

## Contenu du projet

- `connect4_MCTS_UCB.ipynb` : Implémentation du jeu Puissance 4 et des algorithmes MCTS et UCB1-Tuned
- `connect4_rave.ipynb` : Implémentation de l'algorithme RAVE et comparaison avec MCTS
- `connect4_NRPA.ipynb` : Implémentation de l'algorithme NRPA et comparaison avec MCTS

## Fonctionnalités


- **Implémentation complète du jeu Puissance 4**
- **Algorithmes d'IA implémentés :**
  - **MCTS standard** : Utilisant la formule UCB1 classique pour équilibrer l'exploration et l'exploitation
  - **UCB1-Tuned** : Amélioration de MCTS intégrant une estimation de la variance des récompenses
  - **RAVE** : Amélioration de MCTS utilisant l'information "all-moves-as-first" pour accélérer l'apprentissage
  - **NRPA** : Algorithme récursif qui adapte progressivement une politique basée sur les résultats des simulations
- **Simulation de parties entre différents algorithmes**
- **Analyse statistique des performances**
- **Visualisation des résultats** (taux de victoire, avantage du premier joueur)
- **Mesure et comparaison des temps d'exécution**


## Résultats principaux
Nos expériences ont montré que :

- **UCB1-Tuned surpasse légèrement MCTS** avec un taux de victoire d'environ 54% contre 45%
- **MCTS surpasse largement RAVE** avec 73-81% de victoires selon le paramétrage de RAVE
- **MCTS domine complètement NRPA** avec 95-100% de victoires selon le niveau de récursion de NRPA
- **L'avantage du premier joueur est significatif**, avec environ 68-77% de victoires pour le joueur Rouge (premier)
- **Les matchs nuls sont relativement rares** (environ 1% des parties)
- **RAVE présente des performances variables** selon le paramètre k, obtenant de meilleurs résultats avec k=500 (27% de victoires) qu'avec k=100 (19% de victoires)
- **NRPA montre une explosion du temps de calcul** avec l'augmentation du niveau de récursion (de 24ms à 35s par coup)

## Installation et utilisation

### Prérequis

- Python 3.10+
- NumPy
- Matplotlib
- Pandas (pour l'analyse des données)

### Installation
```bash
git clone https://github.com/nadyby/Connect4_MonteCarlo
cd Connect4_MonteCarlo
pip install -r requirements.txt
```

### Utilisation

Pour exécuter une simulation de 100 parties entre MCTS et UCB1-Tuned :
```python
from connect4_MCTS_UCB import Connect4Game, MCTS, UCB1TunedSearch, run_simulation

run_simulation(100)
```

Pour comparer MCTS et RAVE :
```python
from connect4_rave import Connect4Game, MCTS, RAVE, run_simulation_mcts_vs_rave

run_simulation_mcts_vs_rave(100)
```

```python

from connect4_NRPA import Connect4Game, MCTS, NRPA, test_algorithms

test_algorithms(num_games=20, mcts_iterations=1000, nrpa_level=2, nrpa_iterations=20)
```

## Paramètres principaux

- **Nombre d'itérations** : Par défaut fixé à 1000 (ou 2000 pour certaines expériences)
- **Constante d'exploration UCB** : 1.41 (valeur théorique optimale √2)
- **Paramètre `k` de RAVE** : Contrôle l'équilibre entre statistiques MCTS et AMAF (valeurs testées : 500 et 100)
- **Niveau de récursion NRPA** : Détermine la profondeur de récursion (valeurs testées : 1 et 2)
- **Nombre d'itérations NRPA** : Contrôle le nombre de simulations par niveau (valeurs testées : 10 et 20)
- **Taux d'apprentissage NRPA** : Fixé à 0.5 pour l'adaptation de la politique


## Contributeurs

Nadia BEN YOUSSEF
Jihed BHAR
Yassine BEN ABDALLAH

## Licence
MIT
