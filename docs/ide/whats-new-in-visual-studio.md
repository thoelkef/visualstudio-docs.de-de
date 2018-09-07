---
title: Neues in Visual Studio 2017
description: Informationen zu den neuen Features in Visual Studio 2017
ms.custom: ''
ms.date: 08/21/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
f1_keywords:
- VS.StartPage.WhatsNew
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 7307e180-ba28-4774-8a43-cbb980085a71
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3154264938753cf9be41cdd5ef8964f49664d730
ms.sourcegitcommit: bd6f04aff96201d514157de16ed6ddb8593d02b6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/23/2018
ms.locfileid: "42755508"
---
# <a name="what39s-new-in-visual-studio-2017"></a>Neues in Visual Studio 2017

**Für [Release 15.8](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default) aktualisiert**

Möchten Sie von einer vorherigen Version von Visual Studio aktualisieren? Visual Studio 2017 bietet Ihnen Folgendes: beispiellose Produktivität für alle Entwickler, Apps und Plattformen. Verwenden Sie Visual Studio 2017 zum Entwickeln von Apps für Android, iOS, Windows, Linux, das Web und die Cloud. Schnelles Codieren, einfaches Debuggen und einfache Diagnose, häufige Tests und zuverlässige Releases. Sie können Visual Studio auch durch Erstellen eigener Erweiterungen erweitern und anpassen. Verwenden Sie die Versionskontrolle, agile Prozesse, und steigern Sie die Effizienz bei der Zusammenarbeit mit diesem Release!

Dies ist eine allgemeine Zusammenfassung aller Änderungen, die seit der vorherigen Version, Visual Studio 2015, vorgenommen wurden:

* **[Neu definierte Grundlagen](#redefined-fundamentals)** Mit der neuen Setupfunktionalität können Sie generell schneller installieren und das, was Sie wünschen, dann installieren, wenn Sie es benötigen. Es spielt keine Rolle, ob Sie große Projektmappen und Projekte laden möchten, oder mit Codeordnern bzw. auch nur einer einzelnen Codedatei arbeiten, Visual Studio startet schneller. Außerdem behalten Sie mit Visual Studio stets den Überblick, was besonders wichtig ist für Teams, die sich auf DevOps konzentrieren.
* **[Leistung und Produktivität](#performance-and-productivity)** Wir haben uns auf neue, moderne Bereitstellungsfunktionen für Mobilgeräte sowie Cloud- und Desktopcomputer konzentriert. Wir haben außerdem die allgemeine Erfahrung beim Erwerb, für die Leistung und die allgemeine Entwicklerproduktivität verbessert. Visual Studio startet schneller, reagiert besser und benötigt weniger Arbeitsspeicher als je zuvor.
* **[Cloud-App-Entwicklung mit Azure](#cloud-app-development-with-azure)** Eine integrierte Sammlung von Azure-Tools, die Ihnen das einfache Entwickeln von primär auf die Cloud ausgelegten Apps in Microsoft Azure ermöglichen. Visual Studio vereinfacht das Konfigurieren, Erstellen, Debuggen, Packen und Bereitstellen von Apps und Diensten in Azure.
* **[Windows App-Entwicklung](#windows-app-development)** Verwenden Sie die UWP-Vorlagen in Visual Studio 2017, um ein einzelnes Projekt für alle Windows 10-Geräte zu erstellen: PC, Tablet, Smartphone, Xbox, HoloLens, Surface Hub usw. Erstellen Sie dann ein App-Paket, und übermitteln Sie dieses von Visual Studio aus an Microsoft Store, um Ihre App für Kunden bereitzustellen.
* **[Entwicklung mobiler Apps](#mobile-app-development)** Sie können in Visual Studio 2017 mit Xamarin schnell Neuerungen einführen und Ergebnisse erzielen, denn dies vereinheitlicht Ihre mobilen Multi-Plattform-Anforderungen durch Verwendung einer einzigen Kerncodebasis und eines einzigen Satzes von Fertigkeiten. Werden Sie mobil mit Ihren vorhandenen Teams, Technologieinvestitionen und C#-Code, sodass Sie marktgerechte Produkte vor Ablauf des Terminplans und mit Unterschreitung des Budgets bereitstellen können. Beschleunigen Sie jeden Schritt des mobilen Lebenszyklus, um erstklassige Benutzeroberflächen zu bieten oder ein Portfolio von Produktivitäts-Apps, mit denen Ihre Mitarbeiter effektiver arbeiten können. Außerdem **neu in 15.8**: Entwickler mobiler Apps, die Hyper-V nutzen, haben nun Zugriff auf einen schnellen Android-Emulator, der grundsätzlich die neuesten Android-APIs unterstützt, mit vorkonfigurierten Google Play Services funktioniert und alle Features des Android-Emulators unterstützt, einschließlich Kamera, Geolocation und Quick Boot.
* **[Plattformübergreifende Entwicklung](#cross-platform-development)** Übermitteln Sie Software problemlos an alle Zielplattform. Weiten Sie DevOps-Prozesse mithilfe von Redgate Data Tools auf SQL Server aus, und automatisieren Sie die sichere Datenbankbereitstellung aus Visual Studio. Verwenden Sie alternativ .NET Core, um Apps und Bibliotheken zu schreiben, die unverändert unter Windows, Linux und macOS ausgeführt werden. (**Neu in 15.3:** Parallele Unterstützung für .NET Core 2.0 SDKs)
* **[Spieleentwicklung](#games-development)** Mithilfe der Visual Studio-Tools für Unity (VSTU) können Sie Visual Studio zum Schreiben von Spiel- und Editorskripts in C# verwenden und dann den leistungsfähigen Debugger zum Suchen und Beheben von Fehlern nutzen. Das neueste Release von VSTU umfasst Syntaxfarben für die Shadersprache ShaderLab von Unity, bessere Debugger-Visualisierungen und verbesserte Codegenerierung für den MonoBehavior-Assistenten. Mit VSTU werden außerdem die Unity-Projektdateien, Konsolenmeldungen und die Möglichkeit zum Starten des Spiels in Visual Studio eingebunden, sodass beim Schreiben von Code weniger Zeit zum Umschalten in und aus dem Unity-Editor benötigt wird.
* **[KI-Entwicklung](#ai-development)** Mit Visual Studio-Tools für KI (**neu ab Version 15.5**) können Sie die Produktivitätsfeatures von Visual Studio verwenden, um KI-Innovationen zu beschleunigen. Sie können Deep Learning- bzw. KI-Lösungen erstellen, testen und bereitstellen, die eine nahtlose Integration in Azure Machine Learning für robuste Experimentierfunktionen bieten, z.B. das transparente Übermitteln von Datenvorbereitungen oder Modelltrainingsaufträgen an verschiedene Computeziele. Anbieter für Visual Studio Tools for AI bieten zusätzlich Unterstützung für benutzerdefinierte Metriken und das Nachverfolgen des Ausführungsverlaufs, wodurch die Reproduzierbarkeit und Überwachung von Data Science ermöglicht wird.

> [!NOTE]
> Eine vollständige Liste der neuen Features und Funktionen in Visual Studio 2017 finden Sie unter [Aktuelle Versionsanmerkungen](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default). Weitere Informationen zu zukünftig angebotenen Features finden Sie in den [Anmerkungen zur Vorschauversion](/visualstudio/releasenotes/vs2017-preview-relnotes?context=visualstudio/default).

Im Anschluss finden Sie ausführlichere Informationen zu einigen der wichtigsten Verbesserungen und neuen Funktionen in Visual Studio 2017.

## <a name="redefined-fundamentals"></a>Neu definierte Grundlagen

### <a name="a-new-setup-experience"></a>Ein neues Setuperlebnis

[Visual Studio 2017 herunterladen](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) oder [Visual Studio-Systemanforderungen überprüfen](/visualstudio/productinfo/vs2017-system-requirements-vs?context=visualstudio/default)

 In Visual Studio können Sie jetzt einfacher und schneller nur die Funktionen installieren, die Sie benötigen, wenn Sie sie benötigen. Und es lässt sich auch sauber wieder deinstallieren.

 Die wichtigste Änderung beim Installieren von Visual Studio ist die neue Setupoberfläche. Auf der Registerkarte **Arbeitsauslastungen** sehen Sie gruppierte Installationsoptionen, die allgemeine Frameworks, Sprachen und Plattformen darstellen. Von der .NET-Desktopentwicklung bis zur C++-Anwendungsentwicklung unter Windows, Linux und iOS ist alles abgedeckt.

Wählen Sie die benötigten Arbeitsauslastungen, und ändern Sie sie bei Bedarf.

 ![Visual Studio 2017-Setupdialogfeld](../install/media/install-visual-studio-enterprise.png)

Und Sie verfügen ferner über Optionen, um die Installation zu optimieren:

* Möchten Sie Ihre Komponenten lieber selbst aussuchen, statt Arbeitsauslastungen zu verwenden? Wählen Sie im Installationsprogramm die Registerkarte **Einzelne Komponenten** aus.
* Möchten Sie Sprachpakete installieren, ohne zugleich auch die eingestellte Sprache für Windows ändern zu müssen? Wählen Sie die Registerkarte **Sprachpakete** des Installationsprogramms aus.
* **Neues in 15.7**: Soll der Speicherort für die Installation von Visual Studio geändert werden? Wählen Sie die Registerkarte **Installationsoptionen** des Installationsprogramms aus.

Weitere Informationen zur neuen Installationsoberfläche sowie ausführliche Anweisungen, die Sie durch die Installation führen, finden Sie auf der Seite [Installieren von Visual Studio](../install/install-visual-studio.md).

### <a name="a-focus-on-accessibility"></a>Konzentration auf Barrierefreiheit

**In Version 15.3** wurden über 1.700 gezielte Fixes vorgenommen, um die Kompatibilität zwischen Visual Studio und den Hilfstechnologien zu verbessern, die viele Kunden verwenden. Es gibt Dutzende von Szenarien, die kompatibler mit Bildschirmsprachausgaben, Designs mit hohem Kontrast und anderen Hilfstechnologien sind als jemals zuvor. Debugger, Editor und Shell wurden ebenfalls allesamt erheblich verbessert.

Weitere Informationen finden Sie im Blogbeitrag [Accessibility improvements in Visual Studio 2017 version 15.3](https://blogs.msdn.microsoft.com/visualstudio/2017/08/14/accessibility-improvements-in-visual-studio-2017-version-15-3/) (Verbesserungen der Barrierefreiheit in Visual Studio 2017 [Version 15.3]).

## <a name="performance-and-productivity"></a>Leistung und Produktivität

### <a name="sign-in-across-multiple-accounts"></a>Anmelden mit mehreren Konten

Wir haben in Visual Studio einen neuen Identitätsdienst eingeführt, der Ihnen die übergreifende Verwendung von Benutzerkonten in Team Explorer, Azure-Tools, Microsoft Store-Veröffentlichungen usw. ermöglicht.

Sie auch länger angemeldet bleiben. Visual Studio wird Sie nicht alle 12 Stunden auffordern, sich anzumelden. Weitere Informationen finden Sie im Blogbeitrag [Fewer Visual Studio Sign-in Prompts (Weniger Anmeldeaufforderungen in Visual Studio)](https://blogs.msdn.microsoft.com/visualstudio/2016/08/15/fewer-visual-studio-sign-in-prompts/).

### <a name="start-visual-studio-faster"></a>Schnellerer Start von Visual Studio

Das neue Leistungscenter von Visual Studio kann Ihnen helfen, die IDE-Startzeit zu optimieren. Im Leistungscenter werden alle Erweiterungen und Toolfenster aufgelistet, die den Start der IDE verlangsamen könnten. Sie können es zum Verbessern der Startleistung verwenden, indem Sie festlegen, wann Erweiterungen gestartet werden oder ob bestimmte Toolfenster beim Start geöffnet sein sollen.

### <a name="faster-on-demand-loading-of-extensions"></a>Schnelleres Laden von Erweiterungen bei Bedarf

Visual Studio verschiebt seine Erweiterungen (und arbeitet auch mit Erweiterungen von Drittanbietern zusammen), damit sie erst bei Bedarf geladen werden, statt gleich beim IDE-Start. Möchten Sie wissen, welche Erweiterungen sich auf den Start, das Laden von Projektmappen und die Leistung bei der Eingabe auswirken? Sie finden diese Informationen unter **Hilfe** > **Visual Studio-Leistung verwalten**.

  ![Dialogfeld „Optionen“ in Visual Studio 2017](../ide/media/vs2017ide-manage-vs-perf.png)

#### <a name="manage-your-extensions-with-roaming-extensions-manager"></a>Verwalten von Erweiterungen mit dem Roaming-Erweiterungs-Manager

Es ist einfacher, jede Entwicklungsumgebung mit Ihren bevorzugten Erweiterungen einzurichten, wenn Sie sich bei Visual Studio anmelden. Der neue Roaming-Erweiterungs-Manager verfolgt alle Ihre bevorzugten Erweiterungen nach, indem er eine synchronisierte Liste in der Cloud erstellt.

Um eine Liste Ihrer Erweiterungen in Visual Studio anzuzeigen, klicken Sie auf **Extras** > **Erweiterungen und Updates**, und klicken Sie dann auf den **Roaming-Erweiterungs-Manager**.

![Visual Studio 2017: Dialogfeld „Erweiterungen und Updates“](../ide/media/vs2017ide-extensions-and-updates.png)

Der Roaming-Erweiterungs-Manager verfolgt alle von Ihnen installierten Erweiterungen nach, Sie können aber wählen, welche Ihrer Roamingliste hinzugefügt werden sollen.

![Visual Studio 2017: Dialogfeld „Erweiterungen und Updates“](../ide/media/vs2017ide-RoamingExtensionManager.png)

Wenn Sie den Roaming-Erweiterungs-Manager verwenden, werden Sie drei Symboltypen in Ihrer Liste bemerken:

* ![Symbol für „Roaming erfolgt“](../ide/media/vs2017ide-roamedicon.png) ***Roaming erfolgt:*** Eine Erweiterung, die in Ihrer Roamingliste enthalten, auf Ihrem Computer jedoch nicht installiert ist.
  (Erweiterungen dieses Typs können Sie mithilfe der Schaltfläche **Download** herunterladen.)
* ![Symbol für „Roaming und Installation erfolgt“](../ide/media/vs2017ide-roamedinstalledicon.png) ***Roaming und Installation erfolgt:*** Alle Erweiterungen, die Teil dieser Roamingliste und in Ihrer Entwicklungsumgebung installiert sind.
  (Wenn Sie sich gegen das Roaming entscheiden, können Sie zum Entfernen die Schaltfläche **Roaming beenden** verwenden.)
* ![Symbol für „Installiert“](../ide/media/vs2017ide-installedicon.png) ***Installiert:*** Alle Erweiterungen, die in dieser Umgebung installiert, aber nicht in der Roamingliste enthalten sind.
  (Sie können der Roamingliste Erweiterungen mithilfe der Schaltfläche **Roaming starten** hinzufügen.)

Jede Erweiterung, die Sie herunterladen, während Sie angemeldet sind, wird zu Ihrer Liste als **Roamed & Installed** (Roaming und Installation) hinzugefügt. Die Erweiterung wird dann zu Ihrer Roamingliste hinzugefügt, über die Sie auf diese über Ihren Computer zugreifen können.

### <a name="experience-live-unit-testing"></a>Entdecken Sie Live Unit Testing

In Visual Studio Enterprise 2017 liefern Ihnen Livekomponententests Livekomponententest-Ergebnisse und Codeabdeckung im Editor währende der Codierung. Dies funktioniert mit C#- und Visual Basic-Projekten für .NET Framework und .NET Core und unterstützt Testframeworks von MSTest, xUnit und NUnit.

![Live Unit Testing](../ide/media/lut-codewindow.png)

Weitere Informationen finden Sie unter [Introducing Live Unit Testing (Einführung in Live Unit Testing)](../test/live-unit-testing-intro.md). Eine Liste der neuen Funktionen, die in jedem Release von Visual Studio Enterprise 2017 hinzugefügt werden, finden Sie unter [What's new in Live Unit Testing (Neuerungen in Live Unit Testing)](../test/live-unit-testing-whats-new.md).

### <a name="set-up-a-cicd-pipeline"></a>Einrichten einer CI/CD-Pipeline

#### <a name="automated-testing"></a>Automatisiertes Testen

Automatisiertes Testen ist ein wesentlicher Bestandteil aller DevOps-Pipelines. Damit können Sie konsistent und zuverlässig testen und Ihre Projektmappe in viel kürzeren Abständen freigeben. CI/CD-Flüsse (Continuous Integration und Continuous Delivery) können Prozesse effektiver gestalten.

Weitere Informationen zu automatisierten Tests finden Sie im Blogbeitrag [CI/CD pipeline for automated tests in DevOps](https://blogs.msdn.microsoft.com/visualstudioalmrangers/2017/04/20/set-up-a-cicd-pipeline-to-run-automated-tests-efficiently/) (CI/CD-Pipeline für automatisierte Tests in DevOps).

Weitere Informationen zu Neuigkeiten in der DevLabs-Erweiterung [Continuous Delivery-Tools for Visual Studio (Continuous Delivery-Tools für Visual Studio)](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) finden Sie in dem Blogbeitrag [Committing with Confidence: Commit Time Code Quality (Commit mit Vertrauen: Commit ausführen mit Zeitcodequalität)](https://blogs.msdn.microsoft.com/visualstudio/2017/08/21/committing-with-confidence-commit-time-code-quality-information-updated/).

### <a name="visual-studio-ide-enhancements"></a>Verbesserungen der Visual Studio-IDE

#### <a name="multi-caret-editing"></a>Bearbeiten mit mehreren Caretzeichen

**Neu in 15.8:** Das gleichzeitige Bearbeiten von mehreren Stellen in einer Datei ist jetzt ganz einfach. Erstellen Sie zunächst an mehreren Stellen in einer Datei Einfügemarken und Auswahlpunkte. Nehmen Sie dann mithilfe des Features zum Bearbeiten mit mehreren Caretzeichen dieselbe Änderung an zwei oder mehr Stellen gleichzeitig vor.

Weitere Informationen finden Sie im Abschnitt [Multi-caret selection](finding-and-replacing-text.md#multi-caret-selection) (Auswählen mehrerer Caretzeichen) auf der Seite [Suchen und Ersetzen von Text](finding-and-replacing-text.md).

#### <a name="keep-keybinding-profiles-consistent"></a>Konsistente Tastenzuordnungsprofile

**Neu in 15.8:** Achten Sie darauf, dass Ihre Tastenzuordnungen mit den zwei neuen Tastaturprofilen konsistent bleiben: Visual Studio Code und ReSharper (Visual Studio). Diese Schemas finden Sie unter **Extras** > **Optionen** > **Allgemein** > **Tastatur** und über das oberste Dropdownmenü.

  ![Neue Tastenzuordnungsprofile für Visual Studio Code und ReSharper](../ide/media/vs-keyboard-mappings-code-resharper.png)

#### <a name="use-new-refactorings"></a>Verwenden neuer Refactorings

Als Refactoring wird der Prozess bezeichnet, Ihren Code zu verbessern, nachdem dieser geschrieben wurde. Durch Refactoring wird die interne Struktur des Codes geändert, ohne dessen Verhalten zu ändern. Neue Refactorings werden häufig hinzugefügt. Im Folgenden sind einige davon aufgeführt:

* Hinzufügen von Parametern (aus CallSite)
* Generieren von Überschreibungen
* Hinzufügen benannter Argumente
* NULL-Überprüfung für Parameter hinzufügen
* Einfügen von Zifferntrennzeichen in Literale
* Ändern der Basis für numerische Literale (z.B. von hexadezimal zu binär)
* Konvertieren von if-to-switch
* Nicht verwendete Variablen entfernen

Weitere Informationen finden Sie unter [Schnelle Aktionen](../ide/common-quick-actions.md).

#### <a name="interact-with-git"></a>Interaktion mit Git

Wenn Sie in Visual Studio an einem Projekt arbeiten, können Sie Ihren Code für einen Git-Dienst einrichten, ihn schnell dahin übertragen und dort veröffentlichen. Sie können Ihre Git-Repositorys auch mit Menüklicks auf Schaltflächen in der unteren rechten Ecke der IDE verwalten.

![Interaktion von Visual Studio 2017 mit dem Git-Dialogfeld](../ide/media/vsIDE-GitInteraction.png)

#### <a name="experience-improved-navigation-controls"></a>Benutzerfreundlichere Navigationssteuerelemente

Wir haben die Benutzerfreundlichkeit der Navigation verbessert, sodass Sie mit größerer Sicherheit und weniger Ablenkung von A nach B gelangen.

* **Neu in 15.4:** **Gehe zu Definition** (**Strg**+**Klicken** oder **F12**) &ndash; Mausbenutzer können einfacher zu der Definition eines Members navigieren, indem sie **Strg** drücken und dann auf das Member klicken. Durch das Drücken von **STRG** und das Zeigen auf ein Codesymbol mit der Maus wird dieses unterstrichen und in einen Link umgewandelt. Weitere Informationen finden Sie unter [Go To Definition and Peek Definition (Gehe zu Definition und Definition einsehen)](../ide/go-to-and-peek-definition.md).

* **Zur Implementierung wechseln** (**Strg**+**F12**) &ndash; Navigieren Sie von jedem Basistyp oder Member zu dessen verschiedenen Implementierungen.

* **Go To All** (**Strg**+**T** oder **Strg**+**,**) &ndash; ( Gehe zu allen) Navigieren Sie direkt zu jeder beliebigen Datei-/Typ-/Member-/Symboldeklaration. Sie können die Ergebnisliste filtern oder die Abfragesyntax verwenden (z.B. „f Suchbegriff“ für Dateien, „t Suchbegriff“ für Typen usw.).

  ![Verbesserte Option „Gehe zu allen“](../ide/media/vs2017ide-navigation-go-to.png)

* **Alle Verweise suchen** (**Umschalt**+**F12**) &ndash; Mit Syntaxfarbgebung können Sie „Alle Verweise suchen“-Ergebnisse nach einer Kombination aus Projekt, Definition und Pfad gruppieren. Sie können auch Ergebnisse „sperren“, damit Sie die Suche nach anderen Verweisen fortsetzen können, ohne die ursprünglichen Ergebnisse zu verlieren.

  ![Neues Tool „Alle Verweise suchen“](../ide/media/vs2017ide-find-all-references.png)

* **Strukturschnellansicht** &ndash; Punktierte, graue, vertikale Linien (Einzugsführungslinien) dienen nun als Orientierungshilfen im Code, um Kontext innerhalb Ihres Bezugssystems bereitzustellen. Vielleicht kennen Sie sie von den beliebten Produktivitäts-Power Tools. Damit können Sie jederzeit ohne zu scrollen visuell darstellen und ermitteln, in welchem Codeblock Sie sich befinden. Wenn Sie den Mauszeiger über die Zeilen bewegen, werden QuickInfos angezeigt, die Ihnen die Öffnung dieses Blocks und seine übergeordneten Elemente anzeigen. Dies ist sowohl für alle Sprachen verfügbar, die über TextMate-Grammatiken unterstützt werden, als auch für C#, Visual Basic und XAML.

  ![Strukturschnellansicht in Visual Studio 2017](../ide/media/vsIDE-StructureVisualizer.png)

Weitere Informationen zu den neuen Produktivitätsfeatures finden Sie im Blogbeitrag [Productivity in Visual Studio 2017 (Produktivität in Visual Studio 2017)](https://blogs.msdn.microsoft.com/visualstudio/2016/11/28/productivity-in-visual-studio-2017-rc/) von Mark Wilson-Thomas.

### <a name="visual-c"></a>Visual C++

Sie werden eine Reihe von Verbesserungen in Visual Studio bemerken, z.B. die Verteilung von C++ Core Guidelines mit Visual Studio, das Update des Compilers durch verbesserte Unterstützung für C++11- und C++-Funktionen und Hinzufügen und Aktualisieren von Funktionalität in den C++-Bibliotheken. Wir haben auch die Leistung der C++-IDE, die Installation von Arbeitsauslastungen und anderes mehr verbessert.

Wir haben ebenfalls mehr als 250 Fehler und gemeldete Probleme mit dem Compiler und den Tools behoben, von denen viele durch Kunden über die [Community für C++-Entwickler](https://developercommunity.visualstudio.com/spaces/62/index.html "Developer Community for C++") übermittelt wurden.

Ausführliche Angaben finden Sie auf der Seite [Neuerungen bei Visual C++ in Visual Studio 2017](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio).

### <a name="debugging-and-diagnostics"></a>Debuggen und Diagnose

#### <a name="run-to-click"></a>Ausführung bis Klick

Nun können Sie leichter während des Debuggens vorwärts springen, ohne einen Haltepunkt festlegen zu müssen, um in der gewünschten Zeile zu stoppen. Wenn Sie im Debugger angehalten werden, klicken Sie einfach auf das Symbol, das neben der Codezeile angezeigt wird. Die nächste Codeausführung wird nun an dieser Zeile anhalten, sobald sie im Codepfad erreicht wird.

![Debuggen in Visual Studio 2017: Ausführung bis Klick](../ide/media/vs2017ide-RunToClick.png)

#### <a name="the-new-exception-helper"></a>Die neue Ausnahmen-Hilfe

Die neue Ausnahmen-Hilfe hilft Ihnen, Ihre Ausnahmeinformationen auf einen Blick anzeigen. Die Informationen werden in einem kompakten Format mit unmittelbarem Zugriff auf die inneren Ausnahmen angezeigt. Wenn Sie eine NullReferenceException diagnostizieren, können Sie direkt in der Ausnahme-Hilfe schnell sehen, was NULL war.

![Dialogfeld der neuen Ausnahmen-Hilfe in Visual Studio](../ide/media/vs2017ide-ExceptionHelper.png)

Weitere Informationen finden Sie im Blogbeitrag [Using the New Exception Helper in Visual Studio (Verwenden der neuen Ausnahmen-Hilfe in Visual Studio)](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/).

#### <a name="snapshots-and-intellitrace-step-back"></a>Momentaufnahmen und das IntelliTrace-Feature „Step-back“

**Neues in Version 15.5:** Das IntelliTrace-Feature „Step-back“ nimmt automatisch bei jedem Breakpoint und Debuggerschritt eine Momentaufnahme Ihrer Anwendung auf. Durch die erfassten Momentaufnahmen können Sie zu vorherigen Haltepunkten oder Schritten zurückkehren und sich den Zustand der Anwendung so anzeigen lassen, wie er zuvor war. Mit dem IntelliTrace-Feature „Step-back“ können Sie Zeit sparen, wenn Sie den vorherigen Zustand der Anwendung anzeigen oder diesen wiederherstellen, aber das Debuggen nicht erneut starten möchten.

Sie können Momentaufnahmen anzeigen und durch diese navigieren, indem Sie die Schaltflächen **Schritt zurück** und **Schritt vorwärts** in der **Debug**-Symbolleiste verwenden. Mit diesen Schaltflächen können Sie durch die Ereignisse navigieren, die in der Registerkarte **Ereignisse** des Fensters **Diagnosetools** angezeigt werden. Wenn Sie mit „Schritt zurück“ oder „Schritt vor“ zu einem Ereignis navigieren, wird das verlaufsbezogene Debuggen für das ausgewählte Ereignis automatisch aktiviert.

![Das neue Dialogfeld „Ausnahmen-Hilfe“ in Visual Studio](../debugger/media/intellitrace-step-back-icons-description.png  "Schaltfläche „Schritt zurück“ und „Schritt vor“")

Weitere Informationen finden Sie auf der Seite [View snapshots using IntelliTrace step-back (Anzeigen von Momentaufnahmen mithilfe des IntelliTrace-Features „Step-back“)](../debugger/how-to-use-intellitrace-step-back.md).

### <a name="containerization"></a>Containerisierung

Container bieten eine höhere App-Dichte und niedrigere Bereitstellungskosten sowie eine verbesserte Produktivität und DevOps-Flexibilität.

#### <a name="docker-container-tooling"></a>Tools für Docker-Container

**Neues in Version 15.5**:

* Visual Studio enthält Tools für Docker-Container, die nun mehrstufige Dockerdateien unterstützen, die das Erstellen von optimierten Containerimages vereinfachen.
* Wenn Sie ein Projekt mit Docker-Unterstützung öffnen, werden von Visual Studio automatisch die erforderlichen Containerimages im Hintergrund abgerufen, erstellt und ausgeführt. Sie können dieses Verhalten über die Einstellung **Container im Hintergrund automatisch starten** in Visual Studio deaktivieren.

## <a name="cloud-app-development-with-azure"></a>Cloud-App-Entwicklung mit Azure

### <a name="azure-functions-tools"></a>Azure Functions-Tools

Als Teil der Workload „Azure-Entwicklung“ haben wir Tools eingefügt, mit denen Sie Azure-Funktionen entwickeln, indem Sie vorkompilierte C#-Klassenbibliotheken verwenden. Sie können jetzt auf dem lokalen Entwicklungscomputer erstellen, ausführen und debuggen und anschließend direkt aus Visual Studio in Azure veröffentlichen.

Weitere Informationen finden Sie auf der Seite [Azure Functions-Tools für Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-develop-vs).

### <a name="debug-live-aspnet-apps-using-snappoints-and-logpoints-in-live-azure-applications"></a>Debuggen von ASP.NET-Live-Apps mithilfe von Andockpunkten und Protokollpunkten in Azure-Live-Apps

**Neues in Version 15.5:** Der Momentaufnahmedebugger erstellt eine Momentaufnahme Ihrer Apps, die sich in der Produktion befinden, wenn Code ausgeführt wird, der für Sie von Interesse ist. Legen Sie Andockpunkte und Protokollpunkte in Ihrem Code fest, um den Debugger anzuweisen, eine Momentaufnahme zu erstellen. Der Debugger zeigt Fehler ohne Auswirkungen auf den Datenverkehr Ihrer Produktionsanwendung an. Der Momentaufnahmedebugger kann Sie dabei unterstützen, die Zeit zum Beheben von Fehlern, die in Produktionsumgebungen auftreten, erheblich zu reduzieren.

Die Momentaufnahmensammlung ist für folgende Web-Apps verfügbar, die in Azure App Service ausgeführt werden:

* ASP.NET-Apps, die in .NET Framework 4.6.1 oder höher ausgeführt werden.
* ASP.NET Core-Apps, die in .NET Core 2.0 oder höher unter Windows ausgeführt werden.

Weitere Informationen finden Sie unter [Debug live ASP.NET apps using snappoints and logpoints (Debuggen von ASP.NET-Live-Apps mithilfe von Andockpunkten und Protokollpunkten)](../debugger/debug-live-azure-applications.md).

## <a name="windows-app-development"></a>Windows App-Entwicklung

### <a name="universal-windows-platform"></a>Universelle Windows-Plattform

Universelle Windows-Plattform (UWP) ist die App-Plattform für Windows 10. Sie können Apps für UWP mit nur einem API-Satz, einem App-Paket und einem Store entwickeln, um alle Windows 10-Geräte (PC, Tablet, Smartphone, Xbox, HoloLens, Surface Hub usw.) zu erreichen. UWP unterstützt verschiedene Bildschirmgrößen und eine Vielzahl von Interaktionsmodellen, z.B. Fingereingabe, Maus und Tastatur, Gamecontroller oder Stifteingabe. Hinter UWP-Apps steht die Idee, dass Benutzer ihre Funktionen mobil auf ALLEN Geräten verwenden und jeweils das Gerät verwenden möchten, das am praktischsten und produktivsten für die vorliegende Aufgabe ist.

 ![Universelle Windows-Plattform](../cross-platform/media/uwp_coreextensions.png)

Wählen Sie aus C#, Visual Basic, C++ oder JavaScript Ihre bevorzugte Entwicklungssprache aus, um eine UWP-App für Windows 10-Geräte zu erstellen. Visual Studio 2017 stellt für jede Sprache eine Vorlage für UWP-Apps bereit, durch die Sie ein einzelnes Projekt für alle Geräte erstellen können. Wenn Ihre Arbeit abgeschlossen ist, können Sie ein App-Paket erstellen und dieses von Visual Studio aus an Microsoft Store übermitteln, um Ihre App für Kunden mit Windows 10-Geräten bereitzustellen.

**Neues in Version 15.5.:** Version 15.5 von Visual Studio 2017 bietet eine optimale Unterstützung für das Windows 10 Fall Creators Update SDK (10.0.16299.0). Das Windows 10 Fall Creators Update enthält viele Verbesserungen für UWP-Entwickler. Im Folgenden finden Sie einige der wichtigsten Änderungen: 

* **Unterstützung für .NET Standard 2.0**<br/>Zusätzlich zur optimierten App-Entwicklung ist das Windows 10 Fall Creators Update das erste Release von Windows 10, das Unterstützung für .NET Standard 2.0 bietet. [.NET Standard](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/) ist eine Referenzimplementierung der Basisklassenbibliothek, die jede .NET-Plattform implementieren kann. Das Ziel von .NET Standard besteht darin, das Freigeben von Code für .NET-Entwickler für jede .NET-Plattform, mit der sie arbeiten möchten, so einfach wie möglich zu gestalten.
* **Das Beste aus UWP und Win32**<br/>Die Windows 10-Plattform wurde durch die [Desktop-Brücke](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-root) verbessert, um Windows 10 für alle .NET-Entwickler unabhängig davon zu verbessern, ob der derzeitige Fokus auf UWP, WPF, Windows Forms oder Xamarin liegt. Mit dem neuen Projekttyp für das Packen von Apps in Version 15.5 von Visual Studio 2017 können Sie Windows-App-Pakete für Ihre Windows Presentation Foundation- oder Windows Forms-Projekte genau wie für UWP-Projekte erstellen. Nachdem Sie Ihre App gepackt haben, erhalten Sie alle Vorteile von Windows 10 für die App-Entwicklung und können diese über Microsoft Store (bei Verbraucher-Apps) oder Microsoft Store für Unternehmen und Bildungseinrichtungen verteilen. Da gepackte Apps über Zugriff auf die vollständige UWP-API-Oberfläche und auf die Win32-APIs auf dem Desktop verfügen, können Sie Ihre Windows Presentation Foundation- und Windows Forms-Apps nach und nach mit den UWP-APIs und den Windows 10-Features modernisieren. Darüber hinaus können Sie Ihre Win32-Komponenten mit allen Win32-Funktionen in Ihre UWP-Anwendungen integrieren, die auf dem Desktop gekennzeichnet sind.

Weitere Informationen zu UWP finden Sie auf der Seite [Entwickeln von Apps für die universelle Windows-Plattform (UWP)](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md).

## <a name="mobile-app-development"></a>Entwicklung mobiler Apps

### <a name="xamarin"></a>Xamarin

Als Teil der Workload „Mobile Entwicklung mit .NET“ können mit C#, .NET und Visual Studio vertraute Entwickler mithilfe von Xamarin native Apps für Android, iOS und Windows bereitstellen. Entwickler können bei der Arbeit mit Xamarin für mobile Apps die vertraute Leistungsstärke und Produktivität nutzen, einschließlich Remotedebuggen auf Android&mdash;, iOS- und Windows-Geräten – ohne native Programmiersprachen wie Objective-C oder Java erlernen zu müssen.

Weitere Informationen finden Sie unter [Visual Studio und Xamarin](../cross-platform/visual-studio-and-xamarin.md).

### <a name="entitlements-editor"></a>Berechtigungs-Editor

**Neues in Version 15.3:** Für Ihre iOS-Entwicklungsanforderungen haben wir einen eigenständigen Berechtigungs-Editor hinzugefügt. Er enthält eine benutzerfreundliche Benutzeroberfläche, die problemlos durchsucht werden kann. Doppelklicken Sie auf die Datei *entitlements.plist*, um ihn zu starten.

![Berechtigungs-Editor für Xamarin](../ide/media/xamarin-entitlements-editor.png)

### <a name="visual-studio-tools-for-xamarin"></a>Visual Studio-Tools für Xamarin

**Neues in 15.4:** Mit Xamarin Live können Entwickler ihre Apps direkt auf iOS-und Android-Geräten kontinuierlich bereitstellen, testen und debuggen. Nachdem Sie Xamarin Live Player heruntergeladen haben &mdash;(aus dem App Store oder von Google Play)&mdash;, können Sie Ihr Gerät mit Visual Studio verknüpfen. So verändern Sie den Prozess des Erstellens mobiler Apps von Grund auf. Diese Funktion ist jetzt in Visual Studio beinhaltet und kann unter **Tools** > **Optionen** > **Xamarin** > **Sonstiges** > **Xamarin Live Player aktivieren** aktiviert werden.

![Animation der Verknüpfung, Bereitstellung und der Livebearbeitungsmodi von Xamarin Live Player](../ide/media/xamarinliveplayer.gif)

### <a name="support-for-google-android-emulator"></a>Support für den Google Android-Emulator

**Neu in 15.8:** Wenn Sie Hyper-V verwenden, können Sie den Android-Emulator von Google nun parallel mit anderen Hyper-V-basierten Technologien verwenden, einschließlich Hyper-V-VMs, Docker-Tools und dem HoloLens-Emulator. (Diese Funktion erfordert Windows 10 April 2018 Update oder höher.)

![Der Google Android-Emulator mit Hyper-V-Technologien](../ide/media/xamarin-hyperv-android-emulator.png)

#### <a name="xamarinandroid-designer-split-view-editor"></a>Editor mit geteilter Ansicht für den Xamarin.Android-Designer

**Neu in 15.8:** Für Xamarin.Android wurden wichtige Verbesserungen am Designer durchgeführt. Ein Editor mit geteilter Ansicht wurde eingeführt, mit dem Sie Layouts gleichzeitig erstellen, bearbeiten und eine Vorschau dafür erstellen können.

![Der Editor mit geteilter Ansicht für den Xamarin.Android-Designer](../ide/media/android-designer-split-view.png)

Weitere Informationen finden Sie unter [Hardwarebeschleunigung für verbesserte Leistung des Emulators](/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin#hyper-v-overview).

### <a name="visual-studio-app-center"></a>Visual Studio App Center

**Neues in 15.5:** Visual Studio App Center ist nun allgemein für Android, iOS, macOS und Windows-Apps verfügbar und enthält alle erforderlichen Komponenten, um den Lebenszyklus Ihrer Apps zu verwalten, einschließlich automatisierter Builds, des Testens auf echten Geräten in der Cloud, der Verteilung an Betatester und App-Stores sowie des Überwachens der tatsächlichen Nutzung durch Absturz- und Analysedaten. Bei Apps, die in Objective-C, Swift, Java, C#, Xamarin oder React Native geschrieben wurden, werden sämtliche Features unterstützt.

  ![Testumgebung von Visual Studio App Center](../ide/media/app-center-test-env.png)

Weitere Informationen finden Sie im Blogbeitrag [Introducing App Center: Build, Test, Distribute and Monitor Apps in the Cloud (Einführung in App Center: Erstellen, Testen, Verteilen und Überwachen von Apps in der Cloud)](https://blogs.msdn.microsoft.com/vsappcenter/introducing-visual-studio-app-center/).

## <a name="cross-platform-development"></a>Plattformübergreifende Entwicklung

### <a name="redgate-data-tools"></a>Redgate Data Tools

Um DevOps-Funktionen für die Entwicklung der SQL Server-Datenbank zu erweitern, sind Redgate Data Tools jetzt in Visual Studio verfügbar.

In Visual Studio 2017 Enterprise sind enthalten:

* [Redgate ReadyRollCore ](http://www.red-gate.com/products/sql-development/readyroll/entrypage/microsoft-and-readyroll?utm_source=microsoft&utm_medium=link&utm_campaign=readyroll&utm_term=docs-newinvs) unterstützt Sie bei der Entwicklung von Migrationsskripts, dem Verwalten von Datenbankänderungen mithilfe von Quellcodeverwaltung und dem sicherem Automatisieren von Bereitstellungen der Änderungen an SQL Server-Datenbanken zusammen mit Anwendungsänderungen.
* [Redgate SQL Prompt Core](http://www.red-gate.com/products/sql-development/sql-prompt/entrypage/microsoft-and-sql-prompt?utm_source=microsoft&utm_medium=link&utm_campaign=sqlprompt&utm_term=docs-newinvs) unterstützt Sie beim schnelleren und genaueren Schreiben von SQL mithilfe intelligenter Codevervollständigung. Datenbank- und Systemobjekte sowie Schlüsselwörter werden während der Eingabe automatisch von SQL Prompt vervollständigt und es werden auch Spaltenvorschläge bereitgestellt. Dies führt zu optimiertem Code und weniger Fehlern, da Sie sich nicht jeden Spaltennamen oder Alias merken müssen.

In allen Editionen von Visual Studio 2017 ist enthalten:

* [Redgate SQL Search](http://www.red-gate.com/products/sql-development/sql-search/?utm_source=microsoft&utm_medium=link&utm_campaign=sqlsearch&utm_term=docs-newinvs) steigert Ihre Produktivität, weil Sie schnell nach SQL-Fragmenten und -Objekten in mehreren Datenbanken suchen können.

Weitere Informationen finden Sie im Blogbeitrag [Redgate Data Tools in Visual Studio 2017](https://blogs.msdn.microsoft.com/visualstudio/2017/03/07/redgate-data-tools-in-visual-studio-2017/).

### <a name="net-core"></a>.NET Core

.NET Core ist eine allgemeine, modulare, plattformübergreifende Open Source-Implementierung des .NET-Standards und enthält vieler der gleichen APIs wie das .NET Framework.

Die .NET Core-Plattform besteht aus mehreren Komponenten, die den verwalteten Compiler, die Runtime, die Basisklassenbibliotheken sowie zahlreiche Anwendungsmodelle wie ASP.NET Core umfassen. .NET Core unterstützt derzeit die drei Hauptbetriebssysteme: Windows, Linux und macOS. Sie können .NET Core in Geräte-, Cloud- und eingebetteten/IoT-Szenarien verwenden.

Außerdem enthält es nun Unterstützung für Docker.

**Neues in Version 15.3**: Visual Studio 2017 Version 15.3 unterstützt die .NET Core 2.0-Entwicklung. Wenn .NET Core 2.0 verwendet wird, muss das .NET Core 2.0 SDK separat heruntergeladen und installiert werden.

Weitere Informationen finden Sie im [Leitfaden für .NET Core](/dotnet/core/index).

## <a name="games-development"></a>Spieleentwicklung

### <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools für Unity

Als Teil der Workload „Entwicklung von Spielen für Unity“ haben wir die Tools eingefügt, mit denen Sie plattformübergreifend entwickeln können, um 2D- und 3D-Spiele und interaktiven Inhalt zu erstellen. Sie können ein einmal entwickeltes Spiel auf 21 Plattformen, einschließlich aller mobilen Plattformen, WebGL, Mac, PC- und Linux- Desktops, Web und Konsolen, mit Visual Studio 2017 und Unity 5.6 veröffentlichen.

Weitere Informationen finden Sie unter [Visual Studio Tools für Unity](../cross-platform/visual-studio-tools-for-unity.md).

## <a name="ai-development"></a>KI-Entwicklung

### <a name="visual-studio-tools-for-ai"></a>Visual Studio-Tools für KI

**Neues in Version 15.5:** Verwenden Sie die Produktivitätsfeatures von Visual Studio, um KI-Innovationen zu beschleunigen. Verwenden Sie die integrierten Features des Code-Editors wie die Syntaxhervorhebung, IntelliSense und die automatische Textformatierung. Sie können Ihre Deep Learning-Anwendung interaktiv in Ihrer lokalen Umgebung testen, indem Sie das Debuggen in ausführlichen Schritten für lokale Variablen und Modelle verwenden.

  ![Deep Learning-IDE](../ai/media/about/ide.png)

Weitere Informationen finden Sie unter [Visual Studio Tools für KI](../ai/about-ai-tools.md).

## <a name="whats-next"></a>Ausblick

Wir aktualisieren Visual Studio 2017 häufig mit neuen Features, die die Entwicklung immer weiter verbessern. Nachfolgend werden einige der wichtigsten Updates aufgeführt, die sich derzeit in der Phase der experimentellen Vorschau befinden:

* **[Live Share](https://visualstudio.microsoft.com/services/live-share/)**: ein neues Tool, über das Sie eine Codebasis und deren Kontext für ein anderes Teammitglied freigeben können und direkt in Visual Studio eine sofortige bidirektionale Kollaboration erhalten. Mithilfe von Live Share können Ihre Teammitglieder ohne Probleme und auf sichere Weise ein Projekt, das Sie für sie freigegeben haben, lesen, bearbeiten und debuggen sowie darin navigieren.<br><br>Weitere Informationen finden Sie unter [Live Share FAQ (Häufig gestellte Fragen zu Live Share)](/visualstudio/liveshare/faq).<br><br>
* **[IntelliCode](https://visualstudio.microsoft.com/services/intellicode/)**: eine neue Funktion zur Verbesserung der Softwareentwicklung unter Verwendung von KI. Dabei werden bessere kontextbezogene Codevervollständigungen zur Verfügung gestellt, Entwickler werden dabei unterstützt, gemäß den Mustern und Formatierungen ihres Teams zu codieren, versteckte Codeprobleme zu finden und Code Reviews auf die Bereiche zu beschränken, die wirklich wichtig sind. <br><br>Weitere Informationen finden Sie unter [IntelliCode FAQ (Häufig gestellte Fragen zu IntelliCode)](../ide/not-in-toc/intellicode-faq.md).

Sie möchten mehr über unsere Pläne für Visual Studio 2017 erfahren? Weitere Informationen finden Sie auf der Seite [Visual Studio-Roadmap](/visualstudio/productinfo/vs2018-roadmap).

## <a name="contact-us"></a>Kontakt

 Warum sollten Sie dem Visual Studio-Team ein Feedback senden? Weil wir das Feedback unserer Kunden ernst nehmen. Es gibt den Anstoß zu vielen unserer Initiativen.

Wenn Sie einen Vorschlag zu möglichen Verbesserungen von Visual Studio machen oder mehr über Optionen zur Produktunterstützung erfahren möchten, finden Sie weitere Informationen auf der Seite [Talk to Us (Sprechen Sie mit uns)](../ide/talk-to-us.md).

### <a name="report-a-problem"></a>Problem melden

 Manchmal reicht eine Nachricht nicht aus, um das gesamte Ausmaß eines Problems, auf das Sie gestoßen sind, deutlich zu machen. Wenn Ihr Programm nicht mehr reagiert und Abstürze oder andere Leistungsprobleme auftreten, können Sie die Schritte zur Reproduktion und unterstützende Dateien (wie etwa Screenshots, Ablaufverfolgungsdateien und Heap-Dumpdateien) auf einfache Weise mithilfe des Tools **Problem melden** mit uns teilen. Weitere Informationen zur Verwendung dieses Tools finden Sie auf der Seite [Melden eines Problems](how-to-report-a-problem-with-visual-studio-2017.md).

## <a name="see-also"></a>Siehe auch

* [Visual Studio 2017 – Anmerkungen zu dieser Version](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default)
* [Neues in Visual C++](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)
* [Neues in C#](/dotnet/csharp/whats-new)
* [Neues für Team Foundation Server](/tfs/server/whats-new?view=vsts)
* [Neues in Visual Studio für Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/)
