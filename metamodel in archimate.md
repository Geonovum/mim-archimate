# Metamodel in ArchiMate

Dit hoofdstuk beschrijft de mapping tussen MIM en de ArchiMate modelleertaal.

## Inleiding
Zoals in voorgaande tekst beschreven heeft het waarde heeft om MIM modellen te kunnen uitdrukken in ArchiMate. Het biedt een startpunt voor het opstellen van MIM modellen en maakt het mogelijk om MIM modellen op architectuurniveau inzichtelijk te maken en te verbinden. De voorgestelde mapping ziet er op hoofdlijnen als volgt uit:
* Een conceptueel informatiemodel in MIM draait primair om objecttypes die bedoeld zijn om uitdrukking te geven aan soorten dingen in de werkelijkheid. Dat past goed op wat in ArchiMate business objecten zijn. MIM objecttypes worden in ArchiMate daarom uitgedrukt als ArchiMate business objecten.
* Een logisch gegevensmodel in MIM draait primair om gegevensobjecttypes die bedoeld zijn om uitdrukking te geven aan het structureren van soorten gegevens. Dat past goed op wat in ArchiMate data objecten zijn. MIM gegevensobjecttypes worden in ArchiMate daarom uitgedrukt als ArchiMate data objecten.

De definities van de MIM metaklassen en ArchiMate concepten die we aan elkaar relateren zijn niet aan elkaar gelijk. In algemene zin zijn ze dus niet hetzelfde. We stellen dus een meer specifieke interpretatie voor van de ArchiMate concepten. Om die reden is het dan ook nodig om middels specialisatie duidelijk te maken dat betreffende modelelementen de meer specifieke betekenis van MIM volgen. Een ArchiMate business object met als specialisatie "Objecttype" heeft dan de betekenis zoals bedoeld in MIM. Het is voor een specifiek architectuurmodel de vraag in hoeverre alle gemodelleerde business objecten ook deze specialisatie gebruiken. Het is mogelijk om ook business objecten te modelleren die de meer algemene ArchiMate betekenis hanteren. Daarmee zou je een meer algemeen bedrijfsobjectenmodel kunnen relateren aan een specifieker MIM conceptueel informatiemodel. Tegelijkertijd liggen de MIM en ArchiMate definities zo dicht tegen elkaar aan dat er weinig meerwaarde is om dit echt als gescheiden lagen te modelleren. Dit geldt deels ook voor logische gegevensmodellen en ArchiMate data objecten, alhoewel je ook echt andere soorten data objecten zou kunnen modelleren. Denk bijvoorbeeld aan het het modelleren van datasets of registraties als ArchiMate data objecten.  

## Structuur metamodel in ArchiMate

### Kern

| **MIM metaclass**   | **ArchiMate concept**   |
| ------------------- | ----------------------- |
| Objecttype          | Business Object         |
| Attribuutsoort      | Business Object         |
| Gegevensobjecttype  | Data Object             |
| Gegevenstype        | Data Object             |
| Gegevensgroep       | Data Object             |
| Gegevensgroeptype   | Data Object             |
| Generalisatie       | Generalization          |
| Relatiesoort        | Association             |
| Relatieklasse       | Business Object         |


### Datatypen

### Overig

#### Constraint

#### Keuze

#### Packages

## Specificaties metagegevens in ArchiMate



