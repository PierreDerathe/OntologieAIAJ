# 🇫🇷 Ontologie du Système Légal Français

Ce dépôt regroupe un ensemble de réflexions, de ressources, d'expérimentations et d'implémentations autour de la **modélisation ontologique du droit français**, avec une attention particulière portée sur les normes, leur hiérarchie, leur structure interne, et leurs interrelations.

---

## 📁 Contenu du dépôt

### 🔧 Outils & tutoriels

- [`protege.md`](/docs/protege.md)
  ➤ Tutoriel d’introduction à **Protégé**, outil pour la modélisation d'ontologie OWL.

---

### 🧠 Réflexion initiale & méthodologie

- [`ReflexionOntologie.md`](/docs/ReflexionOntologie.md)  
  ➤ Premières réflexions sur une ontologie légale **créée ex nihilo** (⚠️ **abandonnée**).

- [`methontology.md`](/docs/methontology.md)  
  ➤ Synthèse de la méthode **Methontology**, une approche structurée pour construire des ontologies.

---

### 🧱 Ontologies

- [`LegalFrancais.rdf`](/ontology/LegalFrancais.rdf)  
  ➤ Première version de l’ontologie développée pour le droit français (**abandonnée**, non alignée avec les standards existants).

- Dossier [`lkif-core/`](/lkif-core/README.md)  
  ➤ Clone ou copie de l’ontologie **LKIF Core**, modèle ontologique généraliste du domaine juridique.

- [`lkif-core.md`](/docs/lkif-core.md)  
  ➤ **Analyse détaillée** de la structure et des concepts clés de `lkif-core`.

---

### 🧪 Instanciation & tests

- [`RaisonnementInstance.md`](/article-9-1/RaisonnementLKIF.md)  
  ➤ Notes sur une **instanciation expérimentale** de `lkif-core` dans le contexte du droit français.

- [`article-9-1`](/article-9-1/)
  ➤ Dossier contenant toutes les ressources utilisées dans le cadre de l'instanciation de l'article 9-1 du code civil.
  - [`instance.ttl`](/article-9-1/instance.ttl)
    ➤ Fichier **Turtle** contenant un exemple d’**instanciation** concrète.
  - [`glossaire-article-9-1.csv`](/article-9-1/article-9-1%20-%20Glossaire.csv)
    ➤ Fichier **csv** contenant un glossaire des termes pertinents à l'article 9-1.

---

## 📎 Ressources complémentaires

Le dossier [`/ressource/`](/ressources/) contient des documents utiles à la conception de cette ontologie :

- Schémas de structure ou hiérarchie
- Articles académiques

---

## 📌 Objectif

Ce projet vise à :

- Étudier les **principes de modélisation** ontologique adaptés au domaine juridique
- Reprendre ou adapter des **ontologies existantes** (telles que `lkif-core`)
- Tester des **instanciations concrètes** basées sur le droit français
- Préparer le terrain pour une éventuelle ontologie robuste et réutilisable du système légal français

---

## 🔄 État des fichiers

| Fichier                         | Statut         | Description courte                          |
|--------------------------------|----------------|---------------------------------------------|
| `LegalFrancais.rdf`            | ❌ Abandonné   | Ontologie initiale non réutilisable         |
| `ReflexionOntologie.md`        | 🗒 Historique   | Réflexion préliminaire                      |
| `lkif-core.md`                 | ✅ Actif        | Analyse et compréhension de `lkif-core`     |
| `instance.ttl`                 | ✅ Actif        | Exemple d’instanciation `lkif-core`         |
| `RaisonnementInstance.md`      | ✅ Actif        | Raisonnement autour de l’instanciation      |
| `protege.md`                   | ✅ Actif        | Aide à l’édition avec Protégé               |
| `methontology.md`              | ✅ Actif        | Méthodologie de conception d’ontologie      |

---

## 📬 Contact

Pour toute question ou suggestion, n’hésitez pas à ouvrir une issue ou à proposer une pull request.

