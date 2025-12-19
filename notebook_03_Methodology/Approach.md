# Démarche méthodologique

## Principe général

Le Stability Score ne cherche **pas** à :
- Prédire les valeurs futures
- Optimiser un processus
- Prendre des décisions automatiques

Le Stability Score cherche à **mesurer la stabilité comportementale** d'un flux dans le temps.

**Hypothèse de travail :**  
Un flux stable se comporte de façon régulière et prévisible. Quand ce comportement change, c'est un signal à investiguer.

---

## Philosophie de conception

### 1. Simplicité avant complexité

Plutôt qu'un modèle complexe difficile à interpréter, j'ai choisi une approche modulaire basée sur des composants mesurables et compréhensibles.

**Avantage :**  
- Chaque composant peut être inspecté individuellement
- Les équipes métier comprennent ce qui est mesuré
- Debugging et calibration facilités

### 2. Explicabilité avant performance

En banque, un modèle explicable à 80% de performance vaut mieux qu'une boîte noire à 95%.

**Choix technique :**  
Pas de machine learning, pas de réseaux de neurones. Uniquement des algorithmes déterministes basés sur des métriques statistiques classiques.

### 3. Détection avant prédiction

Le score ne dit pas "le flux va crasher dans 10 jours". Il dit "le flux se comporte anormalement depuis X jours".

**Avantage :**  
- Pas de fausses promesses sur le futur
- Signal actionnable : investigation humaine
- Responsabilité claire : c'est un outil d'aide à la décision

---

## Architecture du score

### Les 4 composants mesurés

Le Stability Score agrège **4 signaux indépendants**, chacun capturant un aspect différent de la stabilité :

1. **Volatility** — Mesure l'augmentation anormale du bruit dans les données
2. **Drift** — Détecte les tendances lentes et persistantes
3. **Break** — Identifie les changements locaux de régime
4. **Observability gap** — Quantifie ce qui n'est pas expliqué par le modèle

➡️ [Voir le détail de chaque composant](components.md)

### Agrégation en score unique

Les 4 composants sont normalisés et combinés pour produire un **score de 0 à 100** :

- **100** = Stabilité parfaite
- **70-100** = Comportement normal
- **40-70** = Zone de surveillance
- **0-40** = Dégradation détectée

**Calibration :**  
Les seuils et pondérations sont ajustés selon le type de flux (paiements, délais, volumes, etc.).

---

## Robustesse et tests

### Tests de chocs synthétiques

Pour valider la réactivité du score, j'ai créé 4 types de chocs artificiels sur un flux stable :

- **Rupture brutale** : changement instantané de niveau
- **Pic temporaire** : anomalie ponctuelle puis retour à la normale
- **Dérive lente** : dégradation progressive sur plusieurs semaines

**Résultat :**  
Le score réagit différemment selon le type de choc, ce qui confirme qu'il capture bien des patterns comportementaux distincts.

➡️ [Voir les résultats visuels](../03-results/case-study.md)

### Cas réel : EUR/USD BCE

Test sur des données publiques de change EUR/USD (Banque Centrale Européenne, 2020-2026).

**Observation clé :**  
Le Stability Score détecte des zones de dégradation **plusieurs semaines avant** que le KPI bancaire traditionnel ne réagisse.

---

## Limites assumées

Cette approche n'est **pas** :
- Un système de prédiction infaillible
- Un remplaçant complet des KPI existants
- Un outil d'optimisation automatique

Cette approche **est** :
- Un signal d'alerte précoce
- Un outil de priorisation des investigations
- Un complément aux indicateurs classiques

---

## Next steps méthodologiques

**Backtesting étendu** — Valider sur 10+ flux de natures différentes  
**Calibration sectorielle** — Adapter les paramètres par type de flux  
**Benchmarking** — Comparer systématiquement avec les outils standard  

---

**Question centrale :**  
"Quand tout semble normal dans les chiffres, est-ce que le comportement l'est vraiment ?"

➡️ [Retour au README](../README.md)
