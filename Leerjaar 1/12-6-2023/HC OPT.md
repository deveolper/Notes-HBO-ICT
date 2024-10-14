Vandaag Demo van het Observer Pattern

Volgende week dinsdag presenteren we ons product aan 42.

De demo was niet volledig gelijk aan het voorbeeld in de slides.



Observer voorbeeld:

\<\<interface>> IObserver
----------------------------------------
----------------------------------------
update(Observable, Object)

\<\<template>> Receiver
----------------------------------------
\- Owner: String

----------------------------------------
\+ update(Observable, Object)

\# *getReceiver(): String*

\- getMessage(): String

Email implements Receiver
----------------------------------------
\- email: String

----------------------------------------
\+ Email(String, String)

\- getReceiver(): String


*Observable*
----------------------------------------
----------------------------------------
addObserver(IObserver)

setChanged()

notifyObservers()


Sensor extends Observer
----------------------------------------
\+ MINIMUM: int

\+ MAXIMUM: int

\+ temperature: int

----------------------------------------
\+ Sensor(int)

\+ setTemperature(int)

\- seeder()

\# checkTemperature(String)

\+ main(String[] args)


Alles is terug te kijken.
