---
title: Application Lifecycle Management (ALM) mit Xamarin-Apps | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ff978cc2-5a25-46d6-921b-e51adaa65992
caps.latest.revision: 14
author: ghogen
ms.author: ghogen
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 6fbf89668d47d55d1d77a1d7f11765567fc73405
ms.openlocfilehash: e5ed1f9b6771b489218d2c6118454f1070535b6d
ms.contentlocale: de-de
ms.lasthandoff: 05/26/2017

---
# <a name="application-lifecycle-management-alm-with-xamarin-apps"></a>Application Lifecycle Management (ALM) mit Xamarin-Apps
Mit Xamarin können Sie plattformübergreifende mobile Apps für Android, iOS und Windows mit C#, .NET und Visual Studio erstellen. Xamarin ermöglicht die gemeinsame Verwendung eines großen Teils des Codes für alle Plattformen, sodass nur ein kleiner Prozentsatz plattformspezifisch angepasst werden muss. Weitere Informationen zu Xamarin selbst finden Sie unter [Visual Studio und Xamarin](../cross-platform/visual-studio-and-xamarin.md).  
  
 Das Entwickeln von Apps für moderne Plattformen umfasst viele weitere Aktivitäten neben dem Schreiben von Code. Diese als DevOps (Development + Operations) bezeichneten Aktivitäten decken den gesamten Lebenszyklus der App ab. Dazu gehören das Planen und Nachverfolgen der Arbeit, das Entwickeln und Implementieren von Code, das Verwalten eines Quellcoderepositorys, das Ausführen von Builds, das Verwalten von Continuous Integration und Deployment, das Testen (einschließlich Komponententests und Tests der Benutzeroberfläche), das Durchführen verschiedener Formen der Diagnose in Entwicklungs- und Produktionsumgebungen und das Überwachen der App-Leistung und des Benutzerverhaltens in Echtzeit über Telemetrie und Analysen.  
  
 Visual Studio bietet zusammen mit Visual Studio Team Services und Team Foundation Server eine Vielzahl von DevOps-Funktionen; diese werden auch als Application Lifecycle Management (ALM) bezeichnet. Viele dieser Funktionen sind vollständig auf plattformübergreifende Projekte anwendbar.  
  
 Dies gilt vor allem für Xamarin-Apps, da sie mit C# und .NET erstellt werden, auf die manche ALM-Tools abgestimmt sind. Andere Tools erfordern die feste Integration in Build- und Laufzeitumgebungen. Da Xamarin-Apps nicht auf Windows-Plattformen ausgeführt werden und die Mono-Implementierung von .NET verwenden, bietet Xamarin spezielle Tools für bestimmte Anforderungen.  
  
 In der folgenden Tabelle wird beschrieben, welche ALM-Funktionen von Visual Studio bei einem Xamarin-Projekt ordnungsgemäß bzw. eingeschränkt funktionieren. Ausführliche Informationen über die Funktionen selbst finden Sie in der verknüpften Dokumentation.  
  
## <a name="agile-tools"></a>Agile-Tools  
 Verweislink: **[Arbeit](http://msdn.microsoft.com/Library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)** (mit Visual Studio Team Services oder TFS, einschließlich Team Explorer Everywhere)  
  
 Allgemeiner Kommentar: alle Planungs- und Nachverfolgungsfunktionen sind vom Projekttyp und den Programmiersprachen unabhängig.  
  
|Funktion|Unterstützt von Xamarin|Zusätzliche Kommentare|  
|-------------|----------------------------|-------------------------|  
|Verwalten von Rückständen und Sprints|Ja||  
|Arbeitsüberwachung|Ja||  
|Teamraumzusammenarbeit|Ja||  
|Kanban-Boards|Ja||  
|Berichte und Visualisierung des Fortschritts|Ja||  
  
## <a name="modeling"></a>Modellierung  
 Verweislink: **[Analysieren und Modellieren der Architektur](../modeling/analyze-and-model-your-architecture.md)**  
  
 Die Entwicklungsfeatures sind unabhängig von der Programmiersprache oder funktionieren mit .NET-Sprachen wie C#. Mit Code zusammenhängende Aspekte finden Sie unter [Rollen von Architektur- und Modellierungsdiagrammen in der Softwareentwicklung](../modeling/scenario-change-your-design-using-visualization-and-modeling.md#ModelingDiagramsTools).  
  
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
|[Verwenden von Team Foundation-Versionskontrolle](http://msdn.microsoft.com/Library/1d629052-c65d-4c5d-81eb-eaa4413fe285) oder Visual Studio Team Services|Ja||  
|[Erste Schritte mit Git in Team Services](http://msdn.microsoft.com/Library/32f46ecd-1b03-4ef0-a9c4-8a120da2b03f)|Ja||  
|[Verbessern der Codequalität](/visualstudio/test/improve-code-quality)|Ja||  
|[Ermitteln von Änderungen am Code und andere Verläufe](../ide/find-code-changes-and-other-history-with-codelens.md)|Ja|Außer über plattformspezifische Grenzen hinweg, in denen die Implementierung bis zur Laufzeit nicht aufgelöst wird.|  
|[Verwenden von Code Maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md)|Ja||  
  
## <a name="build"></a>Build  
 Verweislink: **[Build](http://msdn.microsoft.com/Library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)**  
  
|Funktion|Unterstützt von Xamarin|Zusätzliche Kommentare|  
|-------------|----------------------------|-------------------------|  
|Lokaler TFS-Server|Ja|Auf Buildcomputern muss Xamarin installiert sein, und sie können mit einem OSX-Computer verknüpft werden, um Builds für iOS zu erstellen. Weitere Informationen finden Sie unter [Konfigurieren von TFS für Xamarin](http://developer.xamarin.com/guides/cross-platform/ci/configuring_tfs/) (Xamarin-Website)|  
|Lokaler Buildserver mit Verbindung zu Visual Studio Team Services|Ja|Anweisungen finden Sie unter [Buildserver](http://msdn.microsoft.com/Library/2d258a0a-f178-4e93-9da1-eba61151af3c).|  
|Gehosteter Controllerdienst von Visual Studio Team Services|Ja|Siehe [Erstellen Ihrer Xamarin-App](https://www.visualstudio.com/en-us/docs/build/apps/mobile/xamarin).|  
|Builddefinitionen mit Vor- und Nachskripts|Ja||  
|Fortlaufende Integration einschließlich abgegrenzter Eincheckvorgänge|Ja|Abgegrenzte Eincheckvorgänge für TFVC, nur wenn Git auf einem Pull-Request-Modell statt mit Eincheckvorgängen arbeitet.|  
  
## <a name="testing"></a>Test  
 Verweislink: **[Testen der Anwendung](/devops-test-docs/test/test-apps-early-and-often)**  
  
|Funktion|Unterstützt von Xamarin|Zusätzliche Kommentare|  
|-------------|----------------------------|-------------------------|  
|Planen von Tests, Erstellen von Testfällen und Organisieren von Testauflistungen|Ja||  
|Manuelle Tests|Ja||  
|Test-Manager (Aufzeichnung und Wiedergabe von Tests)|Ja|Nur Windows-Geräte und Android-Emulatoren von Visual Studio. Ein Aufzeichnen für alle Geräte ist mit [Xamarin Text Recorder](https://www.xamarin.com/test-cloud/recorder) möglich.|  
|Codeabdeckung|nicht verfügbar||  
|[Komponententest für Code](../test/unit-test-your-code.md)|Ja|Für Windows- und Android-Ziele können die integrierten MSTest-Tools verwendet werden. Zum Ausführen von Komponententests für Windows, Android und iOS empfiehlt Xamarin NUnit. Weitere Informationen finden Sie unter [Konfigurieren von TFS für Xamarin](http://developer.xamarin.com/guides/cross-platform/ci/configuring_tfs/) (Xamarin-Website).|  
|[Verwenden von Benutzeroberflächenautomatisierung zum Testen des Codes](../test/use-ui-automation-to-test-your-code.md)|Nur Windows|Testaufzeichnung der Benutzeroberfläche in Visual Studio ist nur unter Windows möglich. Alle Plattformen finden Sie unter [Xamarin Test Recorder](https://www.xamarin.com/test-cloud/recorder).|  
  
## <a name="improve-code-quality"></a>Verbessern der Codequalität  
 Verweislink: **[Verbessern der Codequalität](/visualstudio/test/improve-code-quality)**  
  
|Funktion|Unterstützt von Xamarin|Zusätzliche Kommentare|  
|-------------|----------------------------|-------------------------|  
|[Analysieren der Qualität von verwaltetem Code](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)|Ja||  
|[Suchen von doppeltem Code mit der Codeklonerkennung](http://msdn.microsoft.com/Library/a97cd5a6-5ffa-4104-9627-8e59e513654d)|Ja||  
|[Messen von Komplexität und Verwaltbarkeit verwalteten Codes](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|Ja||  
|[Leistungs-Explorer](../profiling/performance-explorer.md)|Nein|Verwenden Sie stattdessen den [Xamarin Profiler](http://developer.xamarin.com/guides/cross-platform/deployment,_testing,_and_metrics/) über Xamarin Studio. Beachten Sie, dass der Xamarin Profiler sich derzeit in der Vorschauversion befindet und noch nicht für Windows-Ziele funktioniert.|  
|[Analysieren von .NET Framework-Arbeitsspeicherproblemen](https://msdn.microsoft.com/en-us/library/dn342825.aspx)|Nein|Visual Studio-Tools haben keinen Zugriff auf das Mono-Framework für die Profilerstellung.|  
  
## <a name="release-management"></a>Release Management:  
 Verweislink: **[Automatisieren von Bereitstellungen mit Release Management](https://msdn.microsoft.com/library/vs/alm/release/overview)**  
  
|Funktion|Unterstützt von Xamarin|Zusätzliche Kommentare|  
|-------------|----------------------------|-------------------------|  
|Verwalten von Releaseprozessen|Ja||  
|Bereitstellen auf Servern für das Sideloading über Skripts|Ja||  
|Hochladen in den App Store|Partial|Es stehen Erweiterungen zur Verfügung, die diesen Prozess für manche App-Stores automatisieren können.  Siehe [Erweiterungen für Visual Studio Team Services](https://marketplace.visualstudio.com/VSTS); beispielsweise die [Extension for Google Play (Erweiterung für Google Play)](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|  
  
## <a name="monitor-with-hockeyapp"></a>Überwachen mit HockeyApp  
 Verweislink: **[Überwachen mit HockeyApp](https://www.hockeyapp.net/features/)**  
  
|Funktion|Unterstützt von Xamarin|Zusätzliche Kommentare|  
|-------------|----------------------------|-------------------------|  
|Absturzanalysen, Telemetrie und Betaverteilung|Ja||
