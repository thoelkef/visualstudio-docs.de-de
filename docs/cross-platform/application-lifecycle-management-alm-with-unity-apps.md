---
title: Application Lifecycle Management (ALM) mit Unity-Apps | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dc61e63-9ba2-4c16-b1ad-f46249e576b6
caps.latest.revision: 12
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
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 7e95cec543216f13de06d2c2b86bc08040d1a7fb
ms.contentlocale: de-de
ms.lasthandoff: 05/13/2017

---
# <a name="application-lifecycle-management-alm-with-unity-apps"></a>Application Lifecycle Management (ALM) mit Unity-Apps
Das Entwickeln von Apps für moderne Plattformen umfasst viele weitere Aktivitäten neben dem Schreiben von Code. Diese als DevOps (Development + Operations) bezeichneten Aktivitäten decken den gesamten Lebenszyklus der App ab. Dazu gehören das Planen und Nachverfolgen der Arbeit, das Entwickeln und Implementieren von Code, das Verwalten eines Quellcoderepositorys, das Ausführen von Builds, das Verwalten von Continuous Integration und Deployment, das Testen (einschließlich Komponententests und Tests der Benutzeroberfläche), das Durchführen verschiedener Formen der Diagnose in Entwicklungs- und Produktionsumgebungen und das Überwachen der App-Leistung und des Benutzerverhaltens in Echtzeit über Telemetrie und Analysen.  
  
 Visual Studio bietet zusammen mit Visual Studio Team Services und Team Foundation Server eine Vielzahl von DevOps-Funktionen; diese werden auch als Application Lifecycle Management (ALM) bezeichnet. Viele dieser Funktionen lassen sich auf plattformübergreifende Projekte anwenden, einschließlich mit Unity erstellter Spiele und immersiver graphischer Apps, insbesondere bei Verwendung von C# als Skriptsprache. Da Unity über eine eigene Entwicklungsumgebung und ein eigenes Laufzeitmodul verfügt, können viele ALM-Funktionen allerdings nicht so wie bei anderen Arten von Projekten verwendet werden, die in Visual Studio erstellt wurden.  
  
 In den folgenden Tabellen sehen Sie, welche Visual Studio ALM-Funktionen bei der Arbeit mit Unity verwendet werden können. Ausführliche Informationen über die Funktionen selbst finden Sie in der verknüpften Dokumentation.  
  
## <a name="agile-tools"></a>Agile-Tools  
 Verweislink: **[Arbeit](http://msdn.microsoft.com/Library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)** (mit Visual Studio Team Services oder TFS, einschließlich Team Explorer Everywhere)  
  
 Allgemeiner Kommentar: alle Planungs- und Nachverfolgungsfunktionen sind vom Projekttyp und den Programmiersprachen unabhängig.  
  
|Funktion|Unterstützt von Unity|Zusätzliche Kommentare|  
|-------------|--------------------------|-------------------------|  
|Verwalten von Rückständen und Sprints|Ja||  
|Arbeitsüberwachung|Ja||  
|Teamraumzusammenarbeit|Ja||  
|Kanban-Boards|Ja||  
|Berichte und Visualisierung des Fortschritts|Ja||  
  
## <a name="modeling"></a>Modellierung  
 Verweislink: **[Analysieren und Modellieren der Architektur](../modeling/analyze-and-model-your-architecture.md)**  
  
 Allgemeiner Kommentar: Obwohl diese Funktionen entweder unabhängig von der Programmiersprache sind oder mit .NET-Sprachen wie C# funktionieren, beziehen sie sich auf ein traditionelles Anwendungsparadigma mit Objekthierarchien und Klassenbeziehungen. Für das Entwerfen eines Spiels in Unity ist ein anderes Paradigma erforderlich, nämlich die Beziehungen von grafischen Objekten, Sounds, Shadern, Skripts usw. Aus diesem Grund sind die Modellierungsdiagrammtools von Visual Studio für die Gesamtheit eines Unity-Projekts nicht von besonderer Bedeutung. Sie können möglicherweise zum Verwalten von Beziehungen innerhalb von C#-Skripts verwendet werden, aber das ist nur ein Teil des Ganzen.  
  
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
|[Verwenden von Team Foundation-Versionskontrolle](http://msdn.microsoft.com/Library/1d629052-c65d-4c5d-81eb-eaa4413fe285) oder Visual Studio Team Services|Ja|Unity-Projekte sind einfach eine Sammlung von Dateien, die wie jedes andere Projekt in Versionskontrollsysteme eingefügt werden können, jedoch gibt es einige spezielle Überlegungen, die nach dieser Tabelle aufgeführt sind.|  
|[Erste Schritte mit Git in Team Services](http://msdn.microsoft.com/Library/32f46ecd-1b03-4ef0-a9c4-8a120da2b03f)|Ja|Siehe Hinweise nach der Tabelle.|  
|[Codeanalyse/Verbessern der Codequalität (Verweise, vorgeschlagene Änderungen usw.)](http://msdn.microsoft.com/Library/73baa961-c21f-43fe-bb92-3f59ae9b5945)|Ja||  
|[Ermitteln von Änderungen am Code und andere Verläufe](../ide/find-code-changes-and-other-history-with-codelens.md)|Ja||  
|[Verwenden von Code Maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md)|Ja||  
  
 Besondere Überlegungen für die Versionskontrolle mit Unity:  
  
1.  Unity überwacht Metadaten über Spielressourcen in einer einzelnen, nicht transparenten Bibliothek, die standardmäßig ausgeblendet ist. Damit Dateien und Metadaten synchron bleiben, müssen die Metadaten sichtbar gemacht und in besser verwaltbaren Blöcken gespeichert werden. Weiter Informationen finden Sie unter [Using Version Control System with Unity (Verwenden von Versionskontrollsystemen mit Unity)](http://docs.unity3d.com/Manual/ExternalVersionControlSystemSupport.html) (Unity-Dokumentation).  
  
2.  Nicht alle Dateien und Ordner in einem Unity-Projekt eignen sich für die Quellcodeverwaltung, wie auch im obenstehenden Link beschrieben wird. Die Assets- und ProjectSettings-Ordner sollten hinzugefügt werden, nicht aber die Library- und Temp-Ordner. Eine zusätzliche Liste generierter Dateien, die nicht in die Quellcodeverwaltung aufgenommen werden würden, finden Sie unter [How to use Git for Unity3D source control? (So verwenden Sie Git für die Quellcodeverwaltung von Unity3D)](http://stackoverflow.com/questions/18225126/how-to-use-git-for-unity3d-source-control) auf StackOverflow. Viele Entwickler haben zu diesem Thema auch unabhängig Blog-Einträge geschrieben.  
  
3.  Binäre Objekte in einem Unity-Projekt, z. B. Texturen oder Audiodateien, können eine große Menge an Speicherplatz belegen. Verschiedene Quellcodeverwaltungssysteme wie Git speichern eine Kopie einer Datei für jede vorgenommene Änderung, auch wenn die Änderung nur einen kleinen Teil der Datei betrifft. Dadurch kann das Git-Repository sehr groß werden. Um dies zu vermeiden, entscheiden sich Unity-Entwickler häufig dafür, nur finale Objekte zu ihrem Repository hinzufügen und den Arbeitsverlauf der Objekte anderweitig zu speichern, etwa mit OneDrive, DropBox oder git-annex. Dieser Ansatz funktioniert, da solche Objekte in der Regel nicht zusammen mit Änderungen am Quellcode mit einer Versionsangabe versehen müssen. Entwickler legen in der Regel auch den Objektserialisierungsmodus des Projekteditors auf das Erzwingen von Text fest, um Szenendateien als Text und nicht im Binärformat zu speichern, wodurch Zusammenführungen in der Quellcodeverwaltung ermöglicht werden. Weitere Informationen finden Sie unter [Editoreinstellungen](http://docs.unity3d.com/Manual/class-EditorManager.html) (Unity-Dokumentation).  
  
## <a name="build"></a>Build  
 Verweislink: **[Build](http://msdn.microsoft.com/Library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)**  
  
|Funktion|Unterstützt von Unity|Zusätzliche Kommentare|  
|-------------|--------------------------|-------------------------|  
|Lokaler TFS-Server|Möglich|Unity-Projekte werden über die Unity-Umgebung und nicht über das Visual Studio-Buildsystem erstellt (durch das Erstellen innerhalb der Visual Studio-Tools für Unity kompilieren Sie die Skripts, jedoch wird keine ausführbare Datei erzeugt). Es ist möglich, Unity-Projekte über die Befehlszeile  zu [erstellen (Unity-Dokumentation)](http://docs.unity3d.com/Manual/CommandLineArguments.html). Damit ist es möglich, einen MSBuild-Prozess auf einem TFS-Server zum Ausführen der entsprechenden Unity-Befehle zu konfigurieren, sofern Unity selbst auf diesem Computer installiert ist.<br /><br /> Unity bietet darüber hinaus [Unity Cloud Build](https://build.cloud.unity3d.com/landing/), welches ein Git- oder SVN-Repository überwacht und regelmäßige Builds ausführt. Zurzeit funktioniert es weder mit der Team Foundation-Versionskontrolle noch mit Visual Studio Team Services.|  
|Lokaler Buildserver mit Verbindung zu Visual Studio Team Services|Möglich|Unter den obigen Bedingungen ist es zudem möglich, über Visual Studio Team Services ausgelöste Builds einen lokalen TFS-Computer verwenden zu lassen.  Anweisungen finden Sie unter [Buildserver](http://msdn.microsoft.com/Library/2d258a0a-f178-4e93-9da1-eba61151af3c).|  
|Gehosteter Controllerdienst von Visual Studio Team Services|Nein|Builds von Unity werden derzeit nicht unterstützt.|  
|Builddefinitionen mit Vor- und Nachskripts|Ja|Eine benutzerdefinierte Builddefinition, die einen Build über die Unity-Befehlszeile ausführt, kann ebenfalls für Prä- und Postbuildskripts konfiguriert werden.|  
|Fortlaufende Integration einschließlich abgegrenzter Eincheckvorgänge|Ja|Abgegrenzte Eincheckvorgänge für TFVC, nur wenn Git auf einem Pull-Request-Modell statt mit Eincheckvorgängen arbeitet.|  
  
## <a name="testing"></a>Test  
 Verweislink: **[Testen der Anwendung](/devops-test-docs/test/test-apps-early-and-often)**  
  
|Funktion|Unterstützt von Unity|Zusätzliche Kommentare|  
|-------------|--------------------------|-------------------------|  
|Planen von Tests, Erstellen von Testfällen und Organisieren von Testauflistungen|Ja||  
|Manuelle Tests|Ja||  
|Test-Manager (Aufzeichnung und Wiedergabe von Tests)|Nur Windows-Geräte und Android-Emulatoren||  
|Codeabdeckung|n/v|Nicht zutreffend, da Komponententests in Unity und nicht in Visual Studio erfolgen (siehe unten).|  
|[Komponententest für Code](../test/unit-test-your-code.md)|In Unity, nicht in Visual Studio|Unity bietet ein eigenes Komponententest-Framework als Teil der [Unity-Testtools](https://www.assetstore.unity3d.com/en/#!/content/13802) (Unity Asset Store). Unit-Testergebnisse werden in Unity gemeldet und nicht in Visual Studio angezeigt.|  
|[Verwenden von Benutzeroberflächenautomatisierung zum Testen des Codes](../test/use-ui-automation-to-test-your-code.md)|Nein|Tests der programmieren UI basieren auf lesbaren Steuerelementen in der App-Benutzeroberfläche. Unity-Apps sind grafischer Art, sodass Inhalte nicht von den Tools für Tests der programmierten UI gelesen werden können.|  
  
## <a name="improve-code-quality"></a>Verbessern der Codequalität  
 Verweislink: **[Verbessern der Codequalität](http://msdn.microsoft.com/Library/73baa961-c21f-43fe-bb92-3f59ae9b5945)**  
  
|Funktion|Unterstützt von Unity|Zusätzliche Kommentare|  
|-------------|--------------------------|-------------------------|  
|[Analysieren der Qualität von verwaltetem Code](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)|Ja|Kann den C#-Skriptcode in Visual Studio analysieren.|  
|[Suchen von doppeltem Code mit der Codeklonerkennung](http://msdn.microsoft.com/Library/a97cd5a6-5ffa-4104-9627-8e59e513654d)|Ja|Kann den C#-Skriptcode in Visual Studio analysieren.|  
|[Messen von Komplexität und Verwaltbarkeit verwalteten Codes](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|Ja|Kann den C#-Skriptcode in Visual Studio analysieren.|  
|[Leistungs-Explorer](../profiling/performance-explorer.md)|Nein|Verwenden des [Unity Profiler](http://docs.unity3d.com/Manual/Profiler.html) (Unity-Website).|  
|[Analysieren von .NET Framework-Arbeitsspeicherproblemen](https://msdn.microsoft.com/en-us/library/dn342825.aspx)|Nein|Visual Studio-Tools haben keinen Zugriff auf das Mono-Framework (wie von Unity verwendet) für die Profilerstellung. Verwenden des [Unity Profiler](http://docs.unity3d.com/Manual/Profiler.html) (Unity-Dokumentation).|  
  
## <a name="release-management"></a>Release Management:  
 Verweislink: **[Automatisieren von Bereitstellungen mit Release Management](https://msdn.microsoft.com/library/vs/alm/release/overview)**  
  
|Funktion|Unterstützt von Unity|Zusätzliche Kommentare|  
|-------------|--------------------------|-------------------------|  
|Verwalten von Releaseprozessen|Ja||  
|Bereitstellen auf Servern für das Sideloading über Skripts|Ja||  
|Hochladen in den App Store|Partial|Es stehen Erweiterungen zur Verfügung, die diesen Prozess für manche App-Stores automatisieren können.  Siehe [Erweiterungen für Visual Studio Team Services](https://marketplace.visualstudio.com/VSTS); beispielsweise die [Extension for Google Play (Erweiterung für Google Play)](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|  
  
## <a name="monitor-with-hockeyapp"></a>Überwachen mit HockeyApp  
 Verweislink: **[Überwachen mit HockeyApp](https://www.hockeyapp.net/features/)**  
  
|Funktion|Unterstützt von Unity|Zusätzliche Kommentare|  
|-------------|--------------------------|-------------------------|  
|Absturzanalysen, Telemetrie und Betaverteilung|Ja|HockeyApp wird hauptsächlich für das Verarbeiten und Abrufen Absturzberichte verwendet.<br /><br /> Für die Telemetrie von C#-Skripts kann ein Analytics-Framework verwendet werden, vorausgesetzt, dass es auf der von Unity verwendeten Version von .NET ausgeführt wird. Dies ermöglicht allerdings lediglich Analysen in Spieleskripts und nicht tiefer in der Unity-Engine. Im Moment gibt es kein Plug-In für Application Insights; es stehen jedoch Plug-Ins für andere Analyselösungen wie etwa [Unity Analytics](https://www.assetstore.unity3d.com/en/#!/content/28120) und [Google Analytics](https://github.com/googleanalytics/google-analytics-plugin-for-unity) zur Verfügung. Dienste wie Unity Analytics, die die Art eines Unity-Projekts verstehen, liefern natürlich deutlich aussagekräftigere Analysen als generische Frameworks.|
