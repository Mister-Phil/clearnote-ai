# ClearNote AI 🚀

Analyseur agentique et outil de tri automatisé de notes cliniques pour les professionnels de la santé (Travailleurs Sociaux, Ergothérapeutes, PME Médicales). 

Développé dans le cadre du **Hackathon AlgoFest 2026** (Track: HealthTech & Automation).

---

## 🎯 Le Problème
Les professionnels du secteur médico-social perdent en moyenne **20 minutes par document** à déchiffrer, structurer et synthétiser des notes cliniques ou des comptes-rendus d'évaluation complexes. Ce fardeau administratif réduit le temps disponible pour le soin direct aux patients.

## 💡 Notre Solution
**ClearNote AI** est un agent IA asynchrone sans friction. L'utilisateur envoie simplement ses notes brutes par courriel et reçoit en moins de 30 secondes un rapport clinique structuré, nettoyé et hiérarchisé directement dans sa boîte de réception.

---

## 🏗️ Architecture Algorithmique & Technique

Le pipeline est conçu pour être résilient, scalable et sécuritaire :

1. **Ingestion (Trigger)** : Détection temps réel des courriels entrants non lus via l'API Webhook de Gmail.
2. **Traitement Agentique (IA)** : Routage du corps de texte brut vers le modèle de raisonnement avancé **Claude 3.5 Sonnet / Claude 4.6**. L'agent réalise une extraction d'entités nommées et un résumé structuré en JSON strict.
3. **Parsing Dynamique** : Désérialisation à la volée du schéma JSON pour isoler les métadonnées (`patient_nom`, `actions_prioritaires`, `alertes_deadlines`).
4. **Distribution (Output)** : Génération automatisée d'un courriel HTML hautement lisible renvoyé instantanément au praticien émetteur.

```text
[Courriel Entrant] ➔ [Gmail API] ➔ [Claude Agentic Extraction] ➔ [JSON Parser] ➔ [Rapport Structuré Gmail]
```

---

## ⚙️ Stack Technique
* **Orchestration & Workflow** : Make.com (Moteur de routage logique)
* **Intelligence Artificielle** : Anthropic Claude API (`claude-3-5-sonnet` / `claude-4-6`)
* **Communication & Ingestion** : Google Workspace API (Gmail Restricted Scopes)
* **Format d'échange** : JSON Schema structuré

## 🔒 Sécurité & Confidentialité des Données
* **Zéro Rétention** : Les documents cliniques transitent en mémoire vive dans le pipeline. Aucune donnée de santé n'est stockée de manière persistante sur des serveurs tiers.
* **Conformité Anthropic API** : Les données soumises via l'API commerciale d'Anthropic ne sont jamais utilisées pour l'entraînement des modèles.
