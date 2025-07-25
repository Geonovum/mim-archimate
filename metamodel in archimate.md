# Metamodel in ArchiMate

Dit hoofdstuk beschrijft de mapping tussen MIM en de ArchiMate modelleertaal.

## Inleiding
Zoals in voorgaande tekst beschreven heeft het waarde heeft om MIM modellen te kunnen uitdrukken in ArchiMate. Het biedt een startpunt voor het opstellen van MIM modellen en maakt het mogelijk om MIM modellen op architectuurniveau inzichtelijk te maken en te verbinden. De voorgestelde mapping ziet er op hoofdlijnen als volgt uit:
- Een conceptueel informatiemodel in MIM draait primair om objecttypes die bedoeld zijn om uitdrukking te geven aan soorten dingen in de werkelijkheid. Dat past goed op wat in ArchiMate een <a>Business Object</a> (bedrijfsobject) is. MIM objecttypes worden in ArchiMate daarom uitgedrukt als ArchiMate bedriijfsobjecten.
- Een logisch gegevensmodel in MIM draait primair om gegevensobjecttypes die bedoeld zijn om uitdrukking te geven aan het structureren van soorten gegevens. Dat past goed op wat in ArchiMate een <a>Data Object</a> is. MIM gegevensobjecttypes worden in ArchiMate daarom uitgedrukt als ArchiMate data-objecten.

De definities van de MIM meta-classes en ArchiMate elementen die we aan elkaar relateren zijn niet aan elkaar gelijk. Ze zijn  dus niet hetzelfde. We stellen daarom een meer specifieke interpretatie voor van de ArchiMate elementen. Om die reden is het dan ook nodig om middels specialisatie duidelijk te maken dat betreffende modelelementen de meer specifieke betekenis van MIM volgen. Een ArchiMate bedrijfsobject met als specialisatie "Objecttype" heeft dan de betekenis zoals bedoeld in MIM. Het is voor een specifiek architectuurmodel de vraag in hoeverre alle gemodelleerde bedrijfsobjecten ook deze specialisatie gebruiken. Het is natuurlijk ook nog steeds mogelijk om bedrijfsobjecten te modelleren die de meer algemene ArchiMate betekenis hanteren. Daarmee zou je een meer algemeen ArchiMate bedrijfsobjectmodel kunnen relateren aan een specifieker MIM conceptueel informatiemodel. Tegelijkertijd liggen de MIM en ArchiMate definities zo dicht tegen elkaar aan dat er weinig meerwaarde is om dit echt als gescheiden lagen te modelleren. Dat geldt deels ook voor logische gegevensmodellen en ArchiMate data-objecten, alhoewel je ook echt andere soorten data-objecten zou kunnen modelleren. Denk bijvoorbeeld aan het het modelleren van datasets of registraties als ArchiMate data-objecten.

Een belangrijk aandachtspunt is dat architectuurmodellen ook van nature meer abstract zijn dan informatie/gegevensmodellen. Het is dan ook de vraag hoe ver de mapping van MIM op ArchiMate zou moeten gaan. Zo kent bijvoorbeeld ArchiMate 3.2 niet een standaard manier om attributen en kardinaliteiten te modelleren en visualiseren. We kiezen er desondanks voor om toch de gehele standaard over te nemen in ArchiMate, omdat daarmee allerlei extra toepassingsmogelijkheden ontstaan. Denk bijvoorbeeld aan het inzichtelijk maken of verbinden van attributen. Het is daarom wel waardevol om ook attributen te kunnen modelleren in ArchiMate, ondanks dat de visualisatie ervan al snel leidt tot een groot diagram. Het is uiteindelijk aan een individuele gebruiker om te bepalen hoe ver deze wil gaan in het gebruik van de mapping. Deze standaard biedt vooral mogelijkheden. De ArchiMate standaard is naast een visualisatie vooral een metamodel en er is ook een uitwisselstandaard. Los van of je het in een diagram wilt laten zien, kan het waardevol zijn om dit detailniveau wel in een architectuurrepository aan te brengen en/of te gebruiken bij het uitwisselen van architectuurmodellen.

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
| Externe koppeling   | Gegevensobjecttype       | Externe koppeling  |

Een relatiesoort kent in ArchiMate drie mogelijkheden: association, aggregation of composition. Er is geen specialisatie van deze relatie nodig omdat de betekenis gebonden is aan één van deze drie mogelijkheden. 

Een generalisatie-relatie in MIM heeft in ArchiMate alleen een inverse tegenhanger (Specialization). Er is ook geen specialisatie van deze relatie nodig omdat er maar één logische betekenis is voor deze relatie.

Voor de bindingen tussen de modelelementen wordt gebruik gemaakt van de in MIM voorgedefinieerde bindingen zoals "heeft attribuut" en "heeft gegevensgroep". Hiervoor worden specialisaties van associatie-, aggregatie- of compositierelaties gebruikt met de volledige naam van de binding. Dit geldt alleen voor bindingen die niet automatisch voortvloeien uit de betekenis van elementen en relaties in ArchiMate.  

| **MIM binding**          | **ArchiMate element**   | **Specialisatie**        |
| ------------------------ | ----------------------- | ------------------------ |
| heeft attribuut          | Aggregation             | heeft attribuut          |
| heeft gegevenstype       | Aggregation             | heeft gegevenstype       |
| heeft gegevensgroep      | Aggregation             | heeft gegevensgroep      |
| heeft gegevensgroeptype  | Aggregation             | heeft gegevensgroeptype  |
| heeft datatype           | Aggregation             | heeft dataype            |
| verwijst naar supertype  | Specialization          | \-                       |
| heeft relatiesoort       | Association, Aggregation of Composition | \-       |
| heeft externe koppeling  | Composition             | heeft externe koppeling  |

### Datatypen

![Datatypen](/mim-archimate/media/datatypen.png)

| **MIM metaclass**       | **ArchiMate element** | **Specialisatie** |
| ----------------------- | --------------------- | ----------------- |
| Datatype                | Data Object | Datatype | 
| Primitief datatype      | Data Object | Primitief datatype |
| Gestructureerd datatype | Data Object | Gestructureerd datatype |
| Data-element            | Data Object | Data-element |
| Enumeratie              | Data Object | Enumeratie |
| Enumeratiewaarde        | Data Object | Enumeratiewaarde |
| Referentielijst         | Data Object | Referentielijst |
| Referentie-element      | Data Object | Referentie-element |
| Codelijst               | Data Object | Codelijst |

| **MIM binding**          | **ArchiMate element**   | **Specialisatie**        |
| ------------------------ | ----------------------- | ------------------------ |
| heeft data-element       | Composition             | heeft data-element       |
| bevat enumeratiewaarde   | Composition             | bevat enumeratiewaarde   |
| bevat referentie-element | Composition             | bevat referentie-element |

### Overig

#### Constraint

![Constraint](/mim-archimate/media/constraint.png)

| **MIM metaclass** | **ArchiMate element** | **Specialisatie** |
|-------------------|-----------------------|-------------------|
| Constraint        | Constraint            | \-                |

| **MIM binding**          | **ArchiMate element**   | **Specialisatie**        |
| ------------------------ | ----------------------- | ------------------------ |
| heeft constraint         | Association             | \-                       |

#### Keuze

Het modelelement keuze bepaalt dat er meerdere opties mogelijk zijn, waarvan er één gekozen moet worden. Keuzes worden vastgelegd als ArchiMate data-object. 

| **MIM metaclass**       | **ArchiMate element** | **Specialisatie** |
| ----------------------- | --------------------- | ----------------- |
| Keuze                   | Data Object           | Keuze             | 

| **MIM binding**          | **ArchiMate element**   | **Specialisatie**        |
| ------------------------ | ----------------------- | ------------------------ |
| heeft datatypekeuze      | Aggregation             | heeft datatypekeuze      |
| heeft gegevenstypekeuze  | Aggregation             | heeft gegevenstypekeuze  |
| heeft keuzegegevenstype  | Aggregation             | heeft keuzegegevenstype  |
| heeft relatiedoelkeuze   | Association             | heeft relatiedoelkeuze   |
| heeft relatiesoortkeuze  | Association             | heeft relatiesoortkeuze  |   

Er zijn vijf situaties mogelijk waarin een keuze toegepast wordt:

- Use case 1: een keuze tussen datatypen
- Use case 2: een keuze tussen twee of meer gegevenstypen
- Use case 3: een keuze tussen meerdere manieren om één betekenisvol gegevenstype in te vullen
- Use case 4: een keuze tussen relatiedoelen, als nadere invulling van één betekenisvolle relatiesoort
- Use case 5: een keuze tussen relatiesoorten/relatierollen (elk afzonderlijk betekenisvol)

Voor elke toepassing geldt een aparte subset van het metamodel. 

**Use case 1: Keuze tussen datatypen**

In deze use-case wordt een gegevenstype van een gegevensobjecttype of gegevensgroeptype verbonden aan een keuze middels een aggregatierelatie met specialisatie "heeft datatypekeuze". De keuze zelf wordt vervolgens met een aggregatierelatie verbonden aan 2 of meer datatypes waaruit gekozen moet worden.

![Datatypekeuze](/mim-archimate/media/datatypekeuze.png)

**Use case 2: Keuze tussen 2 of meer gegevenstypen**

In deze use-case wordt een gegevensobjecttype of gegevensgroeptype verbonden aan een keuze middels een aggregatierelatie met specialisatie "heeft gegevenstypekeuze". De keuze zelf wordt vervolgens met een aggregatierelatie verbonden aan 2 of meer gegevenstypes waaruit gekozen moet worden.

![Gegevenstypekeuze](/mim-archimate/media/gegevenstypekeuze.png)

**Use case 3: Keuze tussen meerdere manieren om 1 betekenisvol gegevenstype in te vullen**

Deze use case volgt hetzelfde patroon als de voorgaande use case.

VRAAG: Wat is nu fundamenteel anders in use-case 2 en 3? In de LD mapping worden ze ook niet van elkaar onderscheiden.

**Use case 4: Keuze tussen relatiedoelen, als nadere invulling van 1 betekenisvolle relatiesoort**

In deze use-case wordt een relatiesoort van een gegevensobjecttype of gegevensgroeptype verbonden aan een keuze middels een associatierelatie met specialisatie "heeft relatiedoelkeuze". De naam van deze relatie geeft de betekenis ervan weer. De keuze zelf wordt vervolgens middels een aggregatierelatie verbonden aan 2 of meer gegevensobjecttypes.

![Relatiedoelkeuze](/mim-archimate/media/relatiedoelkeuze.png)

**Use case 5: Keuze tussen relatiesoorten/relatierollen (elk afzonderlijk betekenisvol)**

In deze use-case wordt een relatiesoort van een gegevensobjecttype of gegevensgroeptype verbonden aan een keuze middels een associatierelatie met specialisatie "heeft relatiesoortkeuze". De naam van deze relatie is niet betekenisvol. De keuze zelf wordt vervolgens middels een aggregatierelatie (inclusief eventuele relatierollen) verbonden aan 2 of meer gegevensobjecttypes. 

![Relatiesoortkeuze](/mim-archimate/media/relatiesoortkeuze.png)

ISSUE: In de UML mapping staat "keuzerelatiedoel" in plaats van "relatiekeuzedoel"

#### Relatierol

![Relatierol](/mim-archimate/media/relatierol.png)

| **MIM metaclass**   | **ArchiMate element**    | **Specialisatie**  |
| ------------------- | ------------------------ | ------------------ |
| Relatierol          | Data Object              | Relatierol         |

Relatierollen worden gerepresenteerd als ArchiMate data-objecten, die een associatierelatie hebben met de relatie waarop ze betrekking hebben. Per relatierol wordt bij deze relatie middels een specialisatie aangegeven of het van het type "heeft bron" of "heeft doel" is om aan te geven dat ze betrekking hebben op respectievelijk de bron of het doel.

#### Relatieklasse

![Relatieklasse](/mim-archimate/media/relatieklasse.png)

| **MIM metaclass**   | **ArchiMate element**    | **Specialisatie**  |
| ------------------- | ------------------------ | ------------------ |
| Relatieklasse       | Business Object          | Relatieklasse      |

Relatieklassen worden gerepesenteerd als ArchiMate bedrijfsobjecten, die een associatierelatie hebben met de relatie waarop ze betrekking hebben.

#### Packages

![Domein](/mim-archimate/media/domein.png)

| **MIM metaclass**   | **ArchiMate element**    | **Specialisatie**  |
| ------------------- | ------------------------ | ------------------ |
| Informatiemodel     | Grouping                 | Informatiemodel    |
| Domein              | Grouping                 | Domein             |
| Extern              | Grouping                 | Extern             |
| View                | Grouping                 | View               |

| **MIM binding**          | **ArchiMate element**   | **Specialisatie**        |
| ------------------------ | ----------------------- | ------------------------ |
| bevat modelelement       | Composition             | \-                       |

## Specificaties metagegevens in ArchiMate
De ArchiMate standaard beschrijft zelf niet welke eigenschappen modelelementen kunnen hebben. Daarnaast kent de standaard ook geen datatypen voor eigenschappen. Om die reden worden alle metagegevens van de MIM metaklassen één-op-één worden overgenomen bij ArchiMate modelelementen. Daarbij wordt de letterlijke naam van het metagegeven (zoals bijvoorbeeld "Toelichting") als eigenschap opgenomen bij het ArchiMate modelelement.

Uitzondering op bovenstaande geldt voor de metagegevens "Naam" en "Definitie", waarvoor gebruik wordt gemaakt van de eigenschappen "name" en "documentation" in de ArchiMate uitwisselstandaard [[ArchiMateExchange]]. Die eigenschappen worden in de uitwisselstandaard anders behandeld dan andere eigenschappen.
