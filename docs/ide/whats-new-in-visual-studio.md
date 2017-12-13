---
title: "Neuerungen in Visual Studio 2017 | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/06/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
- vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.StartPage.WhatsNew
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 7307e180-ba28-4774-8a43-cbb980085a71
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 1e616fb0c223a30152b9cd18e6ea53e989690f9b
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2017
---
# <a name="what39s-new-in-visual-studio-2017"></a>Neuerungen in Visual Studio 2017
#### <a name="updated-for-the-154-release"></a>Für Release 15.4 aktualisiert
Möchten Sie von einer vorherigen Version von Visual Studio aktualisieren? Visual Studio 2017 bietet Ihnen Folgendes: beispiellose Produktivität für alle Entwickler, Apps und Plattformen. Verwenden Sie Visual Studio 2017 zum Entwickeln von Apps für Android, iOS, Windows, Linux, das Web und die Cloud. Schnelles Codieren, einfaches Debuggen und einfache Diagnose, häufige Tests und zuverlässige Releases. Sie können Visual Studio auch durch Erstellen eigener Erweiterungen erweitern und anpassen. Verwenden Sie die Versionskontrolle, agile Prozesse, und steigern Sie die Effizienz bei der Zusammenarbeit mit diesem Release!

Dies ist eine allgemeine Zusammenfassung aller Änderungen, die seit der vorherigen Version, Visual Studio 2015, vorgenommen wurden:

* **Neu definierte Grundlagen**. Mit der neuen Setupfunktionalität können Sie generell schneller installieren und das, was Sie wünschen, dann installieren, wenn Sie es benötigen. Es spielt es keine Rolle, ob Sie große Projektmappen und Projekte laden möchten, oder mit Codeordnern bzw. auch nur einer einzelnen Codedatei arbeiten, Visual Studio startet schneller. Außerdem behalten Sie mit Visual Studio stets den Überblick, was besonders wichtig ist für Teams, die sich auf DevOps konzentrieren.
* **Leistung und Produktivität**. Wir haben uns auf neue, moderne Bereitstellungsfunktionen für Mobilgeräte sowie Cloud- und Desktopcomputer konzentriert. Wir haben außerdem die allgemeine Erfahrung beim Erwerb, für die Leistung und die allgemeine Entwicklerproduktivität verbessert. Visual Studio startet schneller, reagiert besser und benötigt weniger Arbeitsspeicher als je zuvor.
* **Cloud-App-Entwicklung mit Azure**. Eine integrierte Sammlung von Azure-Tools, die Ihnen das einfache Entwickeln von primär auf die Cloud ausgelegten Apps in Microsoft Azure ermöglichen. Visual Studio vereinfacht das Konfigurieren, Erstellen, Debuggen, Packen und Bereitstellen von Apps und Diensten in Azure.
* **Entwicklung mobiler Apps**. Sie können in Visual Studio 2017 mit Xamarin schnell Neuerungen einführen und Ergebnisse erzielen, denn dies vereinheitlicht Ihre mobilen Multi-Plattform-Anforderungen durch Verwendung einer einzigen Kerncodebasis und eines einzigen Satzes von Fertigkeiten. Werden Sie mobil mit Ihren vorhandenen Teams, Technologieinvestitionen und C#-Code, sodass Sie marktgerechte Produkte vor Ablauf des Terminplans und mit Unterschreitung des Budgets bereitstellen können. Beschleunigen Sie jeden Schritt des mobilen Lebenszyklus, um erstklassige Benutzeroberflächen zu bieten oder ein Portfolio von Produktivitäts-Apps, mit denen Ihre Mitarbeiter effektiver arbeiten können.
* **Plattformübergreifende Entwicklung** Übermitteln Sie Software problemlos an alle Zielplattform. Weiten Sie DevOps-Prozesse mithilfe von Redgate Data Tools auf SQL Server aus, und automatisieren Sie die sichere Datenbankbereitstellung aus Visual Studio. Verwenden Sie alternativ .NET Core, um Apps und Bibliotheken zu schreiben, die unverändert unter Windows, Linux und macOS ausgeführt werden. (**Neu in 15.3:** Parallele Unterstützung für .NET Core 2.0 SDKs)
* **Spieleentwicklung** Mithilfe der Visual Studio-Tools für Unity (VSTU) können Sie Visual Studio zum Schreiben von Spiel- und Editorskripts in C# verwenden und dann den leistungsfähigen Debugger zum Suchen und Beheben von Fehlern nutzen. Die neueste Version von VSTU umfasst Syntaxfarben für die Shadersprache ShaderLab von Unity, bessere Debugger-Visualisierungen und verbesserte Codegenerierung für den MonoBehavior-Assistenten. Mit VSTU werden außerdem die Unity-Projektdateien, Konsolenmeldungen und die Möglichkeit zum Starten des Spiels in Visual Studio eingebunden, sodass beim Schreiben von Code weniger Zeit zum Umschalten in und aus dem Unity-Editor benötigt wird.

> [!NOTE]
> Eine vollständige Liste der neuen Features und Funktionen in Visual Studio 2017 finden Sie in den [Anmerkungen zur Version](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes).

Im Anschluss finden Sie ausführlichere Informationen zu einigen der wichtigsten Verbesserungen und neuen Funktionen in Visual Studio 2017.

## <a name="redefined-fundamentals"></a>Neu definierte Grundlagen
### <a name="a-new-setup-experience"></a>Ein neues Setuperlebnis

[Visual Studio 2017 herunterladen](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) oder [Visual Studio-Systemanforderungen überprüfen](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs)

 In Visual Studio können Sie jetzt einfacher und schneller nur die Funktionen installieren, die Sie benötigen, wenn Sie sie benötigen. Und es lässt sich auch sauber wieder deinstallieren.

 Die wichtigste Änderung beim Installieren von Visual Studio ist die neue Setupoberfläche. Auf der Registerkarte **Arbeitsauslastungen** sehen Sie gruppierte Installationsoptionen, die allgemeine Frameworks, Sprachen und Plattformen darstellen. Von der .NET-Desktopentwicklung bis zur C++-Anwendungsentwicklung unter Windows, Linux und iOS ist alles abgedeckt.

Wählen Sie die benötigten Arbeitsauslastungen, und ändern Sie sie bei Bedarf.

 ![Visual Studio 2017 Setupdialogfeld](../install/media/install-visual-studio-enterprise.png "Visual Studio 2017 Setupbildschirm")

Möchten Sie Ihre Komponenten lieber selbst aussuchen, statt Arbeitsauslastungen zu verwenden? Wählen Sie im Installationsprogramm die Registerkarte **Einzelne Komponenten** aus. Möchten Sie Sprachpakete installieren, ohne zugleich auch die eingestellte Sprache für Windows ändern zu müssen? Wählen Sie die Registerkarte **Sprachpakete** des Installationsprogramms aus.  

Weitere Informationen über die neue Installationsoberfläche, einschließlich Schritt-für-Schritt-Anweisungen, die Sie durch die Installation führen, finden Sie auf unserer Seite [Installieren von Visual Studio](../install/install-visual-studio.md).

### <a name="a-focus-on-accessibility"></a>Konzentration auf Barrierefreiheit
**In 15.3** haben wir über 1.700 gezielte Fixes vorgenommen, um die Kompatibilität zwischen Visual Studio und den Hilfstechnologien zu verbessern, die viele Kunden verwenden. Es gibt Dutzende von Szenarien, die kompatibler mit Bildschirmsprachausgaben, Designs mit hohem Kontrast und anderen Hilfstechnologien sind als jemals zuvor. Debugger, Editor und Shell haben ebenfalls allesamt erhebliche Verbesserungen erfahren.

Weitere Informationen finden Sie im Blogbeitrag [Accessibility improvements in Visual Studio 2017 version 15.3](https://blogs.msdn.microsoft.com/visualstudio/2017/08/14/accessibility-improvements-in-visual-studio-2017-version-15-3/) (Verbesserungen der Barrierefreiheit in Visual Studio 2017 [Version 15.3]).

## <a name="performance-and-productivity"></a>Leistung und Produktivität
### <a name="sign-in-across-multiple-accounts"></a>Anmelden mit mehreren Konten  
Wir haben in Visual Studio einen neuen Identitätsdienst eingeführt, der Ihnen die übergreifende Verwendung von Benutzerkonten in Team Explorer, Azure-Tools, Microsoft Store-Veröffentlichungen usw. ermöglicht.

Sie auch länger angemeldet bleiben. Visual Studio wird Sie nicht alle 12 Stunden auffordern, sich anzumelden. Weitere Informationen finden Sie im Blogbeitrag [Fewer Visual Studio Sign-in Prompts](https://blogs.msdn.microsoft.com/visualstudio/2016/08/15/fewer-visual-studio-sign-in-prompts/) (Weniger Anmeldeaufforderungen in Visual Studio).

### <a name="start-visual-studio-faster"></a>Schnellerer Start von Visual Studio
Das neue Leistungscenter von Visual Studio kann Ihnen helfen, die IDE-Startzeit zu optimieren. Im Leistungscenter werden alle Erweiterungen und Toolfenster aufgelistet, die den Start der IDE verlangsamen könnten. Sie können es zum Verbessern der Startleistung verwenden, indem Sie festlegen, wann Erweiterungen gestartet werden oder ob bestimmte Toolfenster beim Start geöffnet sein sollen.

### <a name="decrease-solution-load-time"></a>Verringern der Ladedauer von Projektmappen
Das Arbeiten mit Projektmappen, die eine große Anzahl von Projekten enthalten, bedeutet nicht, dass Sie an allen Dateien oder Projekten zugleich arbeiten müssen. Bearbeiten und Debuggen sind jetzt möglich, ohne auf das Laden jedes einzelnen Projekts durch Visual Studio zu warten. Wenn Sie dies mit verwalteten Projekten ausprobieren möchten, aktivieren Sie unter „Extras“ > „Optionen“ > „Projekte und Projektmappen“ den **Lightweight-Ladevorgang für Projektmappen**.

  ![Dialogfeld „Optionen“ in Visual Studio 2017](../ide/media/vs2017ide-lightweight-solution-load.png "Visual Studio 2017-Dialogfeld „Optionen“ – Lightweight-Ladevorgang für Projektmappen")

### <a name="faster-on-demand-loading-of-extensions"></a>Schnelleres Laden von Erweiterungen bei Bedarf
Visual Studio verschiebt seine Erweiterungen (und arbeitet auch mit Erweiterungen von Drittanbietern zusammen), damit sie erst bei Bedarf geladen werden, statt gleich beim IDE-Start. Möchten Sie wissen, welche Erweiterungen sich auf den Start, das Laden von Projektmappen und die Leistung bei der Eingabe auswirken? Sie finden diese Informationen unter „Hilfe“ > „Visual Studio-Leistung verwalten“.

  ![Dialogfeld „Optionen“ in Visual Studio 2017](../ide/media/vs2017ide-manage-vs-perf.png "Visual Studio-Dialogfeld „Hilfe“ – Leistungsverwaltung")

#### <a name="manage-your-extensions-with-roaming-extensions-manager"></a>Verwalten von Erweiterungen mit dem Roaming-Erweiterungs-Manager
Es ist einfacher, jede Entwicklungsumgebung mit Ihren bevorzugten Erweiterungen einzurichten, wenn Sie sich bei Visual Studio anmelden. Der neue Roaming-Erweiterungs-Manager verfolgt alle Ihre bevorzugten Erweiterungen nach, indem er eine synchronisierte Liste in der Cloud erstellt.  

Um eine Liste Ihrer Erweiterungen in Visual Studio anzuzeigen, klicken Sie auf „Extras“ > „Erweiterungen und Updates“, und klicken Sie dann auf den Roaming-Erweiterungs-Manager.

![Visual Studio 2017 – Dialogfeld „Erweiterungen und Updates“](../ide/media/vs2017ide-extensions-and-updates.png "Visual Studio 2017 – „Extras“ > Dialogfeld „Erweiterungen und Updates“")

Der Roaming-Erweiterungs-Manager verfolgt alle von Ihnen installierten Erweiterungen nach, Sie können aber wählen, welche Ihrer Roamingliste hinzugefügt werden sollen.

![Visual Studio 2017 – Dialogfeld „Erweiterungen und Updates“](../ide/media/vs2017ide-RoamingExtensionManager.png "Visual Studio 2017 – Roaming-Erweiterungs-Manager")

Wenn Sie den Roaming-Erweiterungs-Manager verwenden, werden Sie drei Symboltypen in Ihrer Liste bemerken:
* ![Symbol für „Roaming erfolgt“](../ide/media/vs2017ide-roamedicon.png "Symbol für „Roaming erfolgt“") ***Roaming erfolgt***: Eine Erweiterung, die in Ihrer Roamingliste enthalten, auf Ihrem Computer jedoch nicht installiert ist.
  (Erweiterungen dieses Typs können Sie mithilfe der Schaltfläche **Download** herunterladen.)
* ![Symbol für „Roaming und Installation erfolgt“](../ide/media/vs2017ide-roamedinstalledicon.png "Symbol für „Roaming und Installation erfolgt“") ***Roaming und Installation erfolgt***: Alle Erweiterungen, die Teil dieser Roamingliste und in Ihrer Entwicklungsumgebung installiert sind.
  (Wenn Sie sich gegen das Roaming entscheiden, können Sie zum Entfernen die Schaltfläche **Roaming beenden** verwenden.)
* ![Symbol für „Installiert“](../ide/media/vs2017ide-installedicon.png "Symbol für „Installiert“") ***Installiert***: Alle Erweiterungen, die in dieser Umgebung installiert, aber nicht in der Roamingliste enthalten sind.
  (Sie können der Roamingliste Erweiterungen mithilfe der Schaltfläche **Roaming starten** hinzufügen.)

Alle Erweiterungen, die Sie bei bestehender Anmeldung herunterladen, werden der Liste mit dem Status **Roaming und Installation erfolgt** hinzugefügt. Sie sind also Teil Ihrer Roamingliste, und daher haben Sie von jedem Computer aus darauf Zugriff.

### <a name="experience-live-architecture-dependency-validation-and-live-unit-testing"></a>Erleben Sie die Echtzeitüberprüfung der Architekturabhängigkeiten und Livekomponententests
Während Sie den Text in den Text-Editor eingeben, benachrichtigt Sie Visual Studio Sie in Echtzeit über Verletzungen von Architekturabhängigkeitsregeln, und zwar mithilfe von Abhängigkeitsvalidierungsdiagrammen (auch bekannt als Ebenendiagramme).

Fehler werden in der Fehlerliste angezeigt, und Wellenlinien im Text-Editor zeigen den genauen Ort der Regelverletzung an. Es ist nun unwahrscheinlicher, dass Sie unerwünschte Abhängigkeiten einführen.

![Echtzeitüberprüfung der Architektur](../ide/media/vs2017ide-LiveArchitectureDepedendencyValidation.png "Echtzeitüberprüfung der Architekturabhängigkeiten")

#### <a name="live-unit-testing"></a>Livekomponententests
In Visual Studio Enterprise 2017 liefern Ihnen Livekomponententests Livekomponententest-Ergebnisse und Codeabdeckung im Editor währende der Codierung. Dies funktioniert mit C#- und Visual Basic-Projekten für .NET Framework und .NET Core und unterstützt Testframeworks von MSTest, xUnit und NUnit.

![Livekomponententests](../ide/media/lut-codewindow.png "Ein Beispiel unseres neuen Livekomponententest-Features in der Enterprise Edition von Visual Studio")

Weitere Informationen finden Sie unter [Introducing Live Unit Testing (Einführung in Live Unit Testing)](../test/live-unit-testing-intro.md). Eine Liste der neuen Funktionen, die in jedem Release von Visual Studio Enterprise 2017 hinzugefügt werden, finden Sie unter [What's new in Live Unit Testing (Neuerungen in Live Unit Testing)](../test/live-unit-testing-whats-new.md).

#### <a name="set-up-a-cicd-pipeline-to-run-automated-tests-efficiently"></a>Einrichten einer CI/CD-Pipeline zum effizienten Ausführen automatisierter Tests
Automatisiertes Testen ist ein wesentlicher Bestandteil aller DevOps-Pipelines. Damit können Sie konsistent und zuverlässig testen und Ihre Projektmappe in viel kürzeren Abständen freigeben. CI/CD-Flüsse (Continuous Integration und Continuous Delivery) können Prozesse effektiver gestalten.

Weitere Informationen zu automatisierten Tests finden Sie im Blogbeitrag [CI/CD pipeline for automated tests in DevOps](https://blogs.msdn.microsoft.com/visualstudioalmrangers/2017/04/20/set-up-a-cicd-pipeline-to-run-automated-tests-efficiently/) (CI/CD-Pipeline für automatisierte Tests in DevOps).

Weitere Informationen zu Neuigkeiten in der DevLabs-Erweiterung [Continuous Delivery-Tools for Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) (Continuous Delivery-Tools für Visual Studio) finden Sie in dem Blogbeitrag [Committing with Confidence: Commit Time Code Quality](https://blogs.msdn.microsoft.com/visualstudio/2017/08/21/committing-with-confidence-commit-time-code-quality-information-updated/) (Commit mit Vertrauen: Commit ausführen mit Zeitcodequalität).

### <a name="visual-studio-ide-enhancements"></a>Verbesserungen der Visual Studio-IDE
#### <a name="use-new-refactorings"></a>Verwenden neuer Refactorings
**In Version 15.3** haben wir einige neue Refactorings hinzugefügt, einschließlich:
*   Mergingkonflikte lösen
*   Hinzufügen von Parametern (aus CallSite)
*   Generieren von Überschreibungen
*   Hinzufügen benannter Argumente
*   NULL-Überprüfung für Parameter hinzufügen
*   Einfügen von Zifferntrennzeichen in Literale
*   Ändern der Basis für numerische Literale (z.B. von hexadezimal zu binär)
*   Konvertieren von if-to-switch
*   Nicht verwendete Variablen entfernen

Weitere Informationen finden Sie auf der Seite [Umgestaltung, Codegenerierung und schnelle Aktionen in Visual Studio](refactoring-code-generation-quick-actions.md).  

#### <a name="interact-with-git"></a>Interaktion mit Git
Wenn Sie in Visual Studio an einem Projekt arbeiten, können Sie Ihren Code für einen Git-Dienst einrichten, ihn schnell dahin übertragen und dort veröffentlichen. Sie können Ihre Git-Repositorys auch mit Menüklicks auf Schaltflächen in der unteren rechten Ecke der IDE verwalten.

![Visual Studio 2017 interagiert mit dem Git-Dialogfeld](../ide/media/vsIDE-GitInteraction.png "Git-Tools in der Visual Studio-IDE")

#### <a name="experience-improved-navigation-controls"></a>Benutzerfreundlichere Navigationssteuerelemente
Wir haben die Benutzerfreundlichkeit der Navigation verbessert, sodass Sie mit größerer Sicherheit und weniger Ablenkung von A nach B gelangen.

* **Neu in 15.4:** **Gehe zu Definition (STRG+Klick oder F12)** &ndash;Mausbenutzer können einfacher zu der Definition eines Members navigieren, indem sie **STRG** drücken und dann auf das Member klicken. Durch das Drücken von **STRG** und das Zeigen auf ein Codesymbol mit der Maus wird dieses unterstrichen und in einen Link umgewandelt. Weitere Informationen finden Sie unter [Go To Definition and Peek Definition (Gehe zu Definition und Definition einsehen)](../ide/go-to-and-peek-definition.md).  

* **Zur Implementierung wechseln (STRG+F12)** &ndash; Navigieren Sie von jedem Basistyp oder Member zu dessen verschiedenen Implementierungen.

* **Go To All (STRG+T oder STRG+,)** (Gehe zu allen) &ndash; Navigieren Sie direkt zu jeder beliebigen Datei-/Typ-/Member-/Symboldeklaration. Sie können die Ergebnisliste filtern oder die Abfragesyntax verwenden (z.B. „f Suchbegriff“ für Dateien, „t Suchbegriff“ für Typen usw.).

 ![Verbessertes „Gehe zu allen“](../ide/media/vs2017ide-navigation-go-to.png "Beispiel für verbesserte „Gehe zu allen“-Funktion")

* **Alle Verweise suchen (UMSCHALT+F12)** &ndash; Mit Syntaxfarbgebung können Sie „Alle Verweise suchen“-Ergebnisse nach einer Kombination aus Projekt, Definition und Pfad gruppieren. Sie können auch Ergebnisse „sperren“, damit Sie die Suche nach anderen Verweisen fortsetzen können, ohne die ursprünglichen Ergebnisse zu verlieren.

 ![Neues „Alle Verweise suchen“-Tool](../ide/media/vs2017ide-find-all-references.png "Beispiel für neues „Alle Verweise suchen“-Tool")

* **Strukturschnellansicht** &ndash; Punktierte, graue, vertikale Linien (Einzugsführungslinien) dienen nun als Orientierungshilfen im Code, um Kontext innerhalb Ihres Bezugssystems bereitzustellen. Vielleicht kennen Sie sie von den beliebten Produktivitäts-Power Tools. Damit können Sie jederzeit ohne zu scrollen visuell darstellen und ermitteln, in welchem Codeblock Sie sich befinden. Wenn Sie den Mauszeiger über die Zeilen bewegen, werden QuickInfos angezeigt, die Ihnen die Öffnung dieses Blocks und seine übergeordneten Elemente anzeigen. Dies ist sowohl für alle Sprachen verfügbar, die über TextMate-Grammatiken unterstützt werden, als auch für C#, Visual Basic und XAML.  

![Visual Studio 2017 Strukturschnellansicht](../ide/media/vsIDE-StructureVisualizer.png "Strukturschnellansicht in Visual Studio")

Weitere Informationen zu unseren neuen Produktivitätsfeatures finden Sie im Blogbeitrag [Productivity in Visual Studio 2017](https://blogs.msdn.microsoft.com/visualstudio/2016/11/28/productivity-in-visual-studio-2017-rc/) (Produktivität in Visual Studio 2017) von Mark Wilson-Thomas.

### <a name="visual-c"></a>Visual C++
Sie werden eine Reihe von Verbesserungen in Visual Studio bemerken, z.B. die Verteilung von C++ Core Guidelines mit Visual Studio, das Update des Compilers durch verbesserte Unterstützung für C++11- und C++-Funktionen und Hinzufügen und Aktualisieren von Funktionalität in den C++-Bibliotheken. Wir haben auch die Leistung der C++-IDE, die Installation von Arbeitsauslastungen und anderes mehr verbessert.

Wir haben ebenfalls mehr als 250 Fehler und gemeldete Probleme mit dem Compiler und den Tools behoben, von denen viele durch Kunden über [Microsoft Connect](https://connect.microsoft.com/VisualStudio "Microsoft Connect") übermittelt wurden.

Eine vollständige Auflistung der Details finden Sie auf der Seite [Neues für Visual C++ in Visual 2017](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio).  

### <a name="debugging-and-diagnostics"></a>Debuggen und Diagnose
#### <a name="run-to-click"></a>Ausführung bis Klick:
Nun können Sie leichter während des Debuggens vorwärts springen, ohne einen Haltepunkt festlegen zu müssen, um in der gewünschten Zeile zu stoppen. Wenn Sie im Debugger angehalten werden, klicken Sie einfach auf das Symbol, das neben der Codezeile angezeigt wird. Die nächste Codeausführung wird nun an dieser Zeile anhalten, sobald sie im Codepfad erreicht wird.

![Visual Studio 2017-Debuggen – Ausführung bis Klick](../ide/media/vs2017ide-RunToClick.png "Ausführung bis Klick in Visual Studio-Debuggen und Diagnose")

#### <a name="the-new-exception-helper"></a>Die neue Ausnahmen-Hilfe:
Die neue Ausnahmen-Hilfe hilft Ihnen, Ihre Ausnahmeinformationen auf einen Blick anzeigen. Die Informationen werden in einem kompakten Format mit unmittelbarem Zugriff auf die inneren Ausnahmen angezeigt. Wenn Sie eine NullReferenceException diagnostizieren, können Sie direkt in der Ausnahme-Hilfe schnell sehen, was NULL war.

![Das neue Dialogfeld „Ausnahmehilfsprogramm“ in Visual Studio](../ide/media/vs2017ide-ExceptionHelper.png "Das neue Dialogfeld „Ausnahmehilfsprogramm“")

Weitere Informationen finden Sie im Blogbeitrag [Using the New Exception Helper in Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/) (Verwenden der neuen Ausnahmen-Hilfe in Visual Studio).

## <a name="cloud-app-development-with-azure"></a>Cloud-App-Entwicklung mit Azure
### <a name="azure-functions-tools"></a>Azure Functions-Tools
Als Teil der Workload „Azure-Entwicklung“ haben wir Tools eingefügt, mit denen Sie Azure-Funktionen entwickeln, indem Sie vorkompilierte C#-Klassenbibliotheken verwenden. Sie können jetzt auf dem lokalen Entwicklungscomputer erstellen, ausführen und debuggen und anschließend direkt aus Visual Studio in Azure veröffentlichen.

Weitere Informationen finden Sie unter [Azure Functions-Tools für Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-develop-vs) Seite.

## <a name="mobile-app-development"></a>Entwicklung mobiler Apps
### <a name="xamarin"></a>Xamarin
Als Teil der Workload „Mobile Entwicklung mit .NET“ können mit C#, .NET und Visual Studio vertraute Entwickler mithilfe von Xamarin native Apps für Android, iOS und Windows bereitstellen. Entwickler können bei der Arbeit mit Xamarin für mobile Apps die vertraute Leistungsstärke und Produktivität nutzen, einschließlich Remotedebuggen auf Android&mdash;, iOS- und Windows-Geräten – ohne native Programmiersprachen wie Objective-C oder Java erlernen zu müssen.

Weitere Informationen finden Sie unter [Visual Studio und Xamarin](../cross-platform/visual-studio-and-xamarin.md).

### <a name="entitlements-editor"></a>Berechtigungs-Editor
**Neues in Version 15.3:** Für Ihre iOS-Entwicklungsanforderungen haben wir einen eigenständigen Berechtigungs-Editor hinzugefügt. Er enthält eine benutzerfreundliche Benutzeroberfläche, die problemlos durchsucht werden kann. Doppelklicken Sie auf die Datei „entitlements.plist“, um ihn zu starten.

![Berechtigungs-Editor für Xamarin](../ide/media/xamarin-entitlements-editor.png "Entitlement editor for Xamarin")

## <a name="cross-platform-development"></a>Plattformübergreifende Entwicklung
### <a name="redgate-data-tools"></a>Redgate Data Tools
Um DevOps-Funktionen für die Entwicklung der SQL Server-Datenbank zu erweitern, sind Redgate Data Tools jetzt in Visual Studio verfügbar.

In Visual Studio 2017 Enterprise sind enthalten:
- [Redgate ReadyRollCore ](http://www.red-gate.com/products/sql-development/readyroll/entrypage/microsoft-and-readyroll?utm_source=microsoft&utm_medium=link&utm_campaign=readyroll&utm_term=docs-newinvs) unterstützt Sie bei der Entwicklung von Migrationsskripts, dem Verwalten von Datenbankänderungen mithilfe von Quellcodeverwaltung und dem sicherem Automatisieren von Bereitstellungen der Änderungen an SQL Server-Datenbanken zusammen mit Anwendungsänderungen.
- [Redgate SQL Prompt Core](http://www.red-gate.com/products/sql-development/sql-prompt/entrypage/microsoft-and-sql-prompt?utm_source=microsoft&utm_medium=link&utm_campaign=sqlprompt&utm_term=docs-newinvs) unterstützt Sie beim schnelleren und genaueren Schreiben von SQL mithilfe intelligenter Codevervollständigung. Datenbank- und Systemobjekte sowie Schlüsselwörter werden während der Eingabe automatisch von SQL Prompt vervollständigt und es werden auch Spaltenvorschläge bereitgestellt. Dies führt zu optimiertem Code und weniger Fehlern, da Sie sich nicht jeden Spaltennamen oder Alias merken müssen.

In allen Editionen von Visual Studio 2017 ist enthalten:
- [Redgate SQL Search](http://www.red-gate.com/products/sql-development/sql-search/?utm_source=microsoft&utm_medium=link&utm_campaign=sqlsearch&utm_term=docs-newinvs) steigert Ihre Produktivität, weil Sie schnell nach SQL-Fragmenten und -Objekten in mehreren Datenbanken suchen können.

Weitere Informationen finden Sie in unserem Blogbeitrag [Redgate Data Tools in Visual Studio 2017](https://blogs.msdn.microsoft.com/visualstudio/2017/03/07/redgate-data-tools-in-visual-studio-2017/).

### <a name="net-core"></a>.NET Core
.NET Core ist eine allgemeine, modulare, plattformübergreifende Open Source-Implementierung des .NET-Standards und enthält vieler der gleichen APIs wie das .NET Framework.

Die .NET Core-Plattform besteht aus mehreren Komponenten, die den verwalteten Compiler, die Runtime, die Basisklassenbibliotheken sowie zahlreiche Anwendungsmodelle wie ASP.NET Core umfassen. .NET Core unterstützt derzeit die drei Hauptbetriebssysteme: Windows, Linux und macOS. Sie können .NET Core in Geräte-, Cloud- und eingebetteten/IoT-Szenarien verwenden.

Außerdem enthält es nun Unterstützung für Docker.  

**Neues in Version 15.3**: Visual Studio 2017 Version 15.3 unterstützt die .NET Core 2.0-Entwicklung. Wenn .NET Core 2.0 verwendet wird, muss das .NET Core 2.0 SDK separat heruntergeladen und installiert werden.  

Weitere Informationen finden Sie im [Leitfaden für .NET Core](https://docs.microsoft.com/dotnet/core/index).

## <a name="games-development"></a>Spieleentwicklung
### <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools für Unity
Als Teil der Workload „Entwicklung von Spielen für Unity“ haben wir die Tools eingefügt, mit denen Sie plattformübergreifend entwickeln können, um 2D- und 3D-Spiele und interaktiven Inhalt zu erstellen. Sie können ein einmal entwickeltes Spiel auf 21 Plattformen, einschließlich aller mobilen Plattformen, WebGL, Mac, PC- und Linux- Desktops, Web und Konsolen, mit Visual Studio 2017 und Unity 5.6 veröffentlichen.

Weitere Informationen finden Sie unter [Visual Studio Tools für Unity](../cross-platform/visual-studio-tools-for-unity.md).

## <a name="talk-to-us"></a>Sprechen Sie mit uns  
 Warum sollten Sie dem Visual Studio-Team ein Feedback senden? Weil wir das Feedback unserer Kunden ernst nehmen. Es gibt den Anstoß zu vielen unserer Initiativen.  

Wenn Sie einen Vorschlag zu möglichen Verbesserungen von Visual Studio machen oder ein Problem melden möchten, finden Sie weitere Informationen auf der Seite [Talk to Us (Sagen Sie uns Ihre Meinung)](../ide/talk-to-us.md).  

### <a name="report-a-problem"></a>Problem melden  
 Manchmal reicht eine Nachricht nicht aus, um das gesamte Ausmaß eines Problems, auf das Sie gestoßen sind, deutlich zu machen. Wenn Ihr Programm nicht mehr reagiert und Abstürze oder andere Leistungsprobleme auftreten, können Sie die Schritte zur Reproduktion und unterstützende Dateien (wie etwa Screenshots, Ablaufverfolgungsdateien und Heap-Dumpdateien) auf einfache Weise mithilfe des Tools **Problem melden** mit uns teilen. Weitere Informationen zur Verwendung dieses Tools finden Sie auf der Seite [Melden eines Problems](how-to-report-a-problem-with-visual-studio-2017.md).  

### <a name="track-your-issue-in-connect"></a>Verfolgen Ihres Problems in Connect  
 Wenn Sie den Status Ihres Visual Studio-Feedbacks verfolgen möchten, rufen Sie [Verbinden](http://connect.microsoft.com/) auf, und melden Sie den Fehler dort. Nach der Meldung können Sie zu Connect zurückkehren, um den Status zu überprüfen.  

## <a name="see-also"></a>Siehe auch
* [Visual Studio 2017 – Anmerkungen zu dieser Version](https://www.visualstudio.com/news/vs2015-vs)
* [Neues in Visual C++](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)
* [Neues in C#](https://docs.microsoft.com/dotnet/csharp/csharp-7)  
* [Neues für Team Foundation Server](https://www.visualstudio.com/docs/whats-new)
* [Neues in Visual Studio für Mac](https://www.visualstudio.com/vs/visual-studio-mac/)
