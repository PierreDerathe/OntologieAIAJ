## Instanciation de l'Article 9-1 du code civil

Chacun a droit au respect de la présomption d'innocence.

Lorsqu’une personne est, avant toute condamnation, présentée publiquement comme coupable de faits faisant l’objet d’une enquête ou d’une instruction judiciaire, le juge peut, même en référé, sans préjudice de la réparation du dommage subi, prescrire toutes mesures, telles que l’insertion d’une rectification ou la diffusion d’un communiqué, aux fins de faire cesser l’atteinte à la présomption d’innocence, et ce aux frais de la personne, physique ou morale, responsable de cette atteinte.

## Raisonnment

La création de article implique la création du code civil.

### Classe du Code Civil: **Code**

Propriété:
- **bears some (Norm and (utterer some Legislative_Body))**
- **bears only (utterer some Legislative_Body)**
- **bears some (Legal_Expression or Norm)**
- **bears only (Expression and (stated_by some Statement_In_Writing))**

**bears**: A Medium 'bears' or carries expressions.
**utterer**: Relates an utterance (communicated propositional attitude) to its utterer

#### Implication:

Toute partie de code doit être une **Expression** et être communiqué par un **Legislative_Body** (dans le cas français, l'éxecutif  peut faire des lois?).

Une partie de **Code** doit être une **Expression**, une **Norm** ou une **Legal_Expression**?

Est-ce que un article est une **Expression**, un ensemble d'**Expression** ou une partie d'**Expression**? Pour simplifier, je considère que un article est **Expression**.

Nouvelle classe à explorer:
- **Legislative_Body**
- **Expression**, **Legal_Expression** et **Norm**
- **Statement_In_Writing**

```ttl
ex:CodeCivil rdf:type lkif:Code ;
    rdfs:label "Code Civil"@fr ;
    lkif:bears ex:Article9_1_CodeCivil .

ex:Article9_1_CodeCivil rdf:type lkif:Expression .
```

### Classe de l'assemblée nationale: **Legislative_Body**

Propriété:
- **actor_in some/only Action**
- **participant_in only Change**
- **member only (Organisation or Person)**
- **member some Person**
- **member only (plays some Organisation_Role)**
- **holds only Mental_Entity**
- **plays only Role**

**actor_in**: Specifies that the participant is an actor in some action.

#### Implication:

- **participant_in** est une sous-propriété de **actor_in**.
- **utterer** est une sous-propriété de **holds**.
- **Expression** est une sous-propriété de **Mental_Entity**.

Un **Legislative_Body** doit avoir une **Personne** membre, possiblement avec un **Organisation_Role** de député.

Un **Legislative_Body** doit être **actor_in** d'une **Action**, qui dans notre cas sera probablement un **Act_of_Law**, sous-classe de **Action**.

Un article, qui est une **Expression**, doit être **utterer**  par un agent (dans notre cas le **Legislative_Body**) due à une propriété du **Code**.

Définir un **Organisation_Role** de député pour les membres de l'Assemblée Nationale.

```ttl
ex:AssembleeNationale rdf:type lkif:Legislative_Body ;
    rdfs:label "Assemblée Nationale"@fr ;
    lkif:member ex:NadegeAbomangoli ;
    lkif:actor_in ex:VoteLoi2000_516 ;
    lkif:utterer ex:Article9_1_CodeCivil .

ex:NadegeAbomangoli rdf:type lkif:Person .
ex:VoteLoi2000_516 rdf:type lkif:Act_of_Law .
ex:Depute rdf:type lkif:Organisation_Role .
```

### Classe de l'article: **Expression**, **Legal_Expression**, **Norm** ou une sous-classe?

Explorons **Legal_Expression**.

Propriété:
- **attitude some (created_by some Public_Act)**
- **held_by some/only Agent**
- **stated_by some/only Communicated_Attitude**
- **medium some/only Medium**

**stated_by**: Relates a statement to its author

#### Implication:

- **stated_by** est une sous-propriété de **attitude**.
- **created_by** est une sous-propriété de **actor_in**.
- **Act_of_Law** est une sous-classe de **Public_Act**.
- **Statement_In_Writing** est une sous-classe de **Communicated_Attitude**

**Clarification des relations:**

**Legal_Expression** --**stated_by**-> **Statement_In_Writing** --**created_by**-> **Act_of_Law**

Trois classes à utiliser: **Legal_Expression**, **Statement_In_Writing**, **Act_of_Law**.

Or, on a l'article et la loi. Quelle est la troisième classe?

**Première possibilité:**
- Un article est une **Legal_Expression** appartenant à un code.
- Une loi est un **Statement_In_Writing** qui **states**/déclare des articles.
- L'**Act_of_Law** serait pas exemple le fait de voter la loi, ce qui conduit à la **creation** de la loi. Cet acttion demande une date, et un **actor** aurait une croyance, des intentions et des expectations pour cette loi. Ces propriété ont un sens intéréssant mais sont possiblement compliqué à trouver.

Les problèmes posés sont:
- un article complexe peut-il être représenté par une **Legal_Expression**?
- les relations existantes entre une **Statement_In_Writing** et une **Legal_Expression** sont **states**, **asserts**, **declares** et **promises**. Ces relations ne permettent pas d'exprimer de modification, abrogation... Utiliser des relations plus générique pourrait résoudre le problème.

**Deuxième possibilité:**
- La **Legal_Expression** serait un concept, par exemple: Chacun a droit au respect de la présomption d'innocence.
- Un article est une **Statement_In_Writing** alors l'appartenance à un **Code** n'est pas bien représenté par la relation **bears**, et un **Code** ne serait que un assenblement de concept juridique.
- Une loi serait un **Act_of_Law**, une action de création, dans notre cas de modification d'article et pas une entité à part entière.

1- La première possibilité respecte mieux la structure du **Code** contenant les articles et la loi qui est une proposition écrite avec un auteur.

Je vais dévelloper la première possibilité.

```ttl
ex:Article9_1_CodeCivil rdf:type lkif:Legal_Expression ;
    rdfs:label "Article 9-1 du Code Civil"@fr ;
    lkif:stated_by ex:Loi2000_516 ;
    lkif:utterer ex:AssembleeNationale ;
    lkif:medium ex:CodeCivil ;
    lkif:attitude created_by ex:VoteLoi2000_516 .

ex:AssembleeNationale rdf:type lkif:Legislative_Body .
ex:Loi2000_516 rdf:type lkif:Statement_In_Writing .
ex:VoteLoi2000_516 rdf:type lkif:Act_of_Law .
```



