# Synthèse de METHONTOLOGY

Cette synthèse de METHONTOLOGY, méthode de construction d'ontologie, est basé sur [METHONTOLOGY: FromOntological Art TowardsOntological Engineering](/ressources/methontology_origin.pdf) et [Building legal ontologies with METHONTOLOGY and WebODE](/ressources/methontology_legal.pdf).

## Spécification de l'ontologie

- Déterminer le but de l'ontologie, cad son utilisation prévu, des scénario d'utilisation, ses utilisateurs, etc...
- Décider du niveau de formalité de l'ontologie. Que signifie "niveau de formalité"?
- Déterminer le champ d'application, qui comprend l'ensemble des termes à représenter, ses caractéristiques et sa granularité.

Les propriétés suivantes sont attendues de la spécification:

- La concision, c'est-à-dire que chaque terme est pertinent, et il n'y a pas de termes dupliqués.
- La cohérence, c'est-à-dire le fait que tous les termes et leur signification ont un sens dans le domaine.
- La complétude partielle pour que l’ontologie couvre suffisamment bien son domaine avec des concepts essentiels, sans problème d'étape intermédiaire, et à un niveau de détail adapté. On attend:
  - une complétude suffisante (sans prétendre à l’exhaustivité).
  - une cohérence dans la structure.
  - une granularité cohérente et adaptée à l’objectif.

## Principaux composants de modélisation

METHONTOLOGY conceptualise des ontologies à l'aide de Représentations Intermédiaires(IR) graphique et tabulaires. Ces IR permettent de modéliser les composants suivants:

- **Concepts** A prendre au sens large. Nous chercherons à créer des taxonomies des concepts.
Par exemple: Personne morale, Mineur, Decret, Article...
- **Relations** Représente une relation entre concepts. Une relation entre deux éléments est appelée une relation binaire, que nous allons prioriser.
- **Instances** sont utilisées pour représenter des éléments ou des individues de l'ontologie. Les concepts et les relations peuvent être instanciés.
- **Constantes** sont des valeurs qui ne changent pas dans le temps, par exemple l'age de la majorité.
- **Attributs** décrivent les propriétés des instances et des concepts. Nous ferons la différence entre les attributs de classe et d'instance.
- **Axiomes formels** Expression logique toujours vrai utilisé pour contraindre une ontologie et son utilisation.
- **Règles** généralement utilisées pour déduire des information dans une ontologie.

## Etapes de la conceptualisation

### 1. Construire un glossaire des termes

D'abord, un glossaire doit être construit comme mentionné dans la spécification. Il doit contenir tous les termes pertinents, avec leur description, synonymes et acronymes. Le travail important de cette étape est de déterminer le type(concept, instance, attribut, relation) des termes. La granularité choisie peut influencer le type des termes, en particulier entre concept et instance.

### 2. Construire des taxonomies des concepts

Il faut maintenant construire des taxonomies des concepts pour définir la hiérarchie des concepts.

METHONTOLOGY utilise 4 relations taxonomic:

- Subclass-Of: Un concept C1 est une Subclass-Of un concept C2 si tout les instances de C1 sont des instances de C2.
- Disjoint-Decomposition
- Exhaustive-Decomposition
- Partition

### 3. Construire des diagrammes de relations binaires

Le but des ces diagrammes est d'établir les relations binaires entre concepts de la même (ou de différentes) taxonomie.

### 4. Construire un dictionnaire des concepts

Une fois ces diagrammes réalisés, un dictionnaire des concepts peut être construit.
Ce dictionnaire contient tout les concepts, leurs relations, leurs instances et leurs attributs de classe et d'instance.

Un travail similaire est fait pour les relations et les attributs.

### 5. Définir les relations binaires

Pour les relations, il faut décrire la source et la cible de la relation, ainsi que la cardinalité et la relation inverse.

### 6. Définir les attributs des instances et de classes

Pour les attributs, il faut décrire le nom de l'attribut, du concept qu'il décrit, le type de valeur, les valeur autorisées et la cardinalité.

La différence entre attributs d'instance et de classe est que le premier décrit et peut changer entre instance d'une même classe, par exemple le nombre de membre d'une *POrganisation* la où le deuxième précise la définition du concept.

### 7. Définir les constantes

On cherche ici à décrire en détail les constantes mentionnées dans le glossaire. On veut le nom, le type, la valeur, l'unité de mesure. Par exemple, l'age de la majorité est 18 ans.

### 8. Définir les règles et axiomes formels

On doit identifier les règles et axiomes nécessaires et les décrire. Les information à spécifier serait le nom, le description en langage naturelle, l'expression logique, les variables, les concepts et les relations concernées.

Je ne suis pas sûr de la différence entre règles et axiomes.

### 9. Définir les instances

Une fois les autres étapes faites, on peut définir les instances intéressantes qui apparaissent dans le glossaire. Il faudra le nom, le concept de l'instance, ses attributs et ses relations.

## Integration

- Chercher les meta-ontologies qui correspondent le mieux à la conceptualisation. Le but est que les nouveaux concepts soit basées sur un set commun de termes basiques.
- Trouver des ontologies qui contiennent des définitions cohérentes dans la conceptualisation.
