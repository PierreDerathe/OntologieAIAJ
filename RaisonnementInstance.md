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

**Implication:**

Toute partie de code doit être une **Expression** et être communiqué par un **Legislative_Body** (dans le cas français, l'éxecutif  peut faire des lois?).

Une partie de **Code** doit être une **Norm** ou une **Legal_Expression**.

Est-ce que un article est une **Expression**, un ensemble d'**Expression** ou une partie d'**Expression**? Pour simplifier, je considère que un article est **Expression**.

Nouvelle classe à explorer:
- **Legislative_Body**
- **Expression**, **Legal_Expression** et **Norm**
- **Statement_In_Writing**

```ttl
ex:CodeCivil rdf:type lkif:Code ;
    rdfs:label "Code Civil"@fr ;
    lkif:bears ex:Article9_1_CodeCivil .
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

**Implication:**

- **participant_in** est une sous-propriété de **actor_in**.
- **utterer** est une sous-propriété de **holds**.

Un **Legislative_Body** doit avoir une **Personne** membre, possiblement avec un **Organisation_Role** de député.











Loi

Droit

Presomption

Innocence

Personne
classe: 

Date

En Vigueur

Modifié

Codifié



