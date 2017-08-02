---
title: "Neuerungen in Visual Studio 2017 | Microsoft-Dokumentation"
ms.custom: 
ms.date: 04/06/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.StartPage.WhatsNew
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 7307e180-ba28-4774-8a43-cbb980085a71
author: TerryGLee
ms.author: tglee
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
ms.sourcegitcommit: 8bf0b097be929b30627e0f1139c6e0b145933ab4
ms.openlocfilehash: 28c6a166a423b3341ae32676830861eaa78cb40d
ms.contentlocale: de-de
ms.lasthandoff: 05/26/2017

---
# <a name="what39s-new-in-visual-studio-2017"></a>Neuerungen in Visual Studio 2017
Beispiellose Produktivität für alle Entwickler, Apps und Plattformen. Verwenden Sie Visual Studio 2017 zum Entwickeln von Apps für Android, iOS, Windows, Linux, das Web und die Cloud. Schnelles Codieren, einfaches Debuggen und einfache Diagnose, häufige Tests und zuverlässige Releases. Sie können Visual Studio auch durch Erstellen eigener Erweiterungen erweitern und anpassen. Verwenden Sie Versionskontrolle und agile Softwareentwicklung, und arbeiten Sie mit diesem neuen Release effizient zusammen!

> [!NOTE]
> Eine vollständige Liste der neuen Features und Funktionen in Visual Studio 2017 finden Sie in den [Anmerkungen zur Version](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes).

Hier folgt eine allgemeine Zusammenfassung der vorgenommenen Änderungen:

* **Leistung und Produktivität**. Wir haben uns nicht nur auf neue und moderne mobile, Cloud- und Desktopentwicklungsfunktionen konzentriert, sondern auch die gesamte Erwerbs-, Leistungs- und allgemeine Entwicklerproduktivitätserfahrung verbessert. Visual Studio startet schneller, reagiert besser und benötigt weniger Arbeitsspeicher als je zuvor.
* **Neu definierte Grundlagen**. Mit der neuen Setupfunktionalität können Sie generell schneller installieren und das, was Sie wünschen, dann installieren, wenn Sie es benötigen. Visual Studio startet schneller, dabei spielt es keine Rolle, ob Sie große Projektmappen und Projekte laden möchten, oder mit Codeordnern bzw. auch nur einer einzelnen Codedatei arbeiten. Außerdem behalten Sie mit Visual Studio stets den Überblick, was besonders wichtig ist für Teams, die sich auf DevOps konzentrieren.
* **Cloud-App-Entwicklung mit Azure**. Eine integrierte Sammlung von Azure-Tools, die Ihnen das einfache Entwickeln von primär auf die Cloud ausgelegten Apps in Microsoft Azure ermöglichen. Visual Studio vereinfacht das Konfigurieren, Erstellen, Debuggen, Packen und Bereitstellen von Apps und Diensten in Azure.
* **Entwicklung mobiler Apps**. Sie können in Visual Studio 2017 mit Xamarin schnell Neuerungen einführen und Ergebnisse erzielen, denn dies vereinheitlicht Ihre mobilen Multi-Plattform-Anforderungen durch Verwendung einer einzigen Kerncodebasis und eines einzigen Satzes von Fertigkeiten. Werden Sie mobil mit Ihren vorhandenen Teams, Technologieinvestitionen und C#-Code, sodass Sie marktgerechte Produkte vor Ablauf des Terminplans und mit Unterschreitung des Budgets bereitstellen können. Beschleunigen Sie jeden Schritt des mobilen Lebenszyklus, um erstklassige Benutzeroberflächen zu bieten oder ein Portfolio von Produktivitäts-Apps, mit denen Ihre Mitarbeiter effektiver arbeiten können.

Hier finden Sie weitere Details zu einigen der wichtigsten Änderungen.

## <a name="performance-improvements"></a>Leistungsverbesserungen

### <a name="a-new-setup-experience"></a>Ein neues Setuperlebnis  
[Visual Studio 2017 herunterladen](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) oder [Visual Studio-Systemanforderungen überprüfen](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs)

 In Visual Studio können Sie jetzt einfacher und schneller nur die Funktionen installieren, die Sie benötigen, wenn Sie sie benötigen. Und es lässt sich auch sauber wieder deinstallieren.

 Die wichtigste Änderung, die Ihnen beim Installieren von Visual Studio auffallen wird, ist die neue Setupoberfläche. Auf der Registerkarte **Arbeitsauslastungen** sehen Sie gruppierte Installationsoptionen, die allgemeine Frameworks, Sprachen und Plattformen darstellen. Von der .NET-Desktopentwicklung bis zur C++-Anwendungsentwicklung unter Windows, Linux und iOS ist alles abgedeckt.   

 ![Visual Studio 2017 Setupdialogfeld](~/install/media/vs2017-workloads.PNG "Visual Studio 2017 Setupbildschirm")

Wählen Sie die benötigten Arbeitsauslastungen, und ändern Sie sie bei Bedarf.

Möchten Sie Ihre Komponenten lieber selbst aussuchen, statt Arbeitsauslastungen zu verwenden? Wählen Sie einfach im Installationsprogramm die Registerkarte **Einzelne Komponenten** aus. Möchten Sie Sprachpakete installieren, ohne zugleich auch die eingestellte Sprache für Windows ändern zu müssen? Wählen Sie die Registerkarte **Sprachpakete** des Installationsprogramms aus.  

Weitere Informationen über die neue Installationsoberfläche, einschließlich Schritt-für-Schritt-Anweisungen, die Sie durch die Installation führen, finden Sie auf unserer Seite [Installieren von Visual Studio](../install/install-visual-studio.md).

### <a name="start-visual-studio-faster"></a>Schnellerer Start von Visual Studio
Das neue Leistungscenter von Visual Studio kann Ihnen helfen, die IDE-Startzeit zu optimieren. Im Leistungscenter werden alle Erweiterungen und Toolfenster aufgelistet, die den Start der IDE verlangsamen könnten. Sie können es zum Verbessern der Startleistung verwenden, indem Sie festlegen, wann Erweiterungen gestartet werden oder ob bestimmte Toolfenster beim Start geöffnet sein sollen.

### <a name="decrease-solution-load-time"></a>Verringern der Ladedauer von Projektmappen
Das Arbeiten mit Projektmappen, die eine große Anzahl von Projekten enthalten, bedeutet nicht, dass Sie an allen Dateien oder Projekten zugleich arbeiten müssen. Bearbeiten und Debuggen sind jetzt möglich, ohne auf das Laden jedes einzelnen Projekts durch Visual Studio zu warten. Wenn Sie dies mit verwalteten Projekten ausprobieren möchten, aktivieren Sie unter „Extras“ > „Optionen“ > „Projekte und Projektmappen“ den **Lightweight-Ladevorgang für Projektmappen**.

  ![Dialogfeld „Optionen“ in Visual Studio 2017](~/ide/media/vs2017ide-LightweightSolutionLoad.PNG "Visual Studio 2017-Dialogfeld „Optionen“ – Lightweight-Ladevorgang für Projektmappen")

### <a name="faster-on-demand-loading-of-extensions"></a>Schnelleres Laden von Erweiterungen bei Bedarf
Visual Studio verschiebt seine Erweiterungen (und arbeitet auch mit Erweiterungen von Drittanbietern zusammen), damit sie erst bei Bedarf geladen werden, statt gleich beim IDE-Start. Möchten Sie wissen, welche Erweiterungen sich auf den Start, das Laden von Projektmappen und die Leistung bei der Eingabe auswirken? Sie finden diese Informationen unter „Hilfe“ > „Visual Studio-Leistung verwalten“.

  ![Dialogfeld „Optionen“ in Visual Studio 2017](~/ide/media/vs2017ide-manage-vs-perf.png "Visual Studio-Dialogfeld „Hilfe“ – Leistungsverwaltung")

## <a name="productivity-improvements"></a>Produktivitätsverbesserungen

### <a name="sign-in-across-multiple-accounts"></a>Anmelden mit mehreren Konten  
Wir haben in Visual Studio einen neuen Identitätsdienst eingeführt, der Ihnen die übergreifende Verwendung von Benutzerkonten in Team Explorer, Azure-Tools, Windows Store-Veröffentlichung und mehr ermöglicht.

Sie auch länger angemeldet bleiben. Visual Studio wird Sie nicht alle 12 Stunden auffordern, sich anzumelden. Weitere Informationen finden Sie im Blogbeitrag [Fewer Visual Studio Sign-in Prompts](https://blogs.msdn.microsoft.com/visualstudio/2016/08/15/fewer-visual-studio-sign-in-prompts/) (Weniger Anmeldeaufforderungen in Visual Studio).

### <a name="manage-your-extensions-with-roaming-extensions-manager"></a>Verwalten von Erweiterungen mit dem Roaming-Erweiterungs-Manager
Es ist einfacher, jede Entwicklungsumgebung mit Ihren bevorzugten Erweiterungen einzurichten, wenn Sie sich bei Visual Studio anmelden. Der neue Roaming-Erweiterungs-Manager verfolgt alle Ihre bevorzugten Erweiterungen nach, indem er eine synchronisierte Liste in der Cloud erstellt.  

Um eine Liste Ihrer Erweiterungen in Visual Studio anzuzeigen, klicken Sie auf „Extras“ > „Erweiterungen und Updates“, und klicken Sie dann auf den Roaming-Erweiterungs-Manager.

![Visual Studio 2017 – Dialogfeld „Erweiterungen und Updates“](~/ide/media/vs2017ide-extensions-and-updates.png "Visual Studio 2017 – „Extras“ > Dialogfeld „Erweiterungen und Updates“")

Der Roaming-Erweiterungs-Manager verfolgt alle von Ihnen installierten Erweiterungen nach, Sie können aber wählen, welche Ihrer Roamingliste hinzugefügt werden sollen.

![Visual Studio 2017 – Dialogfeld „Erweiterungen und Updates“](~/ide/media/vs2017ide-RoamingExtensionManager.png "Visual Studio 2017 – Roaming-Erweiterungs-Manager")

Wenn Sie den Roaming-Erweiterungs-Manager verwenden, werden Sie 3 Symboltypen in Ihrer Liste bemerken:
* ![Symbol für „Roaming erfolgt“](~/ide/media/vs2017ide-roamedicon.png "Symbol für „Roaming erfolgt“") ***Roaming erfolgt***: Eine Erweiterung, die in Ihrer Roamingliste enthalten, auf Ihrem Computer jedoch nicht installiert ist.
  (Erweiterungen dieses Typs können Sie mithilfe der Schaltfläche **Download** herunterladen.)
* ![Symbol für „Roaming und Installation erfolgt“](~/ide/media/vs2017ide-roamedinstalledicon.png "Symbol für „Roaming und Installation erfolgt“") ***Roaming und Installation erfolgt***: Alle Erweiterungen, die Teil dieser Roamingliste und in Ihrer Entwicklungsumgebung installiert sind.
  (Wenn Sie sich gegen das Roaming entscheiden, können Sie zum Entfernen die Schaltfläche **Roaming beenden** verwenden.)
* ![Symbol für „Installiert“](~/ide/media/vs2017ide-installedicon.png "Symbol für „Installiert“") ***Installiert***: Alle Erweiterungen, die in dieser Umgebung installiert, aber nicht in der Roamingliste enthalten sind.
  (Sie können der Roamingliste Erweiterungen mithilfe der Schaltfläche **Roaming starten** hinzufügen.)

Alle Erweiterungen, die Sie bei bestehender Anmeldung herunterladen, werden der Liste mit dem Status **Roaming und Installation erfolgt** hinzugefügt. Sie sind also Teil Ihrer Roamingliste, und daher haben Sie von jedem Computer aus darauf Zugriff.

### <a name="experience-live-architecture-dependency-validation-and-live-unit-testing"></a>Erleben Sie die Echtzeitüberprüfung der Architekturabhängigkeiten und Livekomponententests

Visual Studio kann Sie jetzt während der Eingabe von Code im Code-Editor in Echtzeit über Verletzungen von Architekturabhängigkeitsregeln benachrichtigen, und zwar mithilfe von Abhängigkeitsvalidierungsdiagrammen (auch bekannt als  Ebenendiagramme).

Fehler werden in der Fehlerliste angezeigt, und Wellenlinien im Text-Editor zeigen den genauen Ort der Regelverletzung an. Es ist nun unwahrscheinlicher, dass Sie unerwünschte Abhängigkeiten einführen.

![Echtzeitüberprüfung der Architektur](~/ide/media/vs2017ide-LiveArchitectureDepedendencyValidation.png "Echtzeitüberprüfung der Architekturabhängigkeiten")

#### <a name="live-unit-testing"></a>Livekomponententests:

In Visual Studio Enterprise 2017 liefern Ihnen Livekomponententests Livekomponententest-Ergebnisse und Codeabdeckung im Editor währende der Codierung. Dies funktioniert mit C#- und Visual Basic-Projekten für .NET Framework und unterstützt Testframeworks von MSTest, xUnit und NUnit.

![Livekomponententests](~/ide/media/lut-codewindow.png "Ein Beispiel unseres neuen Livekomponententest-Features in der Enterprise Edition von Visual Studio")

Weitere Informationen finden Sie im Blogbeitrag [Live Unit Testing in Visual Studio 2017 Enterprise (Verwenden von Livekomponententests in Visual Studio 2017 Enterprise Edition)](https://blogs.msdn.microsoft.com/visualstudio/2017/03/09/live-unit-testing-in-visual-studio-2017-enterprise/).

### <a name="devops"></a>DevOps
#### <a name="redgate-data-tools"></a>Redgate Data Tools:
Um DevOps-Funktionen für die Entwicklung der SQL Server-Datenbank zu erweitern, sind jetzt Redgate Data Tools in den folgenden Editionen von Visual Studio 2017 verfügbar.

In Visual Studio 2017 Enterprise sind enthalten:
- [Redgate ReadyRollCore ](http://www.red-gate.com/products/sql-development/readyroll/entrypage/microsoft-and-readyroll?utm_source=microsoft&utm_medium=link&utm_campaign=readyroll&utm_term=docs-newinvs) unterstützt Sie bei der Entwicklung von Migrationsskripts, dem Verwalten von Datenbankänderungen mithilfe von Quellcodeverwaltung und dem sicherem Automatisieren von Bereitstellungen der Änderungen an SQL Server-Datenbanken zusammen mit Anwendungsänderungen.
- [Redgate SQL Prompt Core](http://www.red-gate.com/products/sql-development/sql-prompt/entrypage/microsoft-and-sql-prompt?utm_source=microsoft&utm_medium=link&utm_campaign=sqlprompt&utm_term=docs-newinvs) unterstützt Sie beim schnelleren und genaueren Schreiben von SQL mithilfe intelligenter Codevervollständigung. Datenbank- und Systemobjekte sowie Schlüsselwörter werden während der Eingabe automatisch von SQL Prompt vervollständigt und es werden auch Spaltenvorschläge bereitgestellt. Dies führt zu optimiertem Code und weniger Fehlern, da Sie sich nicht jeden Spaltennamen oder Alias merken müssen.

In allen Editionen von Visual Studio 2017 ist enthalten:
- [Redgate SQL Search](http://www.red-gate.com/products/sql-development/sql-search/?utm_source=microsoft&utm_medium=link&utm_campaign=sqlsearch&utm_term=docs-newinvs) steigert Ihre Produktivität, weil Sie schnell nach SQL-Fragmenten und -Objekten in mehreren Datenbanken suchen können.

Weitere Informationen finden Sie in unserem Blogbeitrag [Redgate Data Tools in Visual Studio 2017](https://blogs.msdn.microsoft.com/visualstudio/2017/03/07/redgate-data-tools-in-visual-studio-2017/).

### <a name="visual-studio-ide-enhancements"></a>Verbesserungen der Visual Studio-IDE
#### <a name="interact-with-git"></a>Interaktion mit Git:
Wenn Sie in Visual Studio an einem Projekt arbeiten, können Sie Ihren Code für einen Git-Dienst einrichten, ihn schnell dahin übertragen und dort veröffentlichen. Sie können Ihre Git-Repositorys auch mit Menüklicks auf Schaltflächen in der unteren rechten Ecke der IDE verwalten.

![Visual Studio 2017-Dialogfeld zur Interaktion mit Git](~/ide/media/vsIDE-GitInteraction.png "Git-Tools in der Visual Studio-IDE")

#### <a name="view-and-navigate-code-with-structure-visualizer"></a>Anzeigen von und Navigation in Code mit der Strukturschnellansicht:
Die Strukturschnellansicht zeichnet Strukturhilfslinien (auch bekannt als  Einzugsführungslinien) in Ihrem Code. Damit können Sie jederzeit ohne zu scrollen visuell darstellen und ermitteln, in welchem Codeblock Sie sich befinden. Wenn Sie den Mauszeiger über die Zeilen bewegen, werden QuickInfos angezeigt, die Ihnen die Öffnung des Blocks und seine übergeordneten Elemente anzeigen. Dies ist sowohl für alle Sprachen verfügbar, die über TextMate-Grammatiken unterstützt werden, als auch für C#, Visual Basic und XAML.

![Visual Studio 2017 Strukturschnellansicht](~/ide/media/vsIDE-StructureVisualizer.png "Strukturschnellansicht in Visual Studio")

#### <a name="experience-improved-navigation-controls"></a>Benutzerfreundlichere Navigationssteuerelemente:
Wir haben die Benutzerfreundlichkeit der Navigation verbessert, sodass Sie mit größerer Sicherheit und weniger Ablenkung von A nach B gelangen.

* **Gehe zu** (STRG+F12) &ndash; navigieren Sie von jedem Basistyp oder Member zu dessen verschiedenen Implementierungen.

* **Gehe zu allen** (STRG+T oder STRG+,) &ndash; navigieren Sie direkt zu jeder beliebigen Datei-/Typ-/Member-/Symboldeklaration. Sie können die Ergebnisliste filtern oder die Abfragesyntax verwenden (z.B. „f Suchbegriff“ für Dateien, „t Suchbegriff“ für Typen usw.).

 ![Verbessertes „Gehe zu allen“](~/ide/media/vs2017ide-navigation-go-to.png "Beispiel für verbesserte „Gehe zu allen“-Funktion")

* **Alle Verweise suchen (UMSCHALT+F12)** &ndash; mit Syntaxfarbgebung können Sie „Alle Verweise suchen“-Ergebnisse nach einer Kombination aus Projekt, Definition und Pfad gruppieren. Sie können auch Ergebnisse „sperren“, damit Sie die Suche nach anderen Verweisen fortsetzen können, ohne die ursprünglichen Ergebnisse zu verlieren.

 ![Neues „Alle Verweise suchen“-Tool](~/ide/media/vs2017ide-find-all-references.png "Beispiel für neues „Alle Verweise suchen“-Tool")

* **Einzugsführungslinien** &ndash; punktierte, graue, vertikale Linien dienen nun als Orientierungshilfen im Code, um Kontext innerhalb Ihres Bezugssystems bereitzustellen. Vielleicht kennen Sie sie von den beliebten Produktivitäts-Power Tools.

Weitere Informationen zu unseren neuen Produktivitätsfeatures finden Sie im Blogbeitrag [Productivity in Visual Studio 2017](https://blogs.msdn.microsoft.com/visualstudio/2016/11/28/productivity-in-visual-studio-2017-rc/) (Produktivität in Visual Studio 2017) von Mark Wilson-Thomas.

### <a name="visual-c"></a>Visual C++
Sie werden eine Reihe von Verbesserungen in Visual Studio bemerken, z.B. die Verteilung von C++ Core Guidelines mit Visual Studio, die Aktualisierung des Compilers durch verbesserte Unterstützung für C++11- und C++-Features, Hinzufügen und Aktualisieren von Funktionalität in den C++-Bibliotheken. Wir haben auch die Leistung der C++-IDE, die Installation von Arbeitsauslastungen und anderes mehr verbessert.

Wir haben ebenfalls mehr als 250 Fehler und gemeldete Probleme mit dem Compiler und den Tools behoben, von denen viele durch Kunden über [Microsoft Connect](https://connect.microsoft.com/VisualStudio "Microsoft Connect") übermittelt wurden.

Eine vollständige Auflistung der Details finden Sie auf der Seite [Neues für Visual C++ in Visual 2017](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio).  

### <a name="debugging-and-diagnostics"></a>Debuggen und Diagnose

#### <a name="run-to-click"></a>Ausführung bis Klick:

Nun können Sie leichter während des Debuggens vorwärts springen, ohne einen Haltepunkt festlegen zu müssen, um in der gewünschten Zeile zu stoppen. Wenn Sie im Debugger angehalten werden, klicken Sie einfach auf das Symbol, das neben der Codezeile angezeigt wird, über der sich die Maus befindet. Die nächste Codeausführung wird nun an dieser Zeile anhalten, sobald sie im Codepfad erreicht wird.

![Visual Studio 2017-Debuggen – Ausführung bis Klick](~/ide/media/vs2017ide-RunToClick.png "Ausführung bis Klick in Visual Studio-Debuggen und Diagnose")

#### <a name="the-new-exception-helper"></a>Die neue Ausnahmen-Hilfe:

Die neue Ausnahmen-Hilfe hilft Ihnen, Ihre Ausnahmeinformationen auf einen Blick anzeigen. Die Informationen werden in einem kompakten Format mit unmittelbarem Zugriff auf die inneren Ausnahmen angezeigt. Wenn Sie eine NullReferenceException diagnostizieren, können Sie direkt in der Ausnahme-Hilfe schnell sehen, was NULL war.

![Das neue Dialogfeld „Ausnahmehilfsprogramm“ in Visual Studio](~/ide/media/vs2017ide-ExceptionHelper.png "Das neue Dialogfeld „Ausnahmehilfsprogramm“")

Weitere Informationen finden Sie im Blogbeitrag [Using the New Exception Helper in Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/) (Verwenden der neuen Ausnahmen-Hilfe in Visual Studio).

## <a name="talk-to-us"></a>Sprechen Sie mit uns  
 Warum sollten Sie dem Visual Studio-Team ein Feedback senden? Weil wir das Feedback unserer Kunden ernst nehmen. Es gibt den Anstoß zu vielen unserer Initiativen.  

Wenn Sie einen Vorschlag zu möglichen Verbesserungen von Visual Studio machen oder ein Problem melden möchten, finden Sie weitere Informationen auf der Seite [Talk to Us](../ide/talk-to-us.md).  

### <a name="report-a-problem"></a>Problem melden  
 Manchmal reicht eine Nachricht nicht aus, um das gesamte Ausmaß eines Problems, auf das Sie gestoßen sind, deutlich zu machen. Wenn bei Ihnen Hängen, Abstürze oder andere Leistungsprobleme auftreten, können Sie die Schritte zur Reproduktion und unterstützende Dateien (wie etwa Screenshots, Ablaufverfolgungsdateien und Heap-Speicherabbilder) auf einfache Weise mithilfe des Tools **Problem melden** mit uns teilen. Weitere Informationen zur Verwendung dieses Tools finden Sie auf der Seite [Melden eines Problems](how-to-report-a-problem-with-visual-studio-2017.md).  

### <a name="track-your-issue-in-connect"></a>Verfolgen Ihres Problems in Connect  
 Wenn Sie den Status Ihres Visual Studio-Feedbacks verfolgen möchten, rufen Sie [Connect](http://connect.microsoft.com/) auf, und melden Sie den Fehler dort. Nach der Meldung können Sie zu Connect zurückkehren, um den Status zu überprüfen.  

## <a name="see-also"></a>Siehe auch  
* [Neues in Visual C++](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)
* [Neues in C#](https://docs.microsoft.com/en-us/dotnet/csharp/csharp-7)  
* [Neues für Team Foundation Server](https://www.visualstudio.com/en-us/docs/whats-new)
* [Visual Studio – Anmerkungen zu dieser Version](https://www.visualstudio.com/news/vs2015-vs)

