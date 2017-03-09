---
title: "Application Lifecycle Management (ALM) mit Unity-Apps | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "tgt-pltfrm-cross-plat"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2dc61e63-9ba2-4c16-b1ad-f46249e576b6
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "crdun"
manager: "crdun"
---
# Application Lifecycle Management (ALM) mit Unity-Apps
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das Entwickeln von Apps für moderne Plattformen umfasst viele weitere Aktivitäten neben dem Schreiben von Code. Diese als DevOps (Development + Operations) bezeichneten Aktivitäten decken den gesamten Lebenszyklus der App ab. Dazu gehören das Planen und Nachverfolgen der Arbeit, das Entwickeln und Implementieren von Code, das Verwalten eines Quellcoderepositorys, das Ausführen von Builds, das Verwalten von Continuous Integration und Deployment, das Testen (einschließlich Komponententests und Tests der Benutzeroberfläche), das Durchführen verschiedener Formen der Diagnose in Entwicklungs- und Produktionsumgebungen und das Überwachen der App-Leistung und des Benutzerverhaltens in Echtzeit über Telemetrie und Analysen.  
  
 Visual Studio bietet zusammen mit Visual Studio Team Services und Team Foundation Server bieten eine Vielzahl von DevOps-Funktionen, die auch als Application Lifecycle Management oder ALM bezeichnet. Viele dieser gelten für plattformübergreifende Projekte, einschließlich Spiele und faszinierende grafisch apps mit Unity erstellt – insbesondere bei Verwendung von c# als Skriptsprache. Da Unity über eine eigene Entwicklungsumgebung und ein eigenes Laufzeitmodul verfügt, können viele ALM-Funktionen allerdings nicht so wie bei anderen Arten von Projekten verwendet werden, die in Visual Studio erstellt wurden.  
  
 Die folgenden Tabellen identifiziert, wie Visual Studio-ALM-Funktionen gelten bzw. nicht gelten, bei der Arbeit mit Unity. Ausführliche Informationen über die Funktionen selbst finden Sie in der verknüpften Dokumentation.  
  
## <a name="agile-tools"></a>Agile-Tools  
 Referenzlink: **[Arbeit](../Topic/Track%20work%20using%20VSTS%20or%20TFS.md)** (mit Visual Studio Team Services oder TFS, einschließlich Team Explorer Everywhere)  
  
 Allgemeine Anmerkung: sämtliche planungs- und Nachverfolgungsfeatures sind unabhängig von Projekttyp und Programmiersprache.  
  
|Funktion|Unterstützt von Unity|Zusätzliche Kommentare|  
|-------------|--------------------------|-------------------------|  
|Verwalten von Rückständen und Sprints|Ja||  
|Arbeitsüberwachung|Ja||  
|Teamraumzusammenarbeit|Ja||  
|Kanban-Boards|Ja||  
|Berichte und Visualisierung des Fortschritts|Ja||  
  
## <a name="modeling"></a>Modellierung  
 Referenzlink: **[Analysieren und Modellieren der Architektur](../modeling/analyze-and-model-your-architecture.md)**  
  
 Allgemeine Anmerkung: Obwohl diese Funktionen entweder unabhängig von der Programmiersprache oder mit .NET-Sprachen wie c# funktionieren, werden sie in ein traditionelles anwendungsparadigma mit Objekthierarchien und klassenbeziehungen. Für das Entwerfen eines Spiels in Unity ist ein anderes Paradigma erforderlich, nämlich die Beziehungen von grafischen Objekten, Sounds, Shadern, Skripts usw. Aus diesem Grund sind die Modellierungsdiagrammtools von Visual Studio für die Gesamtheit eines Unity-Projekts nicht von besonderer Bedeutung. Sie können möglicherweise zum Verwalten von Beziehungen innerhalb von C#-Skripts verwendet werden, aber das ist nur ein Teil des Ganzen.  
  
|Funktion|Unterstützt von Unity|Zusätzliche Kommentare|  
|-------------|--------------------------|-------------------------|  
|Sequenzdiagramme|Nein||  
|Abhängigkeitsdiagramme|Nein||  
|Aufrufhierarchie|Nein||  
|Klassen-Designer|Nein||  
|Architektur-Explorer|Nein||  
|UML-Diagramme (Anwendungsfall, Aktivität, Klasse, Komponente, Sequenz und DSL)|Nein||  
|Ebenendiagramme|Nein||  
|Ebenenüberprüfung|Nein||  
  
## <a name="code"></a>Code  
  
|Funktion|Unterstützt von Unity|Zusätzliche Kommentare|  
|-------------|--------------------------|-------------------------|  
|[Verwenden von Team Foundation Version Control](../Topic/Use%20Team%20Foundation%20Version%20Control.md) oder Visual Studio Team Services|Ja|Unity-Projekte sind einfach eine Sammlung von Dateien, die in Versionskontrollsysteme wie jedes andere Projekt eingefügt werden kann, aber es gibt einige besondere Aspekte, die nach dieser Tabelle beschrieben.|  
|[Erste Schritte mit Git in Team Services](../Topic/Use%20Visual%20Studio%20with%20Git.md)|Ja|Siehe Hinweise nach der Tabelle.|  
|[Code Analysis/verbessern Codequalität (Verweise, vorgeschlagene Änderungen usw.).](../test/improve-code-quality.md)|Ja||  
|[Ändern von Code und andere Verläufe ermitteln](../ide/find-code-changes-and-other-history-with-codelens.md)|Ja||  
|[Verwenden von Code Maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md)|Ja||  
  
 Besonderheiten bei der Versionskontrolle mit Unity:  
  
1.  Unity überwacht Metadaten über Spielressourcen in einer einzelnen, nicht transparenten Bibliothek, die standardmäßig ausgeblendet ist. Damit Dateien und Metadaten synchron bleiben, müssen die Metadaten sichtbar gemacht und in besser verwaltbaren Blöcken gespeichert werden. Weitere Informationen finden Sie unter [mithilfe von externen Version Control Systems with Unity](http://docs.unity3d.com/Manual/ExternalVersionControlSystemSupport.html) (Unity-Dokumentation).  
  
2.  Nicht alle Dateien und Ordner in einem Unity-Projekt eignen sich für die Quellcodeverwaltung, wie auch im obenstehenden Link beschrieben wird. Die Assets- und ProjectSettings-Ordner sollten hinzugefügt werden, nicht aber die Library- und Temp-Ordner. Eine zusätzliche Liste generierter Dateien, die nicht in die quellcodeverwaltung würden, finden Sie im Abschnitt [Verwendung von Git für Unity3D Source Control?](http://stackoverflow.com/questions/18225126/how-to-use-git-for-unity3d-source-control) auf StackOverflow. Viele Entwickler haben zu diesem Thema auch unabhängig Blog-Einträge geschrieben.  
  
3.  Binäre Objekte in einem Unity-Projekt, z. B. Texturen oder Audiodateien, können eine große Menge an Speicherplatz belegen. Verschiedene Quellcodeverwaltungssysteme wie Git speichern eine Kopie einer Datei für jede vorgenommene Änderung, auch wenn die Änderung nur einen kleinen Teil der Datei betrifft. Dadurch kann das Git-Repository sehr groß werden. Um dies zu vermeiden, entscheiden sich Unity-Entwickler häufig dafür, nur finale Objekte zu ihrem Repository hinzufügen und den Arbeitsverlauf der Objekte anderweitig zu speichern, etwa mit OneDrive, DropBox oder git-annex. Dieser Ansatz funktioniert, da solche Objekte in der Regel nicht zusammen mit Änderungen am Quellcode mit einer Versionsangabe versehen müssen. Entwickler legen in der Regel auch den Objektserialisierungsmodus des Projekteditors auf das Erzwingen von Text fest, um Szenendateien als Text und nicht im Binärformat zu speichern, wodurch Zusammenführungen in der Quellcodeverwaltung ermöglicht werden. Weitere Informationen finden Sie unter [Editoreinstellungen](http://docs.unity3d.com/Manual/class-EditorManager.html) (Unity-Dokumentation).  
  
## <a name="build"></a>Build  
 Referenzlink: **[Erstellen](../Topic/Build%20the%20application.md)**  
  
|Funktion|Unterstützt von Unity|Zusätzliche Kommentare|  
|-------------|--------------------------|-------------------------|  
|Lokaler TFS-Server|Möglich|Unity-Projekte werden über die Unity-Umgebung und nicht über das Visual Studio-Buildsystem erstellt (durch das Erstellen innerhalb der Visual Studio-Tools für Unity kompilieren Sie die Skripts, jedoch wird keine ausführbare Datei erzeugt). Es ist möglich, [Unity-Projekte von der Befehlszeile aus](http://docs.unity3d.com/Manual/CommandLineArguments.html) (Unity-Dokumentation), sodass es möglich, konfigurieren Sie einen MSBuild-Prozess auf einem TFS-Server zum Ausführen der entsprechenden Unity Befehle, sofern Unity selbst auf dem Computer installiert ist.<br /><br /> Darüber hinaus bietet Unity [Unity Cloud Build](https://build.cloud.unity3d.com/landing/), die ein Git- oder SVN-Repository überwacht und regelmäßige builds ausführt. Zurzeit funktioniert es nicht mit Team Foundation-Versionskontrolle oder Visual Studio Team Services.|  
|Lokaler Buildserver mit Verbindung zu Visual Studio Team Services|Möglich|Angesichts der dieselben Kriterien wie oben kann weiter Builds, ausgelöst durch Visual Studio Team Services auf einem lokalen TFS Computer weiterleiten.  Finden Sie unter [Buildserver](../Topic/Deploy%20and%20configure%20a%20build%20server.md) Anweisungen.|  
|Gehosteter Controllerdienst von Visual Studio Team Services|Nein|Unity-Builds werden derzeit nicht unterstützt.|  
|Builddefinitionen mit Vor- und Nachskripts|Ja|Eine benutzerdefinierte Builddefinition, die einen Build über die Unity-Befehlszeile ausführt, kann ebenfalls für Prä- und Postbuildskripts konfiguriert werden.|  
|Fortlaufende Integration einschließlich abgegrenzter Eincheckvorgänge|Ja|Abgegrenzte Eincheckvorgänge für TFVC, nur wenn Git auf einem Pull-Request-Modell statt mit Eincheckvorgängen arbeitet.|  
  
## <a name="testing"></a>Test  
 Referenzlink: **[Testen der Anwendung](/devops-test-docs/test/test-apps-early-and-often)**  
  
|Funktion|Unterstützt von Unity|Zusätzliche Kommentare|  
|-------------|--------------------------|-------------------------|  
|Planen von Tests, Erstellen von Testfällen und Organisieren von Testauflistungen|Ja||  
|Manuelle Tests|Ja||  
|Test-Manager (Aufzeichnung und Wiedergabe von Tests)|Nur Windows-Geräte und Android-Emulatoren||  
|Codeabdeckung|n/v|Nicht zutreffend, da Komponententests in Unity und nicht in Visual Studio erfolgen (siehe unten).|  
|[Komponententest für Code](../test/unit-test-your-code.md)|In Unity, nicht in Visual Studio|Unity bietet einen eigenen Komponententest-Framework als Teil des [Unity-TestTools](https://www.assetstore.unity3d.com/en/#!/content/13802) (Unity Asset Store). Unit-Testergebnisse werden in Unity gemeldet und nicht in Visual Studio angezeigt.|  
|[Verwenden von Benutzeroberflächenautomatisierung zum Testen Ihres Codes](../test/use-ui-automation-to-test-your-code.md)|Nein|Tests der codierten UI basieren auf lesbaren Steuerelementen in der App-Benutzeroberfläche. Unity-Apps sind grafischer Art, sodass Inhalte nicht von den Tools für Tests der codierten UI gelesen werden können.|  
  
## <a name="improve-code-quality"></a>Verbessern der Codequalität  
 Referenzlink: **[Verbessern der Codequalität](../test/improve-code-quality.md)**  
  
|Funktion|Unterstützt von Unity|Zusätzliche Kommentare|  
|-------------|--------------------------|-------------------------|  
|[Analysieren der Qualität von verwaltetem Code](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)|Ja|Den C#-Skript-Code in Visual Studio können analysiert werden.|  
|[Suchen von doppeltem Code mit der Codeklonerkennung](../Topic/Finding%20Duplicate%20Code%20by%20using%20Code%20Clone%20Detection.md)|Ja|Den C#-Skript-Code in Visual Studio können analysiert werden.|  
|[Messen von Komplexität und verwaltbarkeit von verwaltetem Code](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|Ja|Den C#-Skript-Code in Visual Studio können analysiert werden.|  
|[Leistungs-Explorer](../profiling/performance-explorer.md)|Nein|Verwenden der [Unity-Profiler](http://docs.unity3d.com/Manual/Profiler.html) (Unity-Website).|  
|[Analysieren von .NET Framework-Arbeitsspeicherproblemen](../misc/analyze-dotnet-framework-memory-issues.md)|Nein|Visual Studio-Tools haben keinen Zugriff auf das Mono-Framework (wie von Unity verwendet) für die Profilerstellung. Verwenden der [Unity-Profiler](http://docs.unity3d.com/Manual/Profiler.html) (Unity-Dokumentation).|  
  
## <a name="release-management"></a>Release Management:  
 Referenzlink: **[Automatisieren von Bereitstellungen mit Release Management](https://msdn.microsoft.com/library/vs/alm/release/overview)**  
  
|Funktion|Unterstützt von Unity|Zusätzliche Kommentare|  
|-------------|--------------------------|-------------------------|  
|Verwalten von Releaseprozessen|Ja||  
|Bereitstellen auf Servern für das Sideloading über Skripts|Ja||  
|Hochladen in den App Store|Partial|Erweiterungen sind verfügbar, die diesen Prozess für einige app-Stores automatisieren können.  Finden Sie unter [-Erweiterungen für Visual Studio Team Services](https://marketplace.visualstudio.com/VSTS)z. B. die [-Erweiterung für Google Play](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|  
  
## <a name="monitor-with-hockeyapp"></a>Monitor mit HockeyApp  
 Referenzlink: **[-Monitor mit HockeyApp](https://www.hockeyapp.net/features/)**  
  
|Funktion|Unterstützt von Unity|Zusätzliche Kommentare|  
|-------------|--------------------------|-------------------------|  
|Absturz Analyse, Telemetrie und Beta-Verteilung|Ja|HockeyApp ist in erster Linie für die Behandlung von Beta-Verteilung und das Abrufen von Absturzberichten.<br /><br /> Telemetriedaten aus C#-Skripts kann sich die Analytics-Framework verwenden, vorausgesetzt, dass sie auf die Version von .NET ausgeführt wird, die von Unity verwendet wird. Dies ermöglicht allerdings lediglich Analysen in Spieleskripts und nicht tiefer in der Unity-Engine. Derzeit ist es kein Plug-In für Application Insights-Plug-Ins sind jedoch verfügbar für andere Lösungen wie z. B. [Unity Analytics](https://www.assetstore.unity3d.com/en/#!/content/28120) und [Google Analytics](https://github.com/googleanalytics/google-analytics-plugin-for-unity). Dienste wie Unity Analytics, die die Art eines Unity-Projekts verstehen, liefern natürlich deutlich aussagekräftigere Analysen als generische Frameworks.|