---
title: Visual Studio 2015 | Microsoft-Dokumentation
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.topic: conceptual
ms.assetid: 772b6cf4-cee5-42d0-bc18-b4eb07e22ff0
caps.latest.revision: 36
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 52e0b8f87774b11b1750700d5bef19c5423824c4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667142"
---
# <a name="visual-studio-ide"></a>Visual Studio-IDE
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Microsoft Visual Studio 2015 ist eine Suite von Tools zum Erstellen von Software, von der Planungsphase über das Entwerfen, Codieren, Testen und Debuggen der Benutzeroberfläche und das Analysieren der Codequalität und -leistung bis hin zur Bereitstellung beim Kunden und zum Sammeln von Telemetriedaten hinsichtlich der Nutzung. Diese Tools wurden für eine möglichst reibungslose Zusammenarbeit konzipiert und werden alle über die integrierte Entwicklungsumgebung (Integrated Development Environment, IDE) von Visual Studio bereitgestellt.

Sie können Visual Studio verwenden, um verschiedene Anwendungen zu erstellen, von einfachen Store-Apps und Spielen für mobile Clients bis hin zu großen, komplexen Systemen für den Betrieb von Unternehmen und Datencentern. Sie können Folgendes erstellen:

- Apps und Spiele, die nicht nur unter Windows ausgeführt werden können, sondern auch unter Android und iOS.

- Websites und Webdienste basierend auf ASP.NET, JQuery, AngularJS und anderen beliebten Frameworks.

- Anwendungen für so unterschiedliche Plattformen und Geräte wie Azure, Office, Sharepoint, Hololens, Kinect und das Internet der Dinge, um nur einige zu nennen.

- Spiele und grafikintensive Anwendungen für eine Vielzahl von Windows-Geräten, die DirectX verwenden, darunter auch die Xbox.

Visual Studio unterstützt standardmäßig C#, C und C++, JavaScript, F# und Visual Basic. Visual Studio lässt sich problemlos mit Drittanbieteranwendungen einsetzen und in diese integrieren. Nutzen Sie für Unity die Erweiterung [Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md) und für Apache Cordova [Visual Studio Tools für Apache Cordova](https://msdn.microsoft.com/library/db446f2c-6ba4-4c76-aac5-4c66f43b8c42). Sie können Visual Studio selbst erweitern, indem Sie benutzerdefinierte Tools erstellen, die spezielle Aufgaben ausführen.

Wenn Sie Visual Studio noch nie verwendet haben, können Sie sich mit den Lernprogrammen und exemplarischen Vorgehensweisen unter [Get Started Developing with Visual Studio](../ide/get-started-developing-with-visual-studio.md) schnell einarbeiten.

Weitere Informationen zu den neuen Features in Visual Studio 2015 finden Sie unter [Neuerungen in Visual Studio 2015](../what-s-new-in-visual-studio-2015.md).

## <a name="visual-studio-setup"></a>Setup von Visual Studio
 Informationen darüber, welche Edition von Visual Studio die für Sie passende ist, finden Sie unter [Visual Studio – Editionen](http://www.visualstudio.com/products/visual-studio-with-msdn-overview-vs).

 Sie können Visual Studio 2015 installieren, indem Sie es von [Visual Studio Downloads](http://www.visualstudio.com/downloads/download-visual-studio-vs.aspx)herunterladen. Weitere Informationen zum Installationsvorgang finden Sie unter [Installieren von Visual Studio 2015](../install/install-visual-studio-2015.md).

## <a name="ide-basics"></a>IDE-Grundlagen
 Das folgende Bild zeigt die Visual Studio-IDE mit einem geöffneten Projekt, das Fenster "Projektmappen-Explorer" für die Navigation in den Projektdateien und das Fenster "Team Explorer" für die Navigation in der Quellcodeverwaltung und die Arbeitselementnachverfolgung. Die in der Titelleiste hervorgehobenen Funktionen werden im Folgenden ausführlicher erläutert.

 ![Visual Studio-IDE](../ide/media/visualstudioide.png "|::ref1::|")

### <a name="signing-in"></a>Anmelden
 Wenn Sie Visual Studio zum ersten Mal starten, können Sie sich mit Ihrem Microsoft-Konto oder Ihrem Arbeits- oder Schulkonto anmelden. Durch die Anmeldung können Sie Ihre Einstellungen, wie z. B. Fensterlayouts, auf mehreren Geräten synchronisieren und automatisch eine Verbindung mit den benötigten Diensten herstellen, z. B. Azure-Abonnements und Visual Studio Team Services. Bei einer abonnementbasierten Lizenz müssen Sie sich regelmäßig bei Visual Studio anmelden, um den Lizenztoken aktuell zu halten. Wenn Sie über eine Product Key-Lizenz verfügen, müssen Sie sich nicht anmelden; eine Anmeldung vereinfacht jedoch das Herstellen einer Verbindung mit Visual Studio Team Services und Ihren Konten bei Azure, Office 365 und Salesforce.com. Weitere Informationen finden Sie unter [Anmelden bei Visual Studio](../ide/signing-in-to-visual-studio.md).

 Wenn Sie über mehrere Visual Studio Team Services-Konten, Azure-Konten oder MSDN-Abonnements verfügen, können Sie sie verknüpfen und mittels einmaliger Anmeldung auf die Ressourcen und Dienste in all Ihren Konten zugreifen. Weitere Informationen finden Sie unter [Work with multiple user accounts](../ide/work-with-multiple-user-accounts.md).

### <a name="staying-up-to-date"></a>Stets auf dem aktuellen Stand
 Das Benachrichtigungssymbol in der oberen rechten Ecke der Titelleiste zeigt Ihnen, dass Updates für Visual Studio oder andere zugehörige Komponenten, die Sie installiert haben, verfügbar sind. Sie können auswählen, ob Sie diese Benachrichtigungen verwerfen oder darauf reagieren möchten. Weitere Informationen finden Sie unter [Visual Studio-Benachrichtigungen](../ide/visual-studio-notifications.md).

### <a name="finding-things-and-getting-help"></a>Suchen von Informationen und Nutzen der Hilfe
 Das im Folgenden gezeigte Fenster [Schnellstart](../ide/reference/quick-launch-environment-options-dialog-box.md) bietet eine schnelle Möglichkeit, um Befehle, Tools, Funktionen usw. von Visual Studio zu suchen, wenn Sie die Tastenkombination oder die Menüposition nicht kennen. Geben Sie einfach ein, wonach Sie suchen, damit „Schnellstart“ Ihnen einen Link zur gewünschten Option bereitstellen kann.

 ![Schnellstartergebnisse für „Neues Projekt“](../ide/media/productivity-quicklaunch.png "|::ref2::|")

 MSDN ist die Microsoft-Website für die technische Dokumentation – die Seite, die Sie gerade lesen, befindet sich auf MSDN. Drücken Sie in Visual Studio die Taste **F1** , um die MSDN-Hilfeseite für das aktive Fenster aufzurufen. Sie können auch im Code-Editor **F1** drücken, um die MSDN-Hilfeseite für die API oder das Schlüsselwort an der aktuellen Position der Einfügemarke aufzurufen. Platzieren Sie zum Beispiel in einer C#-Datei die Einfügemarke an einer beliebigen Stelle in oder am Ende einer `System.String`-Deklaration, und drücken Sie **F1**, um die MSDN-Hilfeseite für <xref:System.String> zu öffnen.

### <a name="giving-feedback"></a>Bereitstellen von Feedback
 Sie können uns problemlos jederzeit Feedback zu Visual Studio geben. Klicken Sie auf der Titelleiste neben **QuickLaunch** auf das Feedback-Symbol, und klicken Sie dann auf die Option zum **Melden eines Problems** oder zum **Unterbreiten eines Vorschlags**. Vorabversionen von Visual Studio weisen auch eine Option zum **Bewerten des Produkts** auf. Wir sehen uns alle Kommentare an und verwenden sie, um das Produkt zu verbessern. Weitere Informationen finden Sie unter [Talk to Us](../ide/talk-to-us.md).

### <a name="personalizing-the-ide"></a>Personalisieren der IDE
 Sie können das Fensterlayout an Ihren Entwicklungsstil anpassen. Sie können jedes Fenster jederzeit ausblenden, andocken oder die Verankerung aufheben. Sie können den Editor auch im Vollbildmodus ausführen. Sie können mehrere benutzerdefinierte Fensterlayouts erstellen und speichern, die nur die Fenster anzeigen, die Sie für den jeweiligen Kontext benötigen. Sie können z. B. ein Vollbildlayout erstellen, sodass Sie nur den Code-Editor sehen. Darüber hinaus können Sie unterschiedliche Layouts für das Debuggen und für Teamvorgänge erstellen. Weitere Informationen finden Sie unter [Anpassen der Fensterlayouts](../ide/customizing-window-layouts-in-visual-studio.md).

 Sie können Visual Studio in vielerlei Hinsicht anpassen und Ihre Einstellungen übertragen, wenn Sie mit mehreren Computern arbeiten. Weitere Informationen finden Sie unter [Personalisieren der IDE](../ide/personalizing-the-visual-studio-ide.md).

 Es gibt für nahezu jede Option eine Tastenkombination, die Sie ebenfalls anpassen können. Um neue Tastaturkombinationen zu erstellen, geben Sie im Fenster „Schnellstart“ „Tastatur“ ein, um das Dialogfeld „Tastatur“ zu öffnen. Dort können Sie F1 drücken, um die MSDN-Hilfeseite aufzurufen, wenn Sie weitere Informationen zu den Optionen benötigen. Weitere Informationen finden Sie unter [Standardtastenkombinationen in Visual Studio](../ide/default-keyboard-shortcuts-in-visual-studio.md).

## <a name="connecting-to-visual-studio-team-services-and-team-foundation-server"></a>Herstellen einer Verbindung zu Visual Studio Team Services und Team Foundation Server
 Visual Studio Online Team Services (VSTS) ist ein cloudbasierter Dienst zum Hosten von Softwareprojekten und für die Zusammenarbeit in Teams. VSTS unterstützt Git- und Team Foundation-Quellcodeverwaltungssysteme sowie die Scrum-, CMMI- und Agile-Entwicklungsmethoden. Team Foundation-Versionskontrolle (TFVC) verwendet ein einzelnes, zentralisiertes Serverrepository zum Nachverfolgen von Versionsdateien. Lokale Änderungen werden immer beim zentralen Server eingecheckt, damit andere Entwickler die neuesten Änderungen abrufen können. Team Foundation Server (TFS) 2015 ist der Anwendungslebenszyklus-Verwaltungshub für Visual Studio. Auf diese Weise können alle am Entwicklungsprozess beteiligten Personen mithilfe einer einzigen Projektmappe am Prozess teilnehmen. TFS ist auch nützlich für die Verwaltung heterogener Teams und Projekte.

 Wenn Sie in Ihrem Netzwerk über ein Visual Studio Team Services-Konto oder einen Team Foundation Server verfügen, können Sie über das Fenster "Team Explorer" eine Verbindung mit dem Konto bzw. Server herstellen. Über dieses Fenster können Sie Code in die Quellcodeverwaltung einchecken oder daraus auschecken, Arbeitselemente verwalten, Builds starten und auf Teamräume und Arbeitsbereiche zugreifen. Sie können Team Explorer über den **Schnellstart** oder das Hauptmenü über **Anzeigen > Team Explorer** oder über **Team > Verbindungen verwalten** öffnen.  Weitere Informationen zu Visual Studio Team Services finden Sie unter [www.visualstudio.com](https://www.visualstudio.com/). Weitere Informationen über Team Foundation Server finden Sie unter [Team Foundation Server](https://www.visualstudio.com/products/tfs-overview-vs).

 Die folgende Abbildung zeigt den Team Explorer-Bereich für eine Projektmappe, die in VSTS gehostet wird:

 ![Visual Studio Team Explorer](../ide/media/vs2015-teamexplorer.png "|::ref3::|")

## <a name="creating-solutions-and-projects"></a>Erstellen von Projektmappen und Projekten
 Auch wenn Sie Visual Studio zum Durchsuchen einzelner Codedateien verwenden können, so arbeiten Sie jedoch meist in einem *Projekt*. Ein Visual Studio-Projekt ist eine Sammlung von Dateien und Ressourcen, die zu einer einzelnen ausführbaren Binärdatei für Anwendungen (z. B. eine EXE-, DLL- oder APPX-Datei) kompiliert werden. Bei Nicht-ASP.NET-Websites wird keine ausführbare Datei erstellt und das Projekt enthält nur die HTML- und JavaScript-Dateien sowie Bilder. Da Sie gelegentlich mehrere Binärdateien oder Websites erstellen möchten, die eng miteinander verknüpft sind, gibt es in Visual Studio das Konzept der Projektmappe, die mehrere Projekte oder Websites enthalten kann. Wenn Sie ein Projekt erstellen, erstellen Sie im Grunde ein Projekt in einer Projektmappe, der Sie später bei Bedarf weitere Projekte hinzufügen können. Wenn Sie beispielsweise über ein DLL-Projekt verfügen, können Sie der Projektmappe ein EXE-Projekt hinzufügen, das diese DLL lädt und nutzt.

 Eine *Projektvorlage* ist eine Sammlung von vorgegebenen Codedateien und Konfigurationseinstellungen, die Sie schnell einrichten können, um eine bestimmte Art von Anwendung zu erstellen. Visual Studio enthält viele Projektvorlagen. Wenn keine der Standardvorlagen für Sie geeignet ist, können Sie eine eigene erstellen. Nachdem Sie ein Projekt mit einer Vorlage erstellt haben, können Sie darin Ihren eigenen Code schreiben, sprich entweder in den bereitgestellten Dateien oder in neuen, von Ihnen hinzugefügten Dateien. Weitere Informationen finden Sie unter [Projektmappen und Projekte](../ide/solutions-and-projects-in-visual-studio.md). Die folgende Abbildung zeigt das Dialogfeld "Neues Projekt" mit den Projektvorlagen, die für ASP.NET-Anwendungen verfügbar sind.

 ![Visual Studio, Dialogfeld „Neues Projekt“](../ide/media/vs2015-newprojectdialog.png "|::ref4::|")

## <a name="designing-the-user-interface"></a>Entwerfen der Benutzeroberfläche
 Ein Designer ist ein intuitives Tool, das es Ihnen ermöglicht, eine Benutzeroberfläche zu erstellen, ohne Code schreiben zu müssen. Sie können Steuerelemente der Benutzeroberfläche, z. B. Listenfelder, Kalender und Schaltflächen aus dem Fenster [Toolbox](../ide/reference/toolbox.md) auf eine Entwurfsoberfläche ziehen, die das Fenster oder Dialogfeld darstellt. Sie können die Größe der Elemente ändern oder sie neu anordnen, ohne Code zu schreiben. Es gibt Designer für jeden Projekttyp, der eine Benutzeroberfläche umfasst.

 Wenn das Projekt eine XAML-basierte Benutzeroberfläche hat, ist Blend der Standard-Designer für Visual Studio – ein anspruchsvolles Grafiktool, das nahtlos mit Visual Studio zusammenarbeitet.

 ![Zeichenfläche](../ide/media/b5-artboard.png "|::ref5::|")

|||
|-|-|
|![](../designers/media/b1-1.png "B1_1")|**Designansicht** : Zeigt den visuellen Entwurf des Dokuments an. In dieser Ansicht können Sie Objekte auf der Entwurfsoberfläche zeichnen oder ändern.|
|![](../designers/media/b1-2.png "B1_2")|**Breadcrumb** : Schalten Sie schnell zwischen dem Vorlagenbearbeitungsmodus, Stilbearbeitungsmodus und Bearbeitungsbereich für ein ausgewähltes Objekt um.|
|![](../designers/media/b1-3.png "B1_3")|**Zoom** Wird verwendet, um die Ansicht der Entwurfsoberfläche oder der Objekte auf der Entwurfsoberfläche zu verkleinern/vergrößern.|
|![](../designers/media/b1-4.png "B1_4")|**Steuerelemente der Entwurfsoberfläche** Verwenden Sie diese Steuerelemente (**Ausrichtungsgitter anzeigen**, **An Rasterlinien ausrichten** und **Andocken an Ausrichtungslinien aktivieren/deaktivieren**), um die Andockoptionen festzulegen. Das Andocken eignet sich zum Aneinanderreihen von Objekten oder zum gleichmäßigen Verteilen von Linien auf der Entwurfsoberfläche.|
|![](../designers/media/b1-5.png "B1_5")|**Code-Editor** : Bearbeiten Sie Code in XAML, C#, C++ oder Visual Basic manuell im Code-Editor.|

 Weitere Informationen finden Sie unter [Entwerfen von XAML-Code in Visual Studio](../designers/designing-xaml-in-visual-studio.md).

## <a name="writing-navigating-and-understanding-code"></a>Schreiben, Navigieren und Verstehen von Code
 Als Entwickler arbeiten Sie hauptsächlich mit dem Editor-Fenster. Visual Studio enthält Editoren für C#, C++, Visual Basic, JavaScript, XML, HTML, CSS und F#. Darüber hinaus bieten Drittanbieter Plug-In-Editoren (und Compiler) für viele weitere Sprachen.

 Sie können einzelne Dateien im Text-Editor bearbeiten, indem Sie auf **Datei > Öffnen > Datei** klicken. klicken. Klicken Sie zum Bearbeiten von Dateien in einem geöffneten Projekt im Projektmappen-Explorer auf den Dateinamen. Der Code wird eingefärbt, und Sie können das Farbschema durch Eingabe von „Farben“ in der Schnellstartleiste personalisieren. Sie können im Text-Editor viele Fenster im Registerkartenformat gleichzeitig geöffnet haben. Sie können jedes Fenster unabhängig teilen. Sie können den Text-Editor auch im Vollbildmodus ausführen.

 ![GreetingsConsoleApp.cpp im Code-Editor](../ide/media/c-ide-editorlinenumberswordwrapon.png "|::ref11::|")

 Der Text-Editor ist hochgradig interaktiv (falls Sie dies wünschen) und bietet viele Produktivitätsfeatures, mit denen Sie schneller besseren Code schreiben können. Die Features sind je nach Sprache unterschiedlich, und Sie müssen keine davon verwenden (geben Sie in der Schnellstartleiste "Editor" ein), um Funktionen zu aktivieren oder zu deaktivieren. Im Folgenden finden Sie einige der allgemeinen Produktivitätsfeatures:

1. [Refactoring](../ide/refactoring-in-visual-studio.md) enthält die Vorgänge, wie z. B. intelligentes Umbenennen von Variablen, Verschieben von ausgewählten Codezeilen in eine separate Funktion, Verschieben von Code an eine andere Position und Neuanordnen von Funktionsparametern.

2. *IntelliSense* ist der Oberbegriff für einen Satz von beliebten Features, mit denen Typinformationen über den Code direkt im Editor angezeigt und in einigen Fällen kleine Codeabschnitte für Sie geschrieben werden. Damit verfügen Sie über eine grundlegende Dokumentation, die in den Editor integriert ist, sodass Sie die Typinformationen nicht mehr in einem separaten Hilfefenster nachschauen müssen. Die Features von IntelliSense variieren je nach Sprache. Weitere Informationen finden Sie unter [Visual C# IntelliSense](../ide/visual-csharp-intellisense.md), [Visual C++ Intellisense](../ide/visual-cpp-intellisense.md), [JavaScript IntelliSense](../ide/javascript-intellisense.md), [Visual Basic-Specific IntelliSense](../ide/visual-basic-specific-intellisense.md). Die folgende Abbildung zeigt einige IntelliSense-Features:

    ![Visual Studio, Member-Liste](../ide/media/vs2015-intellisense.png "|::ref12::|")

3. Mit**Wellenlinien** werden Sie in Echtzeit auf Fehler oder mögliche Probleme in Ihrem Code hingewiesen, sodass Sie diese unmittelbar und noch vor der Kompilierung oder der Laufzeit beheben können. Wenn Sie auf die Wellenlinie zeigen, werden zusätzliche Informationen zum Fehler angezeigt. Am linken Rand wird u. U. auch eine Glühbirne mit Vorschlägen zum Beheben des Fehlers angezeigt. Weitere Informationen finden Sie unter [Perform quick actions with light bulbs](../ide/perform-quick-actions-with-light-bulbs.md).

    ![Glühbirne mit Mauszeigerbewegung](../ide/media/vs2015-lightbulb-hover.png "|::ref13::|")

4. [Textmarken](../ide/setting-bookmarks-in-code.md) ermöglichen es Ihnen, schnell zu bestimmten Zeilen in Dateien zu navigieren, an denen Sie aktiv arbeiten.

5. Das Fenster [Call Hierarchy](../ide/reference/call-hierarchy.md) kann über das Text-Editor-Kontextmenü geöffnet werden. Es enthält die von der Methode unter der Einfügemarke aufzurufenden bzw. aufgerufenen Methoden.

6. Mit**CodeLens** können Sie nach Codeverweisen, Änderungen an Ihrem Code, verknüpften Fehlern, Arbeitselemente, Codeüberprüfungen und Komponententests suchen, ohne den Editor verlassen zu müssen. Weitere Informationen finden Sie unter [Ermitteln von Änderungen am Code und anderer Verläufe](../ide/find-code-changes-and-other-history-with-codelens.md).

7. Das Fenster **Definitionsvorschau** zeigt integriert eine Methode oder eine Typdefinition, ohne den aktuellen Kontext verlassen zu müssen. Dieses Fenster unterstützt jetzt auch XAML.

8. Über die Kontextmenüoption **Gehe zu Definition** gelangen Sie direkt an die Stelle, an der die Funktion oder das Objekt definiert ist. Durch einen Klick mit der rechten Maustaste im Editor sind auch andere Navigationsbefehle verfügbar.

9. Ein verwandtes Tool, der [Objektkatalog](https://msdn.microsoft.com/f89acfc5-1152-413d-9f56-3dc16e3f0470), ermöglicht es Ihnen, .NET- oder Windows-Runtime-Assemblys auf Ihrem System zu überprüfen, um zu ermitteln, welche Typen sie enthalten und welche Methoden und Eigenschaften diese Typen enthalten.

     ![„System.Timer“ im Objekt-Browser](../ide/media/objectbrowser.png "|::ref14::|")

   Die meisten Elemente im Menü "Bearbeiten" und im Menü "Ansicht" beziehen sich in irgendeiner Form auf den Code-Editor. Weitere Informationen zum Editor finden Sie unter [Codeerstellung](../ide/writing-code-in-the-code-and-text-editor.md) und [Codebearbeitung](https://www.visualstudio.com/features/ide-vs).

## <a name="compiling-and-building-your-code"></a>Kompilieren und Erstellen von Code

Zum Erstellen eines Projekts müssen Sie den Quellcode kompilieren und alle Schritte durchführen, die erforderlich sind, um die ausführbare Datei zu erstellen. Für verschiedene Sprachen sind verschiedene Buildvorgänge erforderlich, und reguläre Websites lassen sich gar nicht erstellen. Unabhängig vom Projekttyp finden sich diese Befehle standardmäßig im Menü „Build“. Zum Kompilieren und Ausführen des Codes mit einer einzigen Tastatureingabe drücken Sie F5. Alle Compiler sind über die IDE vollständig konfigurierbar. Über die Build-Symbolleiste können Sie angeben, ob eine Debugversion des Programms mit Symbolen und zusätzlicher Fehlerprüfung zur Unterstützung von Haltepunkten und Einzelschritten im Debugger oder ob ein Releasebuild erstellt werden soll, der letztendlich den Kunden bereitgestellt wird. Auf der Eigenschaftenseite eines Projekts können Sie weitere Einstellungen für das Erstellen sowie viele andere Einstellungen konfigurieren. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Projektknoten, und wählen Sie „Eigenschaften“. Sie können Builds auch von der Befehlszeile aus ausführen.

Die Ausgabe des Builds, einschließlich der Fehler- oder Erfolgsbenachrichtigungen, wird im **Ausgabefenster** angezeigt. Auf der **Fehlerliste** werden detaillierte Informationen zu Buildfehlern aufgeführt.

## <a name="debugging-your-code"></a>Debuggen von Code
 Der neuartige Debugger von Visual Studio ermöglicht es Ihnen, Code in Ihrem lokalen Projekt, auf einem Remotegerät oder in einem Emulator wie dem für Android oder Windows Phone zu debuggen. Sie können die Anweisungen schrittweise durchlaufen und jeweils die Variablen überprüfen, Sie können Anwendungen mit mehreren Threads durchlaufen und Sie können Haltepunkte festlegen, die nur erreicht werden, wenn eine angegebene Bedingung "true" ist. All dies kann im Code-Editor selbst konfiguriert werden, damit Sie den Codekontext nicht verlassen müssen.

 ![Peek-Fenster für Haltepunkteinstellungen](../ide/media/dbg-breakpoints-peekwindow.png "|::ref15::|")

 Der Debugger selbst verfügt über verschiedene Fenster, mit denen Sie lokale Variablen, die Aufrufliste und andere Aspekte der Laufzeitumgebung anzeigen und bearbeiten können. Sie können diese Fenster über das Menü **Debuggen** aufrufen.

 Das [Immediate Window](../ide/reference/immediate-window.md) ermöglicht es Ihnen, einen Ausdruck einzugeben und unmittelbar das Ergebnis zu sehen.

 Das Fenster [IntelliTrace](https://msdn.microsoft.com/629e9660-c59a-446b-8c30-290059158f61) zeichnet jeden Aufruf einer Methode und andere Ereignisse in einem laufenden .NET-Programm auf und kann Ihnen dabei helfen, schnell herauszufinden, was die Ursache für ein Problem ist.

 Weitere Informationen finden Sie unter [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md).

## <a name="testing-your-code"></a>Testen von Code
 Visual Studio enthält ein Komponententest-Framework für verwalteten Code (.NET) und eins für systemeigenes C++. Zum Erstellen von Komponententests fügen Sie der Projektmappe einfach ein Testprojekt hinzu, schreiben die Tests und führen sie im Fenster "Test-Explorer" aus. Weitere Informationen finden Sie unter [Komponententests des Codes](../test/unit-test-your-code.md).

 ![Komponententest-Explorer](../ide/media/ute-failedpassednotrunsummary.png "|::ref16::|")

## <a name="analyzing-code-quality-and-performance"></a>Analysieren der Codequalität und Leistung
 Visual Studio umfasst leistungsstarke Tools für die statische Analyse und die Laufzeitanalyse. Die Tools für eine statische Analyse können Ihnen dabei helfen, potenzielle Fehler hinsichtlich des Entwurfs, der Globalisierung, Interoperabilität, Leistung, Sicherheit und anderer Kategorien zu identifizieren. Mithilfe von Leistungstests oder der Profilerstellung können Sie messen, wie Ihr Programm ausgeführt wird. Rufen Sie diese Tools über das Menü **Analysieren** auf. Weitere Informationen finden Sie unter [Qualitätsverbesserung mit Visual Studio-Diagnosetools](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945).

## <a name="connecting-to-cloud-services-and-databases"></a>Herstellen einer Verbindung mit Clouddiensten und Datenbanken
 Das Fenster [Server-Explorer](https://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d) in Visual Studio zeigt die Ressourcen in allen Konten, die unter Ihrem Personalisierungskonto verwaltet werden (d. h. das Konto, mit dem Sie sich angemeldet haben), darunter die SQL Server-Instanzen, Azure, salesforce.com, Office 365 sowie Websites.

 ![Server-Explorer](../ide/media/vs2015-serverexplorer3.png "|::ref17::|")

 Visual Studio enthält [Microsoft SQL Server Data Tools](https://msdn.microsoft.com/data/tools.aspx) (SSDT), die es Ihnen ermöglichen, Datenbanken zu erstellen, zu debuggen, zu verwalten und umzugestalten. Sie können mit einem Datenbankprojekt oder direkt mit einer Instanz einer verbundenen Datenbank lokal oder extern arbeiten.

 Der Objekt-Explorer von SQL Server in Visual Studio bietet eine Anzeige der Datenbankobjekte ähnlich der von SQL Server Management Studio. Mit dem Objekt-Explorer von SQL Server können Sie leichte Verwaltungs- und Designarbeiten für Datenbanken durchführen, darunter Bearbeiten von Tabellendaten, Vergleichen von Schemas und Ausführen von Abfragen mithilfe von Kontextmenüs direkt aus dem Objekt-Explorer von SQL Server. SSDT enthalten auch spezielle Projekttypen und Tools zum Entwickeln von SQL Server 2012 Analysis Services-, Reporting Services- und Integration Services Business Intelligence-Lösungen (BI, ehemals Business Intelligence Development Studio).

 ![SQL Server-Objekt-Explorer](../ide/media/vs2015-sqlobjectexplorer.png "|::ref18::|")

## <a name="deploying-your-finished-application"></a>Bereitstellen der fertigen Anwendung
 Wenn Ihre Anwendung für die Bereitstellung beim Kunden bereit ist, bietet Visual Studio die dazu benötigten Tools, unabhängig davon, ob Sie sie im Windows Store, auf einer Sharepoint-Website oder mit InstallShield- oder Windows Installer-Technologien bereitstellen möchten. Sie können auf alle Tools über die IDE zugreifen. Weitere Informationen finden Sie unter [Bereitstellen von Anwendungen, Diensten und Komponenten](../deployment/deploying-applications-services-and-components.md).

## <a name="architecture-and-modeling-tools-enterprise-only"></a>Architektur- und Modellierungstools (nur Enterprise)
 Sie können die Visual Studio-Tools für Architektur und Modellierung verwenden, um Ihre App zu entwerfen und zu modellieren. Mit diesen Tools können Sie die Struktur, das Verhalten und Beziehungen Ihres Codes visualisieren. Sie können im Rahmen des Entwicklungsprozesses Modelle unterschiedlichen Detaillierungsgrads während des gesamten Lebenszyklus der Anwendung erstellen. Sie können Anforderungen, Aufgaben, Testfälle, Fehler oder andere Arbeitsschritte nachverfolgen, die den Modellen zugeordnet sind, indem Sie Modellelemente mit Team Foundation Server-Arbeitselemente und dem Entwicklungsplan verknüpfen. Weitere Informationen finden Sie unter [Entwerfen und Modellieren Ihrer App](../modeling/analyze-and-model-your-architecture.md).

## <a name="extending-visual-studio-through-the-visual-studio-sdk"></a>Erweitern von Visual Studio mit dem Visual Studio SDK
 Visual Studio ist eine erweiterbare Plattform. Eine Visual Studio-Erweiterung ist ein benutzerdefiniertes Tool, das in die IDE integriert werden kann. Sie können Erweiterungen von Drittanbietern hinzufügen oder eigene erstellen. Weitere Informationen finden Sie unter [Entwickeln von Visual Studio-Erweiterungen](https://msdn.microsoft.com/library/5b1b5db3-6005-44cf-83b0-e608d7764d14).

 Die [Visual Studio User Experience Guidelines](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md) sind eine wichtige Referenz für jeden, der Erweiterungen für Visual Studio schreibt. Diese plattformspezifischen Leitfäden bieten Informationen Design, Schriftarten, Farben, Symbolen, Steuerelementen in Dialogfeldern sowie zu weiteren Interaktionsmustern, die dazu beitragen, dass Ihr neues Feature sich nahtlos in Visual Studio integrieren lässt.

## <a name="in-this-guide"></a>In diesem Handbuch

|||
|-|-|
|[Benutzerkonten und Updates](../ide/user-accounts-and-updates.md)|[Personalisieren der IDE](../ide/personalizing-the-visual-studio-ide.md)|
|[Vorgehensweise: Navigieren in der IDE](../ide/how-to-move-around-in-the-visual-studio-ide.md)|[Erste Schritte mit der Entwicklung in Visual Studio](../ide/get-started-developing-with-visual-studio.md)|
|[Suchen und Verwenden von Visual Studio-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md)|[Projektmappen und Projekte](../ide/solutions-and-projects-in-visual-studio.md)|
|[Schreiben von Code](../ide/writing-code-in-the-code-and-text-editor.md)|[Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md)|
|[Profilerstellungstools](../profiling/profiling-tools.md)|[Verbessern der Codequalität](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)|
|[Entwerfen von Benutzeroberflächen](../designers/designing-user-interfaces.md)|[Analysieren und Modellieren der Architektur](../modeling/analyze-and-model-your-architecture.md)|
|[Kompilieren und Erstellen](../ide/compiling-and-building-in-visual-studio.md)|[Bereitstellen von Anwendungen, Diensten und Komponenten](../deployment/deploying-applications-services-and-components.md)|
|[Visual Studio-IDE-64-Bit-Unterstützung](../ide/visual-studio-ide-64-bit-support.md)|[Sicherheit](../ide/security-in-visual-studio.md)|
|[Visual Studio-Beispiele](../ide/visual-studio-samples.md)|[Microsoft Help Viewer](../ide/microsoft-help-viewer.md)|
|[Globalisieren und Lokalisieren von Anwendungen](../ide/globalizing-and-localizing-applications.md)|[Benutzeroberflächenreferenz](../ide/reference/general-user-interface-elements-visual-studio.md)|

## <a name="see-also"></a>Siehe auch

- [Installieren von Visual Studio 2015](../install/install-visual-studio-2015.md)
- [Codebearbeitung](https://www.visualstudio.com/features/ide-vs)
- [Neues in Visual Studio 2015](../what-s-new-in-visual-studio-2015.md)
- [Portieren, Migrieren und Upgraden von Visual Studio-Projekten](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)
- [Sprechen Sie mit uns](../ide/talk-to-us.md)