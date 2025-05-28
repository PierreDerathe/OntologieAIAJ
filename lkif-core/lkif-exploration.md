# Exploration  de LKIF Core

Cette exploration est basée sur [LKIF Core: Principled Ontology Development for the Legal Domain](/lkif-core/LKIF-Core-Principled-Ontology-Development-for-the-Legal-Domain.pdf)

L'ontologie LKIF est composée d'un ensemble de plus petites ontologies. Ces ontologies peuvent être classées en 3 niveaux: Supérieur, Intentionel et Légal. Les ontologies des dernières couches se basent et réutilisent les concepts développés dans les couches supérieurs.

![Dependencies between LKIF Core modules](/lkif-core/image/dependencies.png "Dependencies between LKIF Core modules")
**Dependencies between LKIF Core modules**

## Niveau supérieur

Dans LKIF, toute ontologie juridique doit reposer sur une base conceptuelle minimale représentant le monde physique, mental, abstrait et les occurences:
- Entités ayant une existence physique indépendamment de l'observation humaine. A des propriétés spatio-temporelles.
- Éléments de la pensée ou de l’intention humaine avec des propriétés temporelles.
- Concepts abstraits par exemple logique ou mathématique. Peu utilisé dans notre cas.
- Les occurences permettent de représenter les propriétés spatiales et temporelles nécessaires aux entités.

Les relations méréologiques permettent de définir les ensembles et les parties.

Pour la représentation spatial, sont proposée les notions de place absolue et relative (par rapport à un objet, une entité) et différentes relations entre ces places, par exemple *meet*, la superposition partielle.

![Place and Mereology related concepts](/lkif-core/image/place-mereology.png)

**Concepts méréologique et spatial**

La notion de temps fait la distinction entre *Moment* (un point dans le temps atomique) et *Interval* (une durée) et propose des relations pour exprimer avant, après, pendant...

Ces occurences spatiales et temporelles sont utilisées pour définir les entités physiques et mentales.

Ces concepts sont utilisés pour exprimer le concept de changement comme la différence de situation avant et après le changement, et en particulier la distinction entre *Initiation*, *Continuation* et *Termination*.

La notion de *Process* comme un changement issue d'une nécessité causal est aussi définit, mais je n'ai pas bien compris le concept.

![Concepts related to time and change](/lkif-core/image/time-change.png)

**Concepts relatifs au temps et au changement**

## Niveau intentionnel

Ce niveau essaie d'exprimer la prédiction et l'explication de comportement intelligent.

Le niveau intentionnel introduit une modélisation de concepts mentaux et comportementaux nécessaires à la description d’acteurs rationnels: des *Action*s entrepries par des *Agent*s ayant un *Role* spécifique. De plus, des concepts sont proposés pour décrire les *Intention*s et *Croyance*s des agents, ainsi que la communication entre agents au moyen d'*Expression*s.

Un *Agent* est l'ensemble de ce qui peut être acteur d'une action, le plus souvent des personnes ou des organisation.

Les *Action*s sont des changements due à un *Agent* réalisant ses intentions.

![Actions, agents and organisations](/lkif-core/image/action-agent.png)

**Actions, agents et organisations**

Les *Role*s permettent de spécifier des standarts, des propriétés ou des comportements aux entités ayant ce rôle. Ils qualifient aussi bien des artéfacts que des agents. Le rôle d'un agent prescrit son comportement dans un contexte, et donc ses actions, ce qui met en évidence les déviations.

![Roles](/lkif-core/image/role.png)

**Rôles**

## Niveau légal

Je n'arrive pas à saisir les concepts suivant en lisant le papier ou en parcourant l'ontologie: Les proposition, Attitudes et Expressions ainsi que les Normes et Qualifications.

Pour comprendre cette partie de l'ontologie, un travail de d'[instanciation d'exemple du système légal français](/RaisonnementInstance.md) est proposé.

![Propositions, Attitudes and Expressions](/lkif-core/image/proposition-attitude.png)

**Propositions, Attitudes et Expressions**

![Qualifications and Norms](/lkif-core/image/qualification-norm.png)

**Normes et Qualifications**