---
title: "Application Lifecycle Management (ALM) mit Xamarin-apps | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "tgt-pltfrm-cross-plat"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ff978cc2-5a25-46d6-921b-e51adaa65992
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "crdun"
manager: "crdun"
---
# Application Lifecycle Management (ALM) mit Xamarin-apps
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Xamarin können Sie plattformübergreifende mobile apps für Android, iOS und Windows mit c#, .NET und Visual Studio erstellen. Mit Xamarin können einen großen Teil des Codes für alle Plattformen, sodass nur ein kleiner Prozentsatz plattformspezifisch sind freigegeben werden. Weitere Informationen zu Xamarin selbst finden Sie unter [Visual Studio und Xamarin](../cross-platform/visual-studio-and-xamarin.md).  
  
 Das Entwickeln von Apps für moderne Plattformen umfasst viele weitere Aktivitäten neben dem Schreiben von Code. Diese Aktivitäten, bezeichnet als DevOps (Development + Operations) umfassen vollständige Lebenszyklus der Anwendung und enthalten planen und Nachverfolgen der Arbeit, Entwerfen und Implementieren von Code, Verwalten von einem Quellcoderepository Ausführen von Builds, das Verwalten fortlaufender Integrationen und Bereitstellungen, testen (einschließlich Komponententests und Tests der Benutzeroberfläche), Durchführen verschiedener Formen der Diagnose in Entwicklungs-und produktionsumgebungen und Überwachung von app-Leistung und des Benutzerverhaltens in Echtzeit über Telemetrie und Analysen.  
  
 Visual Studio bietet zusammen mit Visual Studio Team Services und Team Foundation Server bieten eine Vielzahl von DevOps-Funktionen, die auch als Application Lifecycle Management oder ALM bezeichnet. Viele dieser Funktionen sind vollständig auf plattformübergreifende Projekte anwendbar.  
  
 Dies gilt insbesondere mit Xamarin-apps, da sie mit c# und .NET um wovon einige ALM-Tools erstellt werden, erstellt werden. Andere Tools erfordern die enge Integration in Build- und Laufzeitfehler. Da Xamarin-Apps nicht auf Windows-Plattformen ausgeführt werden und die Mono-Implementierung von .NET verwenden, bietet Xamarin spezielle Tools für bestimmte Anforderungen.  
  
 Die folgenden Tabellen identifiziert, welche Visual Studio-ALM-Funktionen zu erwarten, dass auch bei einem Xamarin-Projekt arbeiten und welche Einschränkungen aufweisen. Ausführliche Informationen über die Funktionen selbst finden Sie in der verknüpften Dokumentation.  
  
## <a name="agile-tools"></a>Agile-Tools  
 Referenzlink: **[Arbeit](../Topic/Track%20work%20using%20VSTS%20or%20TFS.md)** (mit Visual Studio Team Services oder TFS, einschließlich Team Explorer Everywhere)  
  
 Allgemeine Anmerkung: sämtliche planungs- und Nachverfolgungsfeatures sind unabhängig von Projekttyp und Programmiersprache.  
  
|Funktion|Unterstützt von Xamarin|Zusätzliche Kommentare|  
|-------------|----------------------------|-------------------------|  
|Verwalten von Rückständen und Sprints|Ja||  
|Arbeitsüberwachung|Ja||  
|Teamraumzusammenarbeit|Ja||  
|Kanban-Boards|Ja||  
|Berichte und Visualisierung des Fortschritts|Ja||  
  
## <a name="modeling"></a>Modellierung  
 Referenzlink: **[Analysieren und Modellieren der Architektur](../modeling/analyze-and-model-your-architecture.md)**  
  
 Die Entwicklungsfeatures sind unabhängig von der Programmiersprache oder funktionieren mit .NET-Sprachen wie C#. Finden Sie unter [Rollen der Architektur und von Modellierungsdiagrammen in der Softwareentwicklung](../modeling/scenario-change-your-design-using-visualization-and-modeling.md#ModelingDiagramsTools) Welche Aspekte sich auf Code beziehen.  
  
|Funktion|Unterstützt von Xamarin|Zusätzliche Kommentare|  
|-------------|----------------------------|-------------------------|  
|Sequenzdiagramme|Ja||  
|Abhängigkeitsdiagramme|Ja||  
|Aufrufhierarchie|Ja||  
|Klassen-Designer|Ja||  
|Architektur-Explorer|Ja||  
|UML-Diagramme (Anwendungsfall, Aktivität, Klasse, Komponente, Sequenz und DSL)|Ja||  
|Ebenendiagramme|Ja||  
|Gültigkeitsprüfung|Ja||  
  
## <a name="code"></a>Code  
  
|Funktion|Unterstützt von Xamarin|Zusätzliche Kommentare|  
|-------------|----------------------------|-------------------------|  
|[Verwenden von Team Foundation Version Control](../Topic/Use%20Team%20Foundation%20Version%20Control.md) oder Visual Studio Team Services|Ja||  
|[Erste Schritte mit Git in Team Services](../Topic/Use%20Visual%20Studio%20with%20Git.md)|Ja||  
|[Code Analysis/verbessern Codequalität (Verweise, vorgeschlagene Änderungen usw.).](../test/improve-code-quality.md)|Ja||  
|[Ändern von Code und andere Verläufe ermitteln](../ide/find-code-changes-and-other-history-with-codelens.md)|Ja|Außer über plattformspezifische Grenzen hinweg, in denen die Implementierung bis zur Laufzeit nicht aufgelöst wird.|  
|[Verwenden von Code Maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md)|Ja||  
  
## <a name="build"></a>Build  
 Referenzlink: **[Erstellen](../Topic/Build%20the%20application.md)**  
  
|Funktion|Unterstützt von Xamarin|Zusätzliche Kommentare|  
|-------------|----------------------------|-------------------------|  
|Lokaler TFS-Server|Ja|Auf Buildcomputern müssen Xamarin installiert und können mit einem OSX-Computer zur Erstellung für iOS verknüpft werden. Weitere Informationen finden Sie unter [Konfigurieren von TFS für Xamarin](http://developer.xamarin.com/guides/cross-platform/ci/configuring_tfs/) (Xamarin-Website)|  
|Lokaler Buildserver mit Verbindung zu Visual Studio Team Services|Ja|Finden Sie unter [Buildserver](../Topic/Deploy%20and%20configure%20a%20build%20server.md) Anweisungen.|  
|Gehosteter Controllerdienst von Visual Studio Team Services|Ja|Finden Sie unter [Erstellen Sie Ihre Anwendung Xamarin](https://www.visualstudio.com/en-us/docs/build/apps/mobile/xamarin).|  
|Builddefinitionen mit Vor- und Nachskripts|Ja||  
|Fortlaufende Integration einschließlich abgegrenzter Eincheckvorgänge|Ja|Abgegrenzte Eincheckvorgänge für TFVC, nur wenn Git auf einem Pull-Request-Modell statt mit Eincheckvorgängen arbeitet.|  
  
## <a name="testing"></a>Test  
 Referenzlink: **[Testen der Anwendung](/devops-test-docs/test/test-apps-early-and-often)**  
  
|Funktion|Unterstützt von Xamarin|Zusätzliche Kommentare|  
|-------------|----------------------------|-------------------------|  
|Planen von Tests, Erstellen von Testfällen und Organisieren von Testauflistungen|Ja||  
|Manuelle Tests|Ja||  
|Test-Manager (Aufzeichnung und Wiedergabe von Tests)|Ja|Windows-Geräte und Android-Emulatoren nur von Visual Studio. Aufzeichnung für alle Geräte kann mit [Xamarin Webleistungstest-Aufzeichnung](https://www.xamarin.com/test-cloud/recorder).|  
|Codeabdeckung|nicht verfügbar||  
|[Komponententest für Code](../test/unit-test-your-code.md)|Ja|Für Windows- und Android-Ziele können die integrierten MSTest-Tools verwendet werden. Zum Ausführen von Komponententests für Windows, Android und iOS empfiehlt Xamarin NUnit. Weitere Informationen finden Sie unter [Konfigurieren von TFS für Xamarin](http://developer.xamarin.com/guides/cross-platform/ci/configuring_tfs/) (Xamarin-Website).|  
|[Verwenden von Benutzeroberflächenautomatisierung zum Testen Ihres Codes](../test/use-ui-automation-to-test-your-code.md)|Nur Windows|Visual Studio UI Test Recorder ist nur in Windows. Für alle Plattformen finden Sie unter [Xamarin Webleistungstest-Aufzeichnung](https://www.xamarin.com/test-cloud/recorder).|  
  
## <a name="improve-code-quality"></a>Verbessern der Codequalität  
 Referenzlink: **[Verbessern der Codequalität](../test/improve-code-quality.md)**  
  
|Funktion|Unterstützt von Xamarin|Zusätzliche Kommentare|  
|-------------|----------------------------|-------------------------|  
|[Analysieren der Qualität von verwaltetem Code](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)|Ja||  
|[Suchen von doppeltem Code mit der Codeklonerkennung](../Topic/Finding%20Duplicate%20Code%20by%20using%20Code%20Clone%20Detection.md)|Ja||  
|[Messen von Komplexität und verwaltbarkeit von verwaltetem Code](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|Ja||  
|[Leistungs-Explorer](../profiling/performance-explorer.md)|Nein|Verwenden Sie stattdessen den [Xamarin Profiler](http://developer.xamarin.com/guides/cross-platform/deployment,_testing,_and_metrics/) über Xamarin Studio. Beachten Sie, dass der Xamarin Profiler sich derzeit in der Vorschauversion befindet und noch nicht für Windows-Ziele funktioniert.|  
|[Analysieren von .NET Framework-Arbeitsspeicherproblemen](../misc/analyze-dotnet-framework-memory-issues.md)|Nein|Visual Studio-Tools haben keinen Zugriff auf das Mono-Framework für die Profilerstellung.|  
  
## <a name="release-management"></a>Release Management:  
 Referenzlink: **[Automatisieren von Bereitstellungen mit Release Management](https://msdn.microsoft.com/library/vs/alm/release/overview)**  
  
|Funktion|Unterstützt von Xamarin|Zusätzliche Kommentare|  
|-------------|----------------------------|-------------------------|  
|Verwalten von Releaseprozessen|Ja||  
|Bereitstellen auf Servern für das Sideloading über Skripts|Ja||  
|Hochladen in den App Store|Partial|Erweiterungen sind verfügbar, die diesen Prozess für einige app-Stores automatisieren können.  Finden Sie unter [-Erweiterungen für Visual Studio Team Services](https://marketplace.visualstudio.com/VSTS)z. B. die [-Erweiterung für Google Play](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|  
  
## <a name="monitor-with-hockeyapp"></a>Monitor mit HockeyApp  
 Referenzlink: **[-Monitor mit HockeyApp](https://www.hockeyapp.net/features/)**  
  
|Funktion|Unterstützt von Xamarin|Zusätzliche Kommentare|  
|-------------|----------------------------|-------------------------|  
|Absturz Analyse, Telemetrie und Beta-Verteilung|Ja||