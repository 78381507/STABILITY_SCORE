# Contexte & Problématique

## Le problème opérationnel réel

Les banques surveillent quotidiennement des centaines de flux opérationnels :
- Paiements interbancaires
- Délais de traitement
- Encaissements clients
- Remboursements de crédits
- Opérations back-office

Chaque flux génère des données en continu. Chaque flux doit rester **stable et prévisible**.

**Le risque principal ?** Pas l'erreur brutale et visible, mais **la dérive lente et silencieuse** du comportement des flux.

---

## Pourquoi les outils actuels ne suffisent pas

### 1. Seuils fixes

Les alertes basées sur des seuils fixes sont inefficaces face aux dérives progressives.

**Exemple :**  
Un délai de paiement passe graduellement de 2 jours à 3 jours sur 6 semaines.  
➡️ Aucun seuil n'est franchi  
➡️ Aucune alerte n'est déclenchée  
➡️ Incident détecté trop tard

### 2. Moyennes mobiles

Les moyennes lissent les données et **masquent la dégradation** en cours.

Quand la moyenne réagit enfin, le problème est déjà installé depuis plusieurs semaines.

### 3. Modèles complexes (ML/AI)

Les approches machine learning peuvent être performantes, mais elles posent des problèmes en banque :
- Boîte noire difficile à expliquer
- Incompatibilité avec les exigences d'audit
- Complexité de maintenance
- Méfiance des régulateurs

### 4. Alertes tardives

**Constat terrain :**  
Les KPI bancaires traditionnels signalent un problème quand il est déjà devenu coûteux à corriger.

Les équipes opérationnelles découvrent l'anomalie par ses **conséquences** (plaintes clients, erreurs en cascade), pas par détection proactive.

---

## Le coût de l'attente

Un incident opérationnel bancaire non détecté peut coûter :
- Temps d'investigation multiplié (chercher la cause racine a posteriori)
- Impact client (insatisfaction, compensation)
- Coûts de correction (ressources mobilisées en urgence)
- Risque réglementaire (notification aux autorités)

**La vraie valeur ?** Détecter **avant** que le flux ne génère un incident visible.

---

## La solution attendue

Pour être utile en banque, un outil de détection doit être :

✅ **Précoce** — Signaler la dégradation avant l'incident  
✅ **Explicable** — Pas de boîte noire, compatible compliance  
✅ **Actionnable** — Prioriser les investigations humaines  
✅ **Fiable** — Minimiser les faux positifs  
✅ **Simple** — Déployable sur des centaines de flux  

**C'est l'objectif du Stability Score.**

---

## La question de recherche

**"Comment mesurer la stabilité comportementale d'un flux bancaire de façon simple, explicable et anticipative ?"**

Réponse ➡️ Voir dossier Methodology
