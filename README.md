# Traveling_Salesman_Problem

[![Notebook](https://img.shields.io/badge/type-Jupyter%20Notebook-orange)]()
[![Langage](https://img.shields.io/badge/langage-Python-blue)]()
[![Licence](https://img.shields.io/badge/licence-%C3%A0%20pr%C3%A9ciser-lightgrey)]()

Collection de notebooks et ressources pour l'étude du Problème du Voyageur de Commerce (TSP). Ce dépôt contient :
- des notebooks Jupyter présentant des formulations linéaires et des heuristiques (Clark & Wright),
- des instances d'exemple,
- un rapport PDF décrivant la démarche et les résultats.

Résumé
-------
Ce dépôt sert à comparer et expérimenter différentes approches pour le TSP : formulation linéaire (résolue par un solveur) et heuristiques basées sur Clarke‑Wright. Les notebooks montrent la modélisation, l'implémentation, les résultats et les visualisations.

Contenu du dépôt
----------------
- Algo_formulation_lineaire_Chemanack_Glandier.ipynb  
  Notebook expliquant la formulation linéaire du problème (variables, contraintes, fonction objectif) et son exécution via un solveur.
- Algo_with_Clark_Wright_Chemanack_Glandier.ipynb  
  Notebook implémentant l'heuristique Clarke‑Wright (regroupement d'arcs / fusion de routes) avec visualisations et comparaisons.
- instance.txt, minstance.txt, tinstance.txt  
  Fichiers d'instances (format texte) utilisés pour tester les algorithmes.
- Rapport_Projet_TOP.pdf  
  Rapport du projet (méthodologie, tests, comparaisons et conclusions).
- README.md (existant) — ce fichier (mis à jour).
  
Prérequis
---------
Recommandé :
- Python 3.8+
- Jupyter Notebook / JupyterLab
- Un solveur linéaire pour la formulation (exemples ci‑dessous)
- git

Dépendances usuelles (suggestion)
- numpy, scipy
- pandas
- matplotlib, seaborn
- networkx (pour graphes et visualisations)
- jupyter, ipykernel
- pulp (ou ortools) / pyomo, ou interface vers un solveur professionnel (CPLEX, Gurobi) si disponible

Exemple d'installation (venv)
```bash
git clone https://github.com/thierrykmr/Traveling_Salesman_Problem.git
cd Traveling_Salesman_Problem

python -m venv .venv
# macOS / Linux
source .venv/bin/activate
# Windows (PowerShell)
.venv\Scripts\Activate.ps1

pip install --upgrade pip
pip install jupyter numpy scipy pandas matplotlib seaborn networkx pulp ortools
```

Remarque : si tu fournis un requirements.txt, installe-le via `pip install -r requirements.txt`.

Comment reproduire les notebooks
-------------------------------
1. Lancer Jupyter :
```bash
jupyter lab
# ou
jupyter notebook
```
2. Ouvrir et exécuter les notebooks :
- Algo_with_Clark_Wright_Chemanack_Glandier.ipynb — parcours interactif de l'heuristique et visualisations.
- Algo_formulation_lineaire_Chemanack_Glandier.ipynb — génération du modèle linéaire et résolution (peut nécessiter un solveur externe).

Exécution non‑interactive (batch)
```bash
jupyter nbconvert --to notebook --execute "Algo_with_Clark_Wright_Chemanack_Glandier.ipynb" --output executed_clark_wright.ipynb
jupyter nbconvert --to notebook --execute "Algo_formulation_lineaire_Chemanack_Glandier.ipynb" --output executed_formulation.ipynb
```

Solveurs recommandés pour la formulation linéaire
-------------------------------------------------
- pulp (open source, interface utile) — par défaut résout avec CBC inclus.
- OR‑Tools (Google) — performant pour certains types de problèmes combinatoires.
- Si tu as accès à des solveurs commerciaux : Gurobi ou CPLEX donnent souvent de meilleures performances sur les instances de taille moyenne/grande.

Exemple d'utilisation avec PuLP (dans un script ou le notebook)
```python
import pulp
# définir problème : pulp.LpProblem(...)
# variables : pulp.LpVariable.dicts(...)
# ajouter contraintes et fonction objectif
# résoudre : prob.solve(pulp.PULP_CBC_CMD())
```

Fichiers d'instances
--------------------
- `instance.txt`, `minstance.txt`, `tinstance.txt` : formats texte contenant les points/distances. Vérifie en ouvrant ces fichiers pour connaître le format exact (coordonnées euclidiennes, matrice de distances, etc.). Les notebooks montrent comment parser ces fichiers.

Résultats et rapport
--------------------
Consulte `Rapport_Projet_TOP.pdf` pour :
- la description détaillée des méthodes,
- les expériences et comparaisons (coût, temps),
- les conclusions et recommandations.

Bonnes pratiques et suggestions
-------------------------------
- Si tu commets les notebooks, enlève les outputs volumineux avant commit (outil : nbstripout), afin de garder l'historique léger.
- Extraire le code réutilisable des notebooks vers des modules Python (`src/` ou `scripts/`) facilite le test et la réutilisation.
- Si tu veux automatiser les expériences, utilise papermill pour paramétrer et exécuter les notebooks sur plusieurs instances.

Propositions d'amélioration du dépôt
------------------------------------
- Ajouter un fichier `requirements.txt` avec versions précises.
- Ajouter un petit script `run_all.sh` pour lancer les notebooks batch et générer les rapports/plots.
- Documenter le format exact des fichiers d'instance dans un `DATA.md` ou dans le README.
- Ajouter une licence (`LICENSE`) si tu veux autoriser explicitement la réutilisation.

Licence
-------

Auteurs & contact
-----------------
- Thierry — @thierrykmr

Remarques finales
-----------------
J'ai parcouru les notebooks et les fichiers d'instances listés dans le dépôt pour rédiger ce README. Si tu veux, je peux ensuite :
- extraire automatiquement les imports depuis les notebooks pour générer un `requirements.txt`,
- ajouter un `DATA.md` décrivant le format exact des instances (si tu me fournis un échantillon ou autorises l'analyse du contenu des fichiers d'instances),
- ou produire un script `run_all.sh`/`Makefile` pour automatiser l'exécution des notebooks.
