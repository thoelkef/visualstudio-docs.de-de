---
title: Application Lifecycle Management (ALM) mit Xamarin-Apps | Microsoft-Dokumentation
ms.date: 08/21/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: ff978cc2-5a25-46d6-921b-e51adaa65992
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: 0cce9882add1443c2d9187d65b26a25081aac75b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "42634940"
---
# <a name="devops-with-xamarin-apps"></a>DevOps mit Xamarin-Apps

Mit Xamarin können Sie plattformübergreifende mobile Apps für Android, iOS und Windows mit C#, .NET und Visual Studio erstellen. Xamarin ermöglicht die gemeinsame Verwendung eines großen Teils des Codes für alle Plattformen, sodass nur ein kleiner Prozentsatz plattformspezifisch angepasst werden muss. Weitere Informationen zu Xamarin selbst finden Sie unter [Visual Studio und Xamarin](../cross-platform/visual-studio-and-xamarin.md).

Das Entwickeln von Apps für moderne Plattformen umfasst viele weitere Aktivitäten neben dem Schreiben von Code. Diese als DevOps (Development + Operations) bezeichneten Aktivitäten decken den gesamten Lebenszyklus der App ab. Dazu gehören das Planen und Nachverfolgen der Arbeit, das Entwickeln und Implementieren von Code, das Verwalten eines Quellcoderepositorys, das Ausführen von Builds, das Verwalten von Continuous Integration und Deployment, das Testen (einschließlich Komponententests und Tests der Benutzeroberfläche), das Durchführen verschiedener Formen der Diagnose in Entwicklungs- und Produktionsumgebungen und das Überwachen der App-Leistung und des Benutzerverhaltens in Echtzeit über Telemetrie und Analysen.

Visual Studio bietet zusammen mit Visual Studio Team Services und Team Foundation Server eine Vielzahl von DevOps-Funktionen. Viele dieser Funktionen sind vollständig auf plattformübergreifende Projekte anwendbar. Dies gilt vor allem für Xamarin-Apps, da sie mit C# und .NET erstellt werden, worauf einige DevOps-Tools basieren. Andere Tools erfordern die enge Integration in Build- und Laufzeitumgebungen. Da Xamarin-Apps nicht auf Windows-Plattformen ausgeführt werden und die Mono-Implementierung von .NET verwenden, bietet Xamarin spezielle Tools für bestimmte Anforderungen.

In den folgenden Tabellen wird beschrieben, welche DevOps-Features in Visual Studio ordnungsgemäß bzw. eingeschränkt funktionieren. Ausführliche Informationen über die Funktionen selbst finden Sie in der verknüpften Dokumentation.

## <a name="agile-tools"></a>Agile-Tools

Verweislink: **[Informationen zu Agile-Tools und Agile-Projektverwaltung](/vsts/work/backlogs/overview?view=vsts)**

Allgemeiner Kommentar: alle Planungs- und Nachverfolgungsfunktionen sind vom Projekttyp und den Programmiersprachen unabhängig.

|Feature|Unterstützt von Xamarin|Zusätzliche Kommentare|
|-------------|----------------------------|-------------------------|
|Verwalten von Rückständen und Sprints|Ja||
|Arbeitsüberwachung|Ja||
|Teamraumzusammenarbeit|Ja||
|Kanban-Boards|Ja||
|Berichte und Visualisierung des Fortschritts|Ja||

## <a name="modeling"></a>Modellierung

Verweislink: **[Analyse und Modellarchitektur](../modeling/analyze-and-model-your-architecture.md)**

Die Entwicklungsfeatures sind unabhängig von der Programmiersprache oder funktionieren mit .NET-Sprachen wie C#. Mit Code zusammenhängende Aspekte finden Sie unter [Rollen von Architektur- und Modellierungsdiagrammen in der Softwareentwicklung](../modeling/scenario-change-your-design-using-visualization-and-modeling.md#ModelingDiagramsTools).

|Feature|Unterstützt von Xamarin|Zusätzliche Kommentare|
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

|Feature|Unterstützt von Xamarin|Zusätzliche Kommentare|
|-------------|----------------------------|-------------------------|
|[Verwenden von Team Foundation-Versionskontrolle](/vsts/tfvc/overview?view=vsts) oder Visual Studio Team Services|Ja||
|[Erste Schritte mit Git in Team Services](/vsts/git/gitquickstart?view=vsts&tabs=visual-studio)|Ja||
|[Verbessern der Codequalität](../test/improve-code-quality.md)|Ja||
|[Ermitteln von Änderungen am Code und andere Verläufe](../ide/find-code-changes-and-other-history-with-codelens.md)|Ja|Außer über plattformspezifische Grenzen hinweg, in denen die Implementierung bis zur Laufzeit nicht aufgelöst wird.|
|[Verwenden von Code Maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md)|Ja||

## <a name="build"></a>Build

Verweislink: **[Build und Release](/vsts/pipelines/index?view=vsts)**

|Feature|Unterstützt von Xamarin|Zusätzliche Kommentare|
|-------------|----------------------------|-------------------------|
|Lokaler TFS-Server|Ja|Auf Buildcomputern muss Xamarin installiert sein, und sie können mit einem OSX-Computer verknüpft werden, um Builds für iOS zu erstellen. Siehe [Verwenden von TFVC](/vsts/tfvc/overview?view=vsts).|
|Lokaler Buildserver mit Verbindung zu Visual Studio Team Services|Ja|Anweisungen finden Sie unter [Build and release agents (Build- und Release-Agents)](/vsts/pipelines/agents/agents?view=vsts).|
|Gehosteter Controllerdienst von Visual Studio Team Services|Ja|Siehe [Erstellen Ihrer Xamarin-App](/vsts/pipelines/apps/mobile/xamarin?view=vsts&tabs=vsts).|
|Builddefinitionen mit Vor- und Nachskripts|Ja||
|Fortlaufende Integration einschließlich abgegrenzter Eincheckvorgänge|Ja|Abgegrenzte Eincheckvorgänge für TFVC, nur wenn Git auf einem Pull-Request-Modell statt mit Eincheckvorgängen arbeitet.|

## <a name="test"></a>Test

|Feature|Unterstützt von Xamarin|Zusätzliche Kommentare|
|-------------|----------------------------|-------------------------|
|Planen von Tests, Erstellen von Testfällen und Organisieren von Testauflistungen|Ja||
|Manuelle Tests|Ja||
|Test-Manager (Aufzeichnung und Wiedergabe von Tests)|Ja|Nur Windows-Geräte und Android-Emulatoren von Visual Studio. Ein Aufzeichnen für alle Geräte ist mit [Xamarin Text Recorder](/appcenter/test-cloud/uitest/) möglich.|
|Codeabdeckung|n/v||
|[Ausführen von Komponententests für Code](../test/unit-test-your-code.md)|Ja|Für Windows- und Android-Ziele können die integrierten MSTest-Tools verwendet werden. Zum Ausführen von Komponententests für Windows, Android und iOS empfiehlt Xamarin NUnit. Siehe [Verwenden von TFVC](/vsts/tfvc/overview?view=vsts).|
|[Verwenden der Benutzeroberflächenautomatisierung zum Testen des Codes](../test/use-ui-automation-to-test-your-code.md)|Nur Windows|Testaufzeichnung der Benutzeroberfläche in Visual Studio ist nur unter Windows möglich. Alle Plattformen finden Sie unter [Xamarin.UITest](/appcenter/test-cloud/uitest/).|

## <a name="improve-code-quality"></a>Verbessern der Codequalität

Verweislink: **[Verbessern der Codequalität](../test/improve-code-quality.md)**

|Feature|Unterstützt von Xamarin|Zusätzliche Kommentare|
|-------------|----------------------------|-------------------------|
|[Analysieren der Qualität von verwaltetem Code](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)|Ja||
|[Suchen von doppeltem Code mit der Codeklonerkennung](http://msdn.microsoft.com/Library/a97cd5a6-5ffa-4104-9627-8e59e513654d)|Ja||
|[Messen von Komplexität und Verwaltbarkeit verwalteten Codes](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|Ja||
|[Leistungs-Explorer](../profiling/performance-explorer.md)|Nein|Verwenden Sie stattdessen den [Xamarin Profiler](/xamarin/cross-platform/deploy-test/) über Xamarin Studio. Beachten Sie, dass der Xamarin Profiler sich derzeit in der Vorschauversion befindet und noch nicht für Windows-Ziele funktioniert.|
|[Analysieren von .NET Framework-Arbeitsspeicherproblemen](https://msdn.microsoft.com/en-us/library/dn342825.aspx)|Nein|Visual Studio-Tools haben keinen Zugriff auf das Mono-Framework für die Profilerstellung.|

## <a name="release-management"></a>Release Management:

Verweislink: **[Build und Release in VSTS und TFS](/vsts/pipelines/overview?view=vsts)**

|Feature|Unterstützt von Xamarin|Zusätzliche Kommentare|
|-------------|----------------------------|-------------------------|
|Verwalten von Releaseprozessen|Ja||
|Bereitstellen auf Servern für das Sideloading über Skripts|Ja||
|Hochladen in den App Store|Partial|Es stehen Erweiterungen zur Verfügung, die diesen Prozess für manche App-Stores automatisieren können.  Siehe [Erweiterungen für Visual Studio Team Services](https://marketplace.visualstudio.com/VSTS); beispielsweise die [Extension for Google Play (Erweiterung für Google Play)](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|

## <a name="monitor-with-hockeyapp"></a>Überwachen mit HockeyApp

Verweislink: **[Überwachen mit HockeyApp](https://www.hockeyapp.net/features/)**

|Feature|Unterstützt von Xamarin|Zusätzliche Kommentare|
|-------------|----------------------------|-------------------------|
|Absturzanalysen, Telemetrie und Betaverteilung|Ja||