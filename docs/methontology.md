# Synthèse de METHONTOLOGY

Cette synthèse de METHONTOLOGY, méthode de construction d'ontologie, est basé sur [Building legal ontologies with METHONTOLOGY and WebODE](/ressources/methontology.pdf).

## Spécification de l'ontologie

- Déterminer le but de l'ontologie, cad son utilisation prévu, des scénario d'utilisation, ses utilisateurs, etc...
- Décider du niveau de formalité de l'ontologie. Que signifie "niveau de formalité"?
- Déterminer le champ d'application, qui comprend l'ensemble des termes à représenter, ses caractéristiques et sa granularité.

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

## Etapes de la conceptualisation:

1. Construire un glossaire des termes
1. Construire une taxonomie des concepts
1. Construire des diagrammes de relations binaires
1. Construire un dictionnaire des concepts
1. Définir les relations binaires en détail
1. Définir les attributs des instances en détail
1. Définir les attributs des classes en détail
1. Définir les constantes en détail
1. Définir les axiomes formels
1. Définir les règles
1. Définir les instances

