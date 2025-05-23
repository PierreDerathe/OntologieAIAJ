# Ontologie légal française

### Différent axe de l'ontologie:
- Placement dans la hiérarchie des normes
- Type de document
- Structure du texte
- Propriétés
- Relation entre entité
- Description sémantique

Sur ces axes, j'ai une première proposition pour les trois premiers et je travaille maintenant sur les **Propriétés** et les **Relations entre entité**.  Je complète dés que j'ai du nouveau. Peut-être un petit retour de si vous pensez que la direction que je prends est bonne.

## Hiérarchie des normes

### Pyramide de kelsen:
1. Bloc de constitutionnalité
2. Bloc de conventionalité
3. Bloc de légalité
4. Bloc règlementaire
5. Actes individuels ou d'application

Hiérarchie proposée:
1. Bloc de constitutionnalité
    - Constitution de 1958
    - Préambule (Déclaration des droits de l'homme, Charte de l’environnement, etc.)
    - Principes fondamentaux reconnus par les lois de la République (PFRLR)
    - Principes à valeur constitutionnelle

2. Bloc de conventionalité
    - Traités et accords internationaux ratifiés
    - Droit de l'Union européenne (primauté)
        - TUE / TFUE
        - Règlements européens
        - Directives (transposables)

3. Lois organiques
    - Catégorie spécifique (art. 46 Constitution)
    - Supérieures aux lois ordinaires

4. Bloc de légalité
    - Lois ordinaires
    - Ordonnances (avant ou après ratification)
    - Lois de finance, lois de programmation
    - Décisions présidentielles (art. 16)
    - Jurisprudence de la Cour de cassation et du Conseil d’État?

5. Principes généraux du droit et jurisprudence
    - Principes généraux dégagés par le juge administratif
    - Jurisprudence constitutionnelle et administrative comme source indirecte du droit
    - Décisions juridictionnelles à valeur interprétative

6. Bloc réglementaire
    - Décrets du Premier ministre / Président
    - Décrets en Conseil d’État
    - Arrêtés ministériels
    - Règlements autonomes (art. 37)
    - Décrets d'application des lois

7. Actes administratifs subordonnés
    - Arrêtés préfectoraux, municipaux
    - Circulaires, instructions, directives internes
    - Décisions individuelles (n’ont pas toujours de portée normative)

**Utilité de cette proposition:**
- Discrimination des niveaux de normativité.
- Traçabilité des hiérarchies dans les relations
- Permet d'ajouter des règles d'inférence automatiques

Géré avec l'attribut `appartient_au_bloc` par exemple

## Typologie:
`DocumentJuridique` (sous-classe de Document)
- Constitution
- Loi
- LoiOrganique
- Ordonnance
- Décret
- Arrêté
- Circulaire
- Instruction
- Arrêt
- Code

`UnitéTextuelle`: Article

On peut aussi envisager les sous catégorie suivante de `DocumentJuridique` utilisant la hiérarchie des normes:
- Documents constitutionnels
- Documents législatifs
- Documents réglementaires
- Documents administratifs non normatifs
- Documents jurisprudentiels
- Documents codifiés(Code)

## Structure

La **structure formelle hiérarchique** des documents comme les **codes**, qui permet de situer chaque **article** dans son contexte.

---

###  1. **Structure canonique des codes français**

La structure des codes suit une hiérarchie très formelle:

```plaintext
Code
├── Livre
│   ├── Titre
│   │   ├── Chapitre
│   │   │   ├── Section
│   │   │   │   ├── Sous-section
│   │   │   │   │   ├── Paragraphe
│   │   │   │   │   │   └── Article
```

> Certains niveaux peuvent être absents selon le code (ex. il peut y avoir un livre → Titre → chapitre → article directement).

---

### 2. **Modélisation ontologique de la structure**

Tu peux modéliser cela en définissant une **classe abstraite** `UnitéStructurelle` avec des sous-classes :

#### Classes :

* `Livre`
* `Titre`
* `Chapitre`
* `Section`
* `SousSection`
* `Paragraphe`
* `Article`

#### Propriétés :

* `est_contenu_dans` (ou `partOf`)
* `contient` (ou `hasPart`)
* `precede` / `succede` (relation d’ordre)
* `a_numero` (identifiant textuel)
* `a_texte` (contenu textuel)
* `fait_partie_de` (pour rattacher toute unité au `DocumentJuridique` parent)

---

### Exemple RDF/Turtle :

```turtle
:Code_Civil a :Code .

:Livre_Ier a :Livre ;
         label "Des personnes"
         est_contenu_dans :Code_Civil .

:Titre_Ier a :Chapitre ;
            label "Des droits civils"
            est_contenu_dans :Livre_I .

:Article_1382 a :Article ;
              a_numero "7" ;
              a_texte "L'exercice des droits civils est indépendant..." ;
              est_contenu_dans :Titre_Ier ;
              fait_partie_du_code :Code_Civil .
```

---

* Crée une **hiérarchie stricte de classes** pour les unités textuelles.
* Lie chaque `Article` à une ou plusieurs entités structurelles parent (`est_contenu_dans`).
* L’article est la **feuille terminale** de l’arbre.

### 🗂️ Ontologies existantes
Voir si des ontologies existantes gère ce genre de problèmes.


## Relations

### **Relations normatives (entre articles ou textes)**

| Relation  | Domaine | Portée                                    | Inverse           | Commentaire                                                    |
| --------- | ------- | ----------------------------------------- | ----------------- | -------------------------------------------------------------- |
| `cite`    | Article | → Article / Document                      | `est_cité_par`    | Fréquente dans les lois, décisions, circulaires                |
| `modifie` | Article / Document | → Article |`est_modifié_par` | Action normative         |
| `abroge`  | Article / Document | → Article |`est_abrogé_par`  | Action de suppression    |
| `crée`    | Article / Document | → Article     |`est_créé_par`    | Création normative       |
| `codifie` | Article / Document       | → Article                |`est_codifié_par` | Intégration dans un code |

---

---

### **Relations structurelles (hiérarchie interne)**

| Relation           | Domaine         | Portée              | Inverse    | Commentaire                                                           |
| ------------------ | --------------- | ------------------- | ---------- | --------------------------------------------------------------------- |
| `est_contenu_dans` | Article / Unité | → UnitéStructurelle | `contient` | Pour modéliser la structure des codes                                 |
| `fait_partie_de`   | Unité / Article | → DocumentJuridique | -          | Pour rattacher toute entité à son code ou texte                       |
| `precede`          | Article         | → Article           | `succede`  | Ordre dans le document (utile pour générer des vues ou des sommaires) |

---

### **Relations temporelles / de version**

Deux choix possibles ici :

#### ✅ Option A : **Article comme entité versionnée**

* `versionPrecedente` / `versionSuivante` entre **articles**
* Permet de chaîner les évolutions

#### ✅ Option B : **Article + module version**

* Un `Article` possède plusieurs instances de `VersionArticle`
* Plus souple, permet de conserver :

  * Titre et autre information générique
  * Peut etre simplification des relation entre entité
  * Plus approprié pour visualisé l'historique et choisir la version concernée.

**Exemple RDF/OWL (option B)** :

```turtle
:Loi_2023_456 a :Loi ;
              modifie :Article_121_1 ;
              abroge :Article_1382 ;
              crée :Article_223_9 ;
              codifie :Article_223_9 .

:Article_1382 a :Article ;
              a_numero "1382" ;
              a_version :Article_1382_V1, :Article_1382_V2 .

:Article_1382_V1 a :VersionArticle ;
                 dateEntreeEnVigueur "1804-03-21"^^xsd:date ;
                 texte "Tout fait quelconque..." ;
                 est_abrogé_par :Loi_2023_456 .

:Article_1382_V2 a :VersionArticle ;
                 dateEntreeEnVigueur "2016-10-01"^^xsd:date ;
                 texte "Tout fait quelconque de l'homme..." .
```

---

### **Autre relations possibles**

Voici quelques relations utiles dans une ontologie juridique :

* `a_autorité_émettrice` → pour lier à l’institution ou auteur (parlement, ministre, municipalité...). Possibilité de lié à wikidata
* `porte_sur` ou `traite_de` → relier à une thématique ou un concept juridique (A approfondir dans l'axe sémantique)
* `applicable_a` → pour modéliser les destinataires (administrations, citoyens, entreprises)

---

## ✅ **Propriétés pour les articles (ou unités normatives)**

| **Propriété**       | **Type**     | **Description / Commentaire**                                                                   |
| ------------------- | ------------ | ----------------------------------------------------------------------------------------------- |
| `id`                | IRI / string | Identifiant unique dans l'ontologie (URI si RDF)                                                |
| `reference`         | string       | Ex. "Code pénal, Article 223-9" – concaténation du nom + numéro                                 |
| `num`               | string       | Numéro d’article seul (ex : "223-9")                                                            |
| `texte`             | string       | Contenu juridique de l’article                                                                  |
| `dateDebut`         | xsd\:date    | Date d’entrée en vigueur                                                                        |
| `dateFin`           | xsd\:date    | Date d’abrogation ou de fin de validité                                                         |
| `etat`              | enum         | `EN_VIGUEUR`, `ABROGE`, `PERIME`, `NON_ENTRE_EN_VIGUEUR` (suggestion ajout)                     |
| `urlLegifrance`     | URI          | Lien vers la ressource officielle                                                               |
| `multipleVersions`  | boolean      | Indique s’il existe plusieurs versions connues de cet article                                   |
| `derniereMiseAJour` | xsd\:date    | Dernière synchronisation de la base (à placer sur l’**entité de gestion**, ex. code ou dataset) |
| `a_un_niveau`       | enum         | `NATIONAL`, `REGIONAL`, `EUROPEEN`, `INTERNATIONAL` (normalisé)                                 |
| `a_une_portee`      | enum         | `GENERALE`, `INDIVIDUELLE`                           |
| `langue`              | | Utile si traductions (dans une optique européenne)      |
---

ontoviz gephi
https://www.w3.org/2001/sw/BestPractices/OEP/SimplePartWhole/

## 🧩 Hiérarchie résumée

```
owl:Thing
├── BlocNormatif
├── EntitéJuridique
│   ├── Norme
│   │   ├── Article
│   │   └── DocumentJuridique
│   └── UnitéStructurelle
└── EtatNormatif
```

---

## 📘 Description des classes

### 🧱 `BlocNormatif`

* **Type** : classe de catégorisation normative (par instances)
* **Description** : Représente un **bloc de la hiérarchie des normes** (bloc de constitutionnalité, bloc de légalité, etc.).
* **Instances typiques** : `:BlocConstitutionnalite`, `:BlocConventionnalite`, `:BlocLegalite`
* **Usage** : Permet de classer chaque `Norme` dans un bloc via une propriété comme `:appartientAuBloc`.

---

### 🟩 `EtatNormatif`

* **Type** : classe énumérative (type fermé de statuts)
* **Description** : Représente l’**état juridique** d’une norme à un instant donné.
* **Instances typiques** : `:EN_VIGUEUR`, `:ABROGE`, `:PERIME`, `:INAPPLICABLE`
* **Usage** : Attribut de toute `Norme` via une data/object property `:aEtatNormatif`.

---

### 🏛 `EntitéJuridique`

* **Type** : classe abstraite
* **Description** : Surclasse générique des entités juridiques, structurantes ou normatives, pour **centraliser des propriétés communes** comme : `label`, `dateDebut`, `etat`, `url`, etc.
* **Remarque** : C’est une classe technique/conceptuelle, utile pour la factorisation ontologique.

---

### ⚖️ `Norme` (sous-classe de `EntitéJuridique`)

* **Type** : classe intermédiaire de contenu normatif
* **Description** : Représente toute entité qui **porte une norme juridique**, que ce soit un `Article` ou un `DocumentJuridique`.
* **Objectif** : Regrouper les entités ayant des relations normatives (`modifie`, `abroge`, `codifie`, etc.).
* **Exemples d’individus** : un article de loi, un décret, une ordonnance.

---

### 📄 `DocumentJuridique` (sous-classe de `Norme`)

* **Type** : classe concrète
* **Description** : Représente un **document juridique complet** (loi, décret, ordonnance, circulaire, etc.).
* **Usage** : Catégorise les différents types de sources de droit formalisées et publiées.
* **Sous-classes possibles** : `Loi`, `Décret`, `Ordonnance`, `Code`, `Instruction`, etc.

---

### 📑 `Article` (sous-classe de `Norme` et `UnitéStructurelle`)

* **Type** : classe concrète **multi-typée**
* **Description** : Représente une **unité élémentaire normative**.
  L’article est à la fois :

  * Une **structure** d’un texte juridique (sous une hiérarchie formelle),
  * Et une **norme** à part entière pouvant être modifiée, abrogée, codifiée, etc.
* **Remarque** : Très important à typer à la fois comme `UnitéStructurelle` et `Norme`.

---

### 📚 `UnitéStructurelle` (sous-classe de `EntitéJuridique`)

* **Type** : classe formelle de structure documentaire
* **Description** : Représente la **structure hiérarchique interne** d’un texte juridique : `Livre`, `Chapitre`, `Section`, `Article`, etc.
* **Usage** : Permet de naviguer la structure logique des codes et textes consolidés (relations `contient`, `estContenuDans`, etc.).

---