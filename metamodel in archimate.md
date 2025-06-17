# Metamodel in ArchiMate

Dit hoofdstuk beschrijft de mapping tussen MIM en de ArchiMate modelleertaal.

## Inleiding
Zoals in voorgaande tekst beschreven heeft het waarde heeft om MIM modellen te kunnen uitdrukken in ArchiMate. Het biedt een startpunt voor het opstellen van MIM modellen en maakt het mogelijk om MIM modellen op architectuurniveau inzichtelijk te maken en te verbinden. De voorgestelde mapping ziet er op hoofdlijnen als volgt uit:
* Een conceptueel informatiemodel in MIM draait primair om objecttypes die bedoeld zijn om uitdrukking te geven aan soorten dingen in de werkelijkheid. Dat past goed op wat in ArchiMate een <a>business object</a>is. MIM objecttypes worden in ArchiMate daarom uitgedrukt als ArchiMate business objecten.
* Een logisch gegevensmodel in MIM draait primair om gegevensobjecttypes die bedoeld zijn om uitdrukking te geven aan het structureren van soorten gegevens. Dat past goed op wat in ArchiMate een <a>data object</a> is. MIM gegevensobjecttypes worden in ArchiMate daarom uitgedrukt als ArchiMate data objecten.

De definities van de MIM metaklassen en ArchiMate concepten die we aan elkaar relateren zijn niet aan elkaar gelijk. In algemene zin zijn ze dus niet hetzelfde. We stellen daarom een meer specifieke interpretatie voor van de ArchiMate concepten. Om die reden is het dan ook nodig om middels specialisatie duidelijk te maken dat betreffende modelelementen de meer specifieke betekenis van MIM volgen. Een ArchiMate business object met als specialisatie "Objecttype" heeft dan de betekenis zoals bedoeld in MIM. Het is voor een specifiek architectuurmodel de vraag in hoeverre alle gemodelleerde business objecten ook deze specialisatie gebruiken. Het is natuurlijk ook nog steeds mogelijk om business objecten te modelleren die de meer algemene ArchiMate betekenis hanteren. Daarmee zou je een meer algemeen ArchiMate bedrijfsobjectenmodel kunnen relateren aan een specifieker MIM conceptueel informatiemodel. Tegelijkertijd liggen de MIM en ArchiMate definities zo dicht tegen elkaar aan dat er weinig meerwaarde is om dit echt als gescheiden lagen te modelleren. Dat geldt deels ook voor logische gegevensmodellen en ArchiMate data objecten, alhoewel je ook echt andere soorten data objecten zou kunnen modelleren. Denk bijvoorbeeld aan het het modelleren van datasets of registraties als ArchiMate data objecten.

Een belangrijk aandachtspunt is dat architectuurmodellen ook van nature meer abstract zijn dan informatie/gegevensmodellen. Het is dan ook niet mogelijk en gewenst om het gehele MIM metamodel te mappen op ArchiMate. De vraag is vooral hoever deze mapping gaat. Zo kent bijvoorbeeld ArchiMate 3.2 niet de mogelijkheid om attributen en kardinaliteiten te modelleren. We kiezen er in deze standaard wel voor om attributen te modelleren, omdat daarmee allerlei extra toepassingsmogelijkheden ontstaan. Denk bijvoorbeeld aan het inzichtelijk maken of verbinden van attributen. Een MIM attribuutsoort wordt gemodelleerd als een ArchiMate business object en een MIM gegevenstype wordt gemodelleerd als ArchiMate data object. Dit is in ArchiMate niet optimaal te visualiseren; het leidt al snel tot een heel groot diagram. Het is echter belangrijk om te beseffen dat ArchiMate naast een visualisatie ook een metamodel is en dat een uitwisselstandaard biedt. Los van of je het in een diagram wilt laten zien, kan het waardevol zijn om dit detailniveau wel in een architectuurrepository aan te brengen en/of te gebruiken bij het uitwisselen van architectuurmodellen.

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
De ArchiMate standaard beschrijft zelf niet welke eigenschappen modelelementen kunnen hebben. Daarnaast kent de standaard ook geen datatypen voor eigenschappen. Om die reden worden alle metagegevens van de MIM metaklassen één-op-één worden overgenomen bij ArchiMate modelelementen. Daarbij wordt de letterlijke naam van het metagegeven (zoals bijvoorbeeld "Toelichting") als eigenschap opgenomen bij het ArchiMate modelelement.

Uitzondering op bovenstaande geldt voor de metagegevens "Naam" en "Definitie", waarvoor gebruik wordt gemaakt van de eigenschappen "name" en "documentation" in de ArchiMate uitwisselstandaard [[ArchiMateExchange]]. Die eigenschappe worden in de uitwisselstandaard anders behandeld dan andere eigenschappen.

