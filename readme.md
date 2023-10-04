# Kwaliteit boven kwantiteit; Sonarqube

*Martijn Gerritsen*, oktober 2023

<img style="z-index:99999999" align="right" width="400" src="images/sonarqube-logo-blue.png"/>
<hr>

Ik volg momenteel de minor DevOps op de HAN. Voor deze minor moet ik een onderzoek doen naar een DevOps tool. Ik heb gekozen voor Sonarqube. In dit document zal ik mijn onderzoek beschrijven.

Het doel van dit onderzoek is om te bestuderen/testen of Sonarqube een goede tool is om te gebruiken in een DevOps omgeving. Ook wordt er gekeken of deze tool eventueel gebruikt kan worden in een kleinschalig DevOps project. In deze context zou Sonarqube gebruikt kunnen worden om de kwaliteit van de code te verbeteren.

Allereerst een korte uitleg over wat Sonarqube is, hierna volgt een uitleg over  de integratie van Sonarqube met DevOps-tools en -workflows voor CI/CD, vervolgens wordt er gekeken naar de voor- en nadelen van Sonarqube en tot slot wordt er een beknopte startup/configuratie handleiding gegeven.

## Wat is Sonarqube?
SonarQube is een krachtige tool voor statische code-analyse die een essentiële rol speelt binnen het bredere DevOps-ecosysteem. Het fungeert als een kritische hoeksteen voor het waarborgen van codekwaliteit en beveiliging in softwareontwikkelingsprojecten. SonarQube analyseert de broncode van applicaties op zoek naar potentieel problematische patronen, codegebreken en veiligheidskwetsbaarheden. Door dit in een vroeg stadium van de ontwikkelingscyclus te doen, helpt het DevOps-teams om sneller en effectiever fouten op te sporen en op te lossen, waardoor de totale kosten van softwareonderhoud worden verminderd en de kwaliteit van de software wordt verbeterd. Daarnaast biedt SonarQube uitgebreide rapportage- en monitoringfuncties, waardoor DevOps-teams in staat zijn om hun codebase continu te verbeteren en te voldoen aan de best practices op het gebied van codekwaliteit en beveiliging. Kortom, SonarQube speelt een cruciale rol in het ondersteunen van de DevOps-praktijken door te zorgen voor een solide basis van codekwaliteit en beveiliging gedurende de hele levenscyclus van softwareontwikkeling.

## Hoe legt Sonarqube de integratie met DevOps-tools en -workflows voor CI/CD?
SonarQube integreert naadloos met DevOps-tools en -workflows voor Continuous Integration/Continuous Deployment (CI/CD). Door plug-ins en extensies te bieden voor populaire CI/CD-platforms zoals Jenkins, Azure DevOps, en GitLab, maakt SonarQube het mogelijk om code-analyses automatisch uit te voeren als onderdeel van de CI/CD-pijplijnen. Dit betekent dat bij elke codecommit of build, SonarQube de code kan analyseren en direct feedback kan genereren aan de ontwikkelaars over codekwaliteit, beveiligingsproblemen en andere kwetsbaarheden. Deze geautomatiseerde integratie zorgt voor snelle feedbackloops en stelt ontwikkelingsteams in staat om problemen in een vroeg stadium te identificeren en op te lossen. Het maakt deel uit van de DevOps-filosofie om de ontwikkelings- en operationele aspecten van softwareontwikkeling te verenigen, en SonarQube draagt bij aan deze convergentie door ontwikkelaars en operationele teams te voorzien van waardevolle inzichten om de codekwaliteit en veiligheid te waarborgen in een snel bewegende CI/CD-omgeving.

## Wat zijn de voor- en nadelen van Sonarqube?

### Voordelen:

- Codekwaliteit en beveiliging: SonarQube identificeert codekwaliteitsproblemen en beveiligingslekken, wat bijdraagt aan robuustere en veiligere software in een DevOps-context.
- Vroege foutopsporing: Door vroegtijdige code-analyse kunnen DevOps-teams problemen in een vroeg stadium aanpakken, wat de totale onderhoudskosten vermindert en de doorlooptijd versnelt.
- Geautomatiseerde integratie: SonarQube integreert naadloos met CI/CD-tools en -workflows, waardoor snelle feedbackloops ontstaan en ontwikkelaars direct inzicht krijgen in codekwaliteit en beveiliging.
- Samenwerking: Het faciliteert de samenwerking tussen ontwikkeling en operations door gezamenlijke inzichten te bieden, wat in lijn is met de samenwerkingsdoelen van DevOps.

### Nadelen:

- Foutieve meldingen: SonarQube kan soms valse positieven genereren, wat tot verwarring en tijdsverspilling kan leiden voor ontwikkelaars in een snelle DevOps-omgeving.
- Configuratiecomplexiteit: Het configureren van SonarQube voor specifieke projecten kan complex zijn en vereist aandacht, wat extra beheerwerk met zich meebrengt in een DevOps-ecosysteem.
- Mogelijke vertraging: Onjuist gebruik van SonarQube kan ontwikkelaars afleiden van hun hoofdtaken, waardoor ontwikkelingstijden langer worden in plaats van korter in een DevOps-perspectief.
- Hulpmiddelenharmonisatie: Het kan nodig zijn om de DevOps-toolstack aan te passen of te harmoniseren om optimaal van SonarQube te profiteren, wat extra inspanningen vereist voor integratie in bestaande workflows.

## Je project koppelen aan Sonarqube
Nu het duidelijk is wat Sonarqube is en kan doen, is het tijd om te kijken hoe je een project kan koppelen aan Sonarqube. In dit voorbeeld zal ik een project koppelen aan Sonarqube en de resultaten bekijken.

### Stap 0: Vereisten
Om Sonarqube te kunnen gebruiken heb je het volgende nodig:
- Een JDK (Java Development Kit) versie 11 of hoger.
- Minimaal 2GB RAM beschikbaar.
- Minimaal 1GB vrije schijfruimte.

### Stap 1: Sonarqube downloaden
Via de officiële website van Sonarqube kan je de laatste versie [downloaden](https://www.sonarqube.org/downloads/). In dit voorbeeld is de Community Edition gebruikt.

### Stap 2: Sonarqube configureren
Na het downloaden van Sonarqube moet het geconfigureerd worden. Doe dit door het volgende te doen:
- Pak het ZIP-bestand uit naar de gewenste locatie.
- Open het bestand `sonarqube-<versie>/conf/sonar.properties` en pas de volgende regels aan:
    - `sonar.jdbc.username` en `sonar.jdbc.password` om de databasegebruikersnaam en het wachtwoord in te stellen.
    - `sonar.jdbc.url` om de JDBC-URL van de database in te stellen.
    - Sla het bestand op.

### Stap 3: Sonarqube starten
Om Sonarqube te starten moet je het volgende doen:
- Open een terminal en navigeer naar de uitgepakte map.
- Start de server met het commando `bin/[OS]/sonar.sh console` (Linux) of `bin/[OS]/StartSonar.bat` (Windows).
- Wacht tot de server is gestart. De voortgang kan gecontroleerd worden door het bestand `logs/sonar.log` te bekijken.

### Stap 4: Sonarqube openen in de browser
Om Sonarqube te openen in de browser moet je het volgende doen:
- Open een browser en ga naar `http://localhost:9000`.
- Log in met de standaard inloggegevens:
    - Gebruikersnaam: `admin`
    - Wachtwoord: `admin`
- Wijzig hierna je wachtwoord, dit wordt aangegeven.


### Stap 5: Project toevoegen
Om een project toe te voegen moet je het volgende doen:
- Klik op het plusje in de linkerbovenhoek.
- Klik op `Create new project`.
- Voeg je eigen project toe door de instructies te volgen.

# Conclusie
SonarQube is een krachtige tool voor statische code-analyse die een essentiële rol speelt binnen het bredere DevOps-ecosysteem. Het fungeert als een kritische hoeksteen voor het waarborgen van codekwaliteit en beveiliging in softwareontwikkelingsprojecten. SonarQube analyseert de broncode van applicaties op zoek naar potentieel problematische patronen, codegebreken en veiligheidskwetsbaarheden. Door dit in een vroeg stadium van de ontwikkelingscyclus te doen, helpt het DevOps-teams om sneller en effectiever fouten op te sporen en op te lossen, waardoor de totale kosten van softwareonderhoud worden verminderd en de kwaliteit van de software wordt verbeterd. Daarnaast biedt SonarQube uitgebreide rapportage- en monitoringfuncties, waardoor DevOps-teams in staat zijn om hun codebase continu te verbeteren en te voldoen aan de best practices op het gebied van codekwaliteit en beveiliging. Kortom, SonarQube speelt een cruciale rol in het ondersteunen van de DevOps-praktijken door te zorgen voor een solide basis van codekwaliteit en beveiliging gedurende de hele levenscyclus van softwareontwikkeling.

# Bronnen
- ChatGPT. (z.d.). ChatGPT. https://chat.openai.com/
- https://docs.sonarsource.com/sonarqube/latest/