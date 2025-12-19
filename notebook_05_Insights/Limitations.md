# Limites et prochaines étapes

Cette section reconnaît honnêtement les limites actuelles du projet et identifie les axes d'amélioration prioritaires.

---

## Limites actuelles

### 1. Validation limitée à un seul dataset

**Constat :**  
Le Stability Score a été testé principalement sur le cas EUR/USD (BCE, 2020-2026).

**Limitation :**  
Un seul cas de validation ne suffit pas pour garantir la robustesse sur tous les types de flux bancaires.

**Questions non résolues :**
- Le score fonctionne-t-il aussi bien sur des flux de paiements ? De délais ? De volumes ?
- Les seuils de détection sont-ils adaptés à tous les secteurs ?
- Y a-t-il des types de flux où l'approche est moins performante ?

**Impact :**  
Avant une utilisation opérationnelle, il faut backtester sur **5 à 10 flux différents** pour confirmer la généralisation.

---

### 2. Détection des dérives comportementales uniquement

**Constat :**  
Le score détecte les changements **internes** au flux (drift, volatilité, break), pas les chocs **externes** soudains.

**Limitation :**  
Si un événement extérieur brutal impacte le flux (réglementation, crise), le score le détectera mais **pas avant** qu'il ne se produise.

**Exemple :**  
Une nouvelle réglementation bancaire change instantanément un processus de paiement.  
➡️ Le score détectera le changement, mais ne l'anticipera pas (il ne lit pas les calendriers réglementaires).

**Impact :**  
Le score est un outil de surveillance continue, pas un oracle prédictif. Il faut le combiner avec une veille réglementaire et organisationnelle.

---

### 3. Calibration initiale nécessaire

**Constat :**  
Les seuils de détection (volatilité acceptable, drift significatif) doivent être ajustés selon le type de flux.

**Limitation :**  
Il n'existe pas encore de calibration "par défaut" universelle.

**Conséquence :**  
Pour un nouveau flux, il faut :
1. Observer le comportement historique (3-6 mois minimum)
2. Calibrer les seuils des 4 composants
3. Tester en mode "observation" avant activation en production

**Impact :**  
Le déploiement n'est pas instantané. Il faut un temps de calibration initial pour chaque flux.

---

### 4. Pas de scoring "absolu" entre flux

**Constat :**  
Un score de 60 sur le flux A n'est pas directement comparable à un score de 60 sur le flux B.

**Limitation :**  
Chaque flux a sa propre baseline de stabilité. Un flux intrinsèquement bruité peut avoir un score "normal" à 70, tandis qu'un flux très régulier devrait être à 95+.

**Conséquence :**  
Le score est un **indicateur relatif** par flux, pas un benchmark absolu entre flux.

**Impact :**  
On ne peut pas comparer directement la stabilité de deux flux différents. Il faut analyser chaque flux par rapport à son historique propre.

---

## Next steps prioritaires

### 1. Backtesting étendu (court terme)

**Objectif :**  
Valider le score sur **10 flux différents** :
- 3 flux de paiements
- 3 flux de délais
- 2 flux de volumes
- 2 flux de remboursements

**Métriques à mesurer :**
- Temps d'anticipation moyen (en jours)
- Taux de faux positifs
- Taux de faux négatifs
- Stabilité du score sur périodes calmes

**Résultat attendu :**  
Confirmer (ou infirmer) la robustesse du score sur des flux de natures variées.

---

### 2. Calibration sectorielle (moyen terme)

**Objectif :**  
Définir des paramètres de calibration **par type de flux** :
- Flux de paiements → Seuils X
- Flux de délais → Seuils Y
- Flux de volumes → Seuils Z

**Résultat attendu :**  
Réduire le temps de déploiement initial en proposant des calibrations "par défaut" selon le secteur.

---

### 3. Benchmarking systématique (moyen terme)

**Objectif :**  
Comparer le Stability Score aux outils standard sur les mêmes datasets :
- Seuils fixes (percentile 95, 99)
- Moyennes mobiles (7j, 30j)
- Z-score
- Détection d'anomalies (Isolation Forest, LOF)

**Métriques :**
- Temps d'anticipation vs outils classiques
- Taux de faux positifs vs outils classiques
- Facilité d'interprétation (subjectif, test utilisateur)

**Résultat attendu :**  
Documenter précisément dans quels cas le Stability Score apporte une valeur supérieure aux outils existants.

---

### 4. Documentation ROI (long terme)

**Objectif :**  
Quantifier l'impact économique de la détection anticipée.

**Approche :**
1. Identifier des incidents réels survenus dans l'historique
2. Estimer le coût de ces incidents (temps, ressources, impact client)
3. Calculer combien de jours d'avance le score aurait donné
4. Estimer le coût évité si l'incident avait été détecté plus tôt

**Résultat attendu :**  
Pouvoir argumenter : "3 semaines d'avance = économie de X€ par incident évité"

---

## Questions ouvertes

Ces questions nécessitent encore des expérimentations pour être résolues :

**Q1 : Fréquence optimale de recalcul**  
- Recalculer le score quotidiennement ? Hebdomadairement ?
- Le temps réel est-il nécessaire ou le batch suffit-il ?

**Q2 : Horizon de détection**  
- Le score détecte combien de temps à l'avance en moyenne ?
- Y a-t-il un "sweet spot" entre détection trop tardive et faux positifs ?

**Q3 : Adaptation aux saisonnalités**  
- Comment le score gère-t-il les flux à forte saisonnalité (fin de mois, fin de trimestre) ?
- Faut-il des calibrations spécifiques pour ces périodes ?

**Q4 : Dégradation acceptable**  
- Quel niveau de dégradation justifie une investigation humaine ?
- Score < 70 ? < 60 ? < 50 ?

**Q5 : Combinaison avec d'autres signaux**  
- Le score gagne-t-il à être combiné avec des alertes métier existantes ?
- Quelle est la meilleure logique de fusion de signaux ?

---

## Conclusion : un projet en construction

Ce projet est une **preuve de concept** démontrant la viabilité de l'approche.

**Ce qui est validé :**  
✓ Le principe de détection comportementale fonctionne  
✓ L'explicabilité est un vrai atout  
✓ La détection anticipée est confirmée sur un cas réel  

**Ce qui reste à faire :**  
⚠️ Validation à plus grande échelle  
⚠️ Calibration sectorielle  
⚠️ Documentation du ROI  

**Objectif :**  
Transformer une étude de cas personnelle en un outil opérationnel crédible.

---

➡️ [Retour aux enseignements clés](key-findings.md)  
➡️ [Retour au README](../README.md)
