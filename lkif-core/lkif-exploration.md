# Exploration  de LKIF Core 

L'ontologie LKIF est composée d'un ensemble de plus petites ontologies. Ces ontologies peuvent être classées en 3 couches: Top, Intentional et Legal. Les ontologie des dernières couches se basent et réutilisent les concepts développés dans les couches supérieurs.

Les couches Top et Intentional définissent des concepts généraux qui sont difficiles à utiliser dans un premier temps. Je préfère me concentrer sur la dernière couche Legal pour constater comment elle s'applique au droit français. Je reviendrait sur ces couches dans un second temps pour utiliser ces concepts plus généraux et pour voir si il est possible d'utiliser cette base.

Je les présente tout de même pour donner une idée de leurs contenus.

![Dependencies between LKIF Core modules](/lkif-core/image/dependencies.png "Dependencies between LKIF Core modules")
**Dependencies between LKIF Core modules**

## Top module

Dans LKIF, toute ontologie juridique doit reposer sur une base conceptuelle minimale représentant le monde physique, mental, abstrait et les occurences:
- Entités ayant une existence physique indépendamment de l'observation humaine. A des propriétés spatiaux temporelles.
- Éléments de la pensée ou de l’intention humaine avec des propriétés temporelles.
- Concepts abstraits par exemple logique ou mathématique. Peut utilisé dans notre cas.
- Les occurences permettent de représenter les propriétés spatiales et temporelles nécessaires aux entités.

![Place and Mereology related concepts](/lkif-core/image/place-mereology.png)

![Concepts related to time and change](/lkif-core/image/time-change.png)

![Actions, agents and organisations](/lkif-core/image/action-agent.png)

![Roles](/lkif-core/image/role.png)

![Propositions, Attitudes and Expressions](/lkif-core/image/proposition-attitude.png)

![Qualifications and Norms](/lkif-core/image/qualification-norm.png)