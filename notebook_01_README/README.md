# Stability Score — Détection précoce de dérives opérationnelles

> **Un indicateur comportemental pour signaler les anomalies avant qu'elles deviennent des incidents**

Les banques surveillent des centaines de flux opérationnels : paiements, délais, encaissements, remboursements. Les indicateurs classiques (moyennes, seuils fixes) restent souvent au vert jusqu'à l'apparition d'un incident coûteux.

**Le problème ?** La dérive lente et silencieuse du comportement des flux.

**La solution ?** Un score de stabilité (0-100) qui détecte les changements comportementaux **avant** que les KPI traditionnels ne réagissent.

---

## 📊 Illustration clé

[Early Signal](ECB_USD-EUR.png)

**En bleu** : Le Stability Score détecte les zones de dégradation (zones grises)  
**En orange** : Le KPI bancaire traditionnel réagit avec retard

➡️ **Temps d'avance moyen : plusieurs semaines**

---

## 🎯 Objectif de cette étude

Ce projet est une **étude de cas personnelle** démontrant une approche méthodologique pour la détection d'anomalies comportementales dans les flux bancaires.

**Ce repository contient :**
- Le contexte métier et la problématique
- La démarche méthodologique (sans code propriétaire)
- Les résultats visuels sur un cas réel (EUR/USD BCE)
- Les insights et limitations

**Ce repository ne contient pas :**
- Le code source (méthodologie propriétaire)
- Les formules mathématiques exactes
- Les paramètres de calibration

---

## 📂 Navigation

### [01 — Contexte & Problématique](01-context/problem-statement.md)
Pourquoi les outils actuels ne suffisent pas face aux dérives silencieuses.

### [02 — Méthodologie](02-methodology/approach.md)
Démarche générale et principes de conception.

### [03 — Résultats](03-results/case-study.md)
Analyse du cas EUR/USD avec visualisations.

### [04 — Insights](04-insights/key-findings.md)
Enseignements clés et limitations reconnues.

---

## 🔑 Principes de conception

**Simple** — 4 composants mesurables, pas de boîte noire  
**Explicable** — Compatible audit et compliance bancaire  
**Actionnable** — Signal précoce pour investigation humaine  
**Robuste** — Testé sur différents types de chocs

---

## 🎓 Compétences démontrées

- **Analyse quantitative** : Décomposition d'un problème complexe en composants mesurables
- **Pensée métier** : Compréhension des contraintes bancaires (explicabilité, audit)
- **Visualisation** : Communication claire de résultats analytiques
- **Rigueur scientifique** : Tests de robustesse, reconnaissance des limitations

---

## 📧 Contact

**François** — [mailto: tilkinanalytics@gmail.com]

*Ce projet est une étude de cas personnelle à visée démonstrative.*

---

**Disclaimer** : La méthodologie complète et le code source sont propriétaires et ne sont pas partagés dans ce repository.
