Voor alle voorbeelden geldt dat Cat een subtype is van Animal.

Covariant:
  Behoud de volgorde van de types.

  Dus als I covariant is, dan is de volgorde van types: I\<Child\> ≤ I\<Parent\>

  Voorbeeld:
    IEnumerable\<Cat\> is een subtype van IEmumerable\<Animal\> want IEnumerable\<T\> is covariant op T

Contravariant:
  Keert de volgorde juist om.

  Dus als I contravariant is, dan is dit de volgorde van types: I\<Parent\> ≤ I\<Child\>

  Voorbeeld:
    Action\<Animal\> is een subtype van Action\<Cat\> want Action\<T\> is contravariant op T

Invariant:
  Als I invariant is dan kan I\<Parent\> niet voor I\<Child\> worden gebruikt en omgekeerd.

  Voorbeeld:
    IList\<Cat\> is geen subtype van IList\<Animal\> en IList\<Animal\> is geen subtype van IList\<Cat\> want IList\<T\> is invariant op T.

Bivariant (niet behandeld, maar voor compleetheid wel in deze lijst):
  Als I bivariant is, dan gedraagt I zich soms covariant, en soms contravariant (afhankelijk van de context).

  C# heeft geen built-in bivariant types in de strikte zin van het woord.

Variant:
  Covariant, Contravariant, of Bivariant

  Voorbeeld:
    Zie andere voorbeelden.
