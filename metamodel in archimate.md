# Metamodel in ArchiMate

Dit hoofdstuk beschrijft de mapping tussen MIM en de ArchiMate modelleertaal.

## Inleiding
Zoals in voorgaande tekst beschreven heeft het waarde heeft om MIM modellen te kunnen uitdrukken in ArchiMate. Het biedt een startpunt voor het opstellen van MIM modellen en maakt het mogelijk om MIM modellen op architectuurniveau inzichtelijk te maken en te verbinden. De voorgestelde mapping ziet er op hoofdlijnen als volgt uit:
- Een conceptueel informatiemodel in MIM draait primair om objecttypes die bedoeld zijn om uitdrukking te geven aan soorten dingen in de werkelijkheid. Dat past goed op wat in ArchiMate een <a>business object</a>is. MIM objecttypes worden in ArchiMate daarom uitgedrukt als ArchiMate business objecten.
- Een logisch gegevensmodel in MIM draait primair om gegevensobjecttypes die bedoeld zijn om uitdrukking te geven aan het structureren van soorten gegevens. Dat past goed op wat in ArchiMate een <a>data object</a> is. MIM gegevensobjecttypes worden in ArchiMate daarom uitgedrukt als ArchiMate data objecten.

De definities van de MIM metaklassen en ArchiMate elementen die we aan elkaar relateren zijn niet aan elkaar gelijk. In algemene zin zijn ze dus niet hetzelfde. We stellen daarom een meer specifieke interpretatie voor van de ArchiMate elementen. Om die reden is het dan ook nodig om middels specialisatie duidelijk te maken dat betreffende modelelementen de meer specifieke betekenis van MIM volgen. Een ArchiMate business object met als specialisatie "Objecttype" heeft dan de betekenis zoals bedoeld in MIM. Het is voor een specifiek architectuurmodel de vraag in hoeverre alle gemodelleerde business objecten ook deze specialisatie gebruiken. Het is natuurlijk ook nog steeds mogelijk om business objecten te modelleren die de meer algemene ArchiMate betekenis hanteren. Daarmee zou je een meer algemeen ArchiMate business object model kunnen relateren aan een specifieker MIM conceptueel informatiemodel. Tegelijkertijd liggen de MIM en ArchiMate definities zo dicht tegen elkaar aan dat er weinig meerwaarde is om dit echt als gescheiden lagen te modelleren. Dat geldt deels ook voor logische gegevensmodellen en ArchiMate data objecten, alhoewel je ook echt andere soorten data objecten zou kunnen modelleren. Denk bijvoorbeeld aan het het modelleren van datasets of registraties als ArchiMate data objecten.

Een belangrijk aandachtspunt is dat architectuurmodellen ook van nature meer abstract zijn dan informatie/gegevensmodellen. Het is dan ook niet mogelijk en gewenst om het gehele MIM metamodel te mappen op ArchiMate. De vraag is vooral hoever deze mapping gaat. Zo kent bijvoorbeeld ArchiMate 3.2 niet de mogelijkheid om attributen en kardinaliteiten te modelleren (anders dan ze in zelfgedefinieerde eigenschappen van modelelementen uit te drukken). We kiezen er in deze standaard wel voor om attributen te modelleren, omdat daarmee allerlei extra toepassingsmogelijkheden ontstaan. Denk bijvoorbeeld aan het inzichtelijk maken of verbinden van attributen. Een MIM attribuutsoort wordt gemodelleerd als een ArchiMate business object en een MIM gegevenstype wordt gemodelleerd als ArchiMate data object. Dit is in ArchiMate niet optimaal te visualiseren; het leidt al snel tot een heel groot diagram. Het is echter belangrijk om te beseffen dat ArchiMate naast een visualisatie ook een metamodel is en dat een uitwisselstandaard biedt. Los van of je het in een diagram wilt laten zien, kan het waardevol zijn om dit detailniveau wel in een architectuurrepository aan te brengen en/of te gebruiken bij het uitwisselen van architectuurmodellen.

We kiezen er in deze standaard voor om de volgende MIM metaclasses <u>niet</u> te modelleren in ArchiMate:
- n.t.b.

## Structuur metamodel in ArchiMate

### Kern
![Kern](/mim-archimate/media/kern.png)

Er is bewust voor gekozen om in het diagram de relatie-gerelateerde meta-classes in MIM niet te tonen als aparte entiteiten. Zij worden verderop in dit document verder uitgewerkt.

De volgende tabel beschrijft hoe de metaclasses in de kern van MIM zich verhouden tot de te gebruiken ArchiMate elementen en welke specialisaties moeten worden aangebracht in de ArchiMate elementen om ze de betekenis uit MIM te geven. 

| **MIM metaclass**   | **ArchiMate element**    | **Specialisatie**  |
| ------------------- | ------------------------ | ------------------ |
| Objecttype          | Business Object          | Objecttype         |
| Attribuutsoort      | Business Object          | Attribuutsoort     |
| Gegevensobjecttype  | Data Object              | Gegevensobjecttype |
| Gegevenstype        | Data Object              | Gegevenstype       |
| Gegevensgroep       | Data Object              | Gegevensgroep      |
| Gegevensgroeptype   | Data Object              | Gegevensgroeptype  |
| Generalisatie       | Specialization (inverse) | \-                 |
| Relatiesoort        | Association, Aggregation of Composition | \-       |
| Relatieklasse       | Business Object          | Relatieklasse      |
| Externe koppeling   | Gegevensobjecttype       | Externe koppeling  |

Een relatiesoort kent in ArchiMate drie mogelijkheden: association, aggregation of composition. Er is geen specialisatie van deze relatie nodig omdat de betekenis deze gebonden is één van deze drie mogelijkheden. 

Een generalisatie-relatie in MIM heeft in ArchiMate alleen een inverse tegenhanger (Specialization). Er is ook geen specialisatie van deze relatie nodig omdat er maar één logische betekenis is voor deze relatie.

Voor de bindingen tussen de modelelementen wordt gebruik gemaakt van de in MIM voorgedefinieerde bindingen zoals "heeft attribuut" en "heeft gegevensgroep". Hiervoor worden specialisaties van associatie-, aggregatie- of compositierelaties gebruikt met de volledige naam van de binding. Dit geldt alleen voor bindingen die niet automatisch voortvloeien uit de betekenis van elementen en relaties in ArchiMate.  

| **MIM binding**          | **ArchiMate element**   | **Specialisatie**        |
| ------------------------ | ----------------------- | ------------------------ |
| heeft attribuut          | Aggregation             | heeft attribuut          |
| heeft gegevenstype       | Aggregation             | heeft gegevenstype       |
| heeft gegevensgroep      | Aggregation             | heeft gegevensgroep      |
| heeft gegevensgroeptype  | Aggregation             | heeft gegevensgroeptype  |
| verwijst naar supertype  | Specialization          | \-                       |
| heeft relatiesoort       | Association, Aggregation of Composition | \-       |
| heeft externe koppeling  | Composition             | heeft externe koppeling  |

### Datatypen

![Datatype](/mim-archimate/media/datatype.png)

| **MIM metaclass**       | **ArchiMate element** | **Specialisatie** |
| ----------------------- | --------------------- | ----------------- |
| Datatype                | Data Object | Datatype | 
| Primitief datatype      | Data Object | Primitief datatype |
| Gestructureerd datatype | Data Object | Gestructureerd datatype |
| Data-element            | Data Object | Data-element |
| Enumeratie              | Data Object | Enumeratie |
| Enumeratiewaarde        | Data Object | Enumeratiewaarde |
| Referentielijst         | Data Object | Enumeratiewaarde |
| Referentie-element      | Data Object | Referentie-element |
| Codelijst               | Data Object | Codelijst |


| **MIM binding**          | **ArchiMate element**   | **Specialisatie**        |
| ------------------------ | ----------------------- | ------------------------ |
| heeft datatype           | Aggregation             | heeft dataype            |
| heeft data-element       | Composition             | heeft data-element       |

### Overig

#### Constraint

| **MIM metaclass** | **ArchiMate element** | **Specialisatie** |
|-------------------|-----------------------|-------------------|
| Constraint        | Constraint            | \-                |


| **MIM binding**          | **ArchiMate element**   | **Specialisatie**        |
| ------------------------ | ----------------------- | ------------------------ |
| heeft constraint         | Association             | \-                       |

#### Keuze

| **MIM metaclass**       | **ArchiMate element** | **Specialisatie** |
| ----------------------- | --------------------- | ----------------- |
| Keuze                   | Data Object           | Keuze             | 

Het modelelement keuze bepaalt dat er meerdere opties mogelijk zijn, waarvan er één gekozen moet worden. 
Er zijn vijf situaties mogelijk waarin een keuze toegepast wordt.

- Use case 1: een keuze tussen datatypen
- Use case 2: een keuze tussen twee of meer attribuutsoorten (@gegevenstypen?@)
- Use case 3: een keuze tussen meerdere manieren om één betekenisvol attribuutsoort (@gegevenstype@?) in te vullen
- Use case 4: een keuze tussen relatiedoelen, als nadere invulling van één betekenisvolle relatiesoort
- Use case 5: een keuze tussen relatiesoorten/relatierollen (elk afzonderlijk betekenisvol)

Voor elke toepassing geldt een aparte subset van het metamodel. 


- Use case 1: een relatie naar een "Keuze"

| **MIM binding**          | **ArchiMate element**   | **Specialisatie**        |
| ------------------------ | ----------------------- | ------------------------ |
| heeft datatypekeuze      | Aggregation             | heeft datatypekeuze      |
| heeft attribuutkeuze     | Aggregation             | heeft attribuutkeuze     |
| heeft keuzeattribuut     | Aggregation             | heeft keuzeattribuut     |
| heeft relatiedoelkeuze   | Aggregation             | heeft relatiedoelkeuze   |
| heeft relatiesoortkeuze  | Aggregation             | heeft relatiesoortkeuze  |   

#### Relatierol

#### Waardelijsten

| **MIM binding**          | **ArchiMate element**   | **Specialisatie**        |
| ------------------------ | ----------------------- | ------------------------ |
| bevat enumeratiewaarde   | Composition             | bevat enumeratiewaarde   |
| bevat referentie-element | Composition             | bevat referentie-element |

#### Packages

| **MIM binding**          | **ArchiMate element**   | **Specialisatie**        |
| ------------------------ | ----------------------- | ------------------------ |
| bevat modelelement       | Composition             | \-                       |


## Specificaties metagegevens in ArchiMate
De ArchiMate standaard beschrijft zelf niet welke eigenschappen modelelementen kunnen hebben. Daarnaast kent de standaard ook geen datatypen voor eigenschappen. Om die reden worden alle metagegevens van de MIM metaklassen één-op-één worden overgenomen bij ArchiMate modelelementen. Daarbij wordt de letterlijke naam van het metagegeven (zoals bijvoorbeeld "Toelichting") als eigenschap opgenomen bij het ArchiMate modelelement.

Uitzondering op bovenstaande geldt voor de metagegevens "Naam" en "Definitie", waarvoor gebruik wordt gemaakt van de eigenschappen "name" en "documentation" in de ArchiMate uitwisselstandaard [[ArchiMateExchange]]. Die eigenschappe worden in de uitwisselstandaard anders behandeld dan andere eigenschappen.



[def]: ttps://geonovum.github.io/mim-archimate/media/kern.pn