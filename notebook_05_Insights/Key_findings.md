# Enseignements clés

Cette section présente les observations principales issues des tests du Stability Score sur le cas EUR/USD BCE.

---

## Finding 1 : Détection anticipée confirmée

**Observation :**  
Le Stability Score détecte les zones de dégradation **plusieurs semaines avant** que le KPI bancaire traditionnel ne réagisse.

**Mesure concrète :**  
Sur le cas EUR/USD, les zones grises (dégradation détectée) apparaissent systématiquement avant les pics du KPI retardé.

**Implication métier :**  
Ce délai d'anticipation permet aux équipes opérationnelles de :
- Lancer une investigation avant l'incident
- Identifier la cause racine plus facilement
- Corriger le problème avec moins de ressources

**Valeur ajoutée :**  
Passer d'une logique **réactive** (corriger après l'incident) à une logique **proactive** (détecter avant l'incident).

---

## Finding 2 : Robustesse aux différents types de chocs

**Observation :**  
Les tests de chocs synthétiques montrent que le score réagit différemment selon le type d'anomalie :

- **Rupture brutale** → Chute instantanée du score, récupération lente
- **Pic temporaire** → Chute forte mais récupération rapide
- **Dérive lente** → Chute progressive et persistante

**Implication technique :**  
Le score capture bien des **patterns comportementaux distincts**, pas juste des variations de magnitude.

**Valeur ajoutée :**  
Les équipes peuvent interpréter la forme de la courbe du score pour diagnostiquer le type de problème avant même d'investiguer les données brutes.

---

## Finding 3 : Lisibilité pour les non-data scientists

**Observation :**  
Le score sur une échelle 0-100 et la décomposition en 4 composants visuels rendent l'outil accessible aux équipes métier.

**Tests informels :**  
Des profils non-techniques (managers, analystes métier) comprennent immédiatement :
- Que 100 = stable, 0 = instable
- Quel composant est dégradé (volatilité, drift, break, observability)
- Quand la dégradation a commencé (lecture de la courbe)

**Implication organisationnelle :**  
Pas besoin de data scientists pour utiliser le score au quotidien. Les équipes opérationnelles peuvent s'en servir directement.

**Valeur ajoutée :**  
Adoption facilitée, formation minimale, appropriation par les métiers.

---

## Finding 4 : Cas d'usage validé sur données réelles

**Dataset :** EUR/USD, Banque Centrale Européenne, 2020-2026

**Résultat :**  
Le score a détecté avec succès :
- Les zones de forte volatilité (2020, 2023, 2025)
- Les périodes de drift persistant
- Les changements de régime comportemental

**Comparaison :**  
Le KPI bancaire traditionnel (normalisé 0-100) reste bruité et réagit avec retard systématique.

**Validation :**  
Ce premier cas réel confirme que l'approche fonctionne sur un flux financier complexe avec plusieurs années de données.

---

## Finding 5 : Complémentarité avec les KPI existants

**Observation :**  
Le Stability Score n'est pas un remplaçant des KPI classiques, mais un **signal complémentaire**.

**Logique d'utilisation :**
1. Le Stability Score **alerte** sur une dégradation comportementale
2. Les équipes investiguent les **données brutes**
3. Les KPI classiques confirment ou infirment l'**impact métier**

**Valeur ajoutée :**  
Les deux outils se renforcent mutuellement :
- Le Stability Score donne l'alerte tôt
- Les KPI traditionnels mesurent l'impact final

---

## Synthèse

**Ce qui fonctionne :**
✓ Détection anticipée (plusieurs semaines d'avance)  
✓ Robustesse aux différents types d'anomalies  
✓ Explicabilité et lisibilité métier  
✓ Validation sur un cas réel complexe  

**Ce qui reste à valider :**
⚠️ Performance sur d'autres types de flux (voir [limitations](limitations.md))  
⚠️ Taux de faux positifs sur grande échelle  
⚠️ Seuils optimaux selon les secteurs  

---

➡️ [Voir les limitations et next steps](limitations.md)  
➡️ [Retour au README](../README.md)
