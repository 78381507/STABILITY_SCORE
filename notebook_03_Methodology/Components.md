# Les 4 composants du Stability Score

Chaque composant capture une dimension différente de l'instabilité comportementale. Ensemble, ils forment une vue complète de la stabilité d'un flux.

---

## 1. Volatility (Volatilité)

### Définition intuitive

La volatilité mesure l'**augmentation anormale du bruit** dans les données.

Un flux stable a des variations prévisibles. Quand le bruit augmente soudainement, même si la moyenne reste stable, c'est un signal de dégradation.

### Ce qu'elle détecte

- **Instabilité naissante** — Le flux devient erratique
- **Perte de régularité** — Les patterns habituels se désorganisent
- **Incohérences opérationnelles** — Variations inhabituelles sans cause apparente

**Exemple bancaire :**  
Un délai de paiement était stable à 2 jours ± 2 heures. Soudain, il varie entre 1 et 3 jours sans raison.  
➡️ La moyenne est toujours à 2 jours, mais le comportement est devenu instable.

### Pourquoi c'est important

La volatilité est souvent le **premier signal** de dégradation. Elle apparaît avant que la moyenne ne bouge ou qu'un seuil ne soit franchi.

En détectant l'augmentation du bruit tôt, on peut investiguer avant que le problème ne devienne visible dans les KPI classiques.

---

## 2. Drift (Dérive)

### Définition intuitive

Le drift détecte les **tendances lentes et persistantes** dans les données.

Contrairement à un choc brutal, le drift est progressif : le flux glisse graduellement vers un nouveau comportement.

### Ce qu'il détecte

- **Dégradation progressive** — Le flux se dégrade semaine après semaine
- **Changement structurel lent** — Nouvelle dynamique qui s'installe
- **Dérive non corrigée** — Problème non détecté qui s'accumule

**Exemple bancaire :**  
Un volume de transactions passe de 1000/jour à 850/jour sur 8 semaines.  
➡️ Aucun jour n'est alarmant individuellement, mais la tendance est claire.

### Pourquoi c'est important

Le drift est **invisible aux seuils fixes**. Il ne franchit jamais d'alerte, mais il dégrade silencieusement le flux.

C'est le type de problème qui passe sous le radar des outils classiques, puis explose en incident 3 mois plus tard quand il devient enfin visible.

---

## 3. Break (Rupture)

### Définition intuitive

Le break identifie les **changements locaux de régime** : le flux adopte soudainement un nouveau comportement.

À la différence de la volatilité (augmentation du bruit) ou du drift (glissement lent), le break est un **changement de comportement structurel**.

### Ce qu'il détecte

- **Changement de régime** — Le flux opère désormais différemment
- **Rupture dans les patterns** — Les règles habituelles ne s'appliquent plus
- **Incident non résolu** — Un problème a modifié durablement le comportement

**Exemple bancaire :**  
Un flux de remboursements suit un pattern saisonnier stable. Soudain, le pattern disparaît : les remboursements deviennent constants toute l'année.  
➡️ Quelque chose a changé structurellement dans le processus.

### Pourquoi c'est important

Le break signale qu'on n'est **plus dans le même flux**. Les références historiques ne sont plus pertinentes.

C'est critique pour les équipes : elles doivent comprendre ce qui a changé pour adapter leur surveillance.

---

## 4. Observability Gap (Écart d'observabilité)

### Définition intuitive

L'observability gap quantifie **ce qui n'est pas expliqué** par le modèle de comportement normal du flux.

C'est la partie "inexplicable" des variations observées.

### Ce qu'il détecte

- **Comportement atypique** — Des patterns jamais vus auparavant
- **Données corrompues** — Valeurs incohérentes avec l'historique
- **Facteur externe non modélisé** — Une variable cachée perturbe le flux

**Exemple bancaire :**  
Un flux de paiements est modélisé avec des patterns jour/semaine/mois. Soudain, 15% des valeurs ne correspondent à aucun de ces patterns.  
➡️ Il y a quelque chose dans les données que le modèle ne capture pas.

### Pourquoi c'est important

Un observability gap élevé signifie que le flux échappe à la compréhension du modèle. C'est un signal qu'il faut **revoir les hypothèses** ou investiguer un nouveau phénomène.

C'est aussi un indicateur de **qualité de modélisation** : si le gap reste élevé même après calibration, c'est que le flux est intrinsèquement complexe ou bruité.

---

## Agrégation des composants

Les 4 composants sont **normalisés** (ramenés sur une échelle 0-100), puis **combinés** pour produire le Stability Score final.

**Logique de combinaison :**  
- Si **un seul** composant chute fortement → Le score chute (signal d'alerte)
- Si **tous** les composants sont stables → Le score reste élevé
- Si **plusieurs** composants se dégradent → Le score chute fortement (alerte renforcée)

**Pondération :**  
Les 4 composants n'ont pas forcément le même poids selon le type de flux. Par exemple :
- Flux très bruité → Le drift compte plus que la volatilité
- Flux très régulier → La volatilité est un signal fort

---

## Visualisation

Chaque composant peut être affiché individuellement pour comprendre **quelle dimension** de la stabilité est affectée.

![Exemple de décomposition des 4 composants](../03-results/visualizations/02-components-breakdown.png)

Cette décomposition permet aux équipes métier de diagnostiquer rapidement :
- "Ah, c'est le drift qui pose problème, pas la volatilité"
- "Le break est apparu le 15 avril, qu'est-ce qui a changé ce jour-là ?"

---

➡️ [Retour à la méthodologie](approach.md)  
➡️ [Voir les résultats](../03-results/case-study.md)
