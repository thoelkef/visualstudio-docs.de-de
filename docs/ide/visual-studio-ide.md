---
title: Übersicht über Visual Studio 2017
ms.date: 06/01/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
f1_keywords:
- vs.startpage
- VS.StartPage.HowDoI
- MSDNSTART
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 38491757da5010d015553f1d3c562e27914b28a9
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39078978"
---
# <a name="visual-studio-overview"></a>Übersicht über Visual Studio

Die *interaktive Entwicklungsumgebung* für Visual Studio ist eine kreative Startplattform, die Sie verwenden können, um Code zu bearbeiten, zu debuggen und zu kompilieren und anschließend eine App zu veröffentlichen. Bei einer interaktiven Entwicklungsumgebung (IDE) handelt es sich um ein funktionsreiches Programm, das für viele Aspekte der Softwareentwicklung verwendet werden kann. Neben dem üblichen Editor und Debugger, den die meisten IDEs bereitstellen, enthält Visual Studio Compiler, Codevervollständigungstools, grafische Designer und viele andere Features zur Erleichterung der Softwareentwicklung.

Visual Studio ist für Windows und Mac verfügbar. [Visual Studio für Mac](/visualstudio/mac/) enthält viele der Features von Visual Studio 2017 und wurde für die Entwicklung plattformübergeifender und mobiler Apps optimiert.

Der Fokus dieses Artikels liegt auf Visual Studio 2017 für Windows. Die grundlegenden Features der IDE werden vorgestellt. Es werden einige Aktionen erläutert, die Sie mit Visual Studio durchführen können, unter anderem das Erstellen eines einfachen Projekts, die Verwendung von [IntelliSense](using-intellisense.md) als Hilfsmittel beim Programmieren und das Debuggen einer App, um den Wert einer Variablen während der Ausführung des Programms zu sehen. Darüber hinaus werden die verschiedenen Toolfenster vorgestellt.

## <a name="install-the-visual-studio-ide"></a>Installieren von Visual Studio-IDE

Laden Sie zunächst [Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) herunter, und installieren Sie es auf Ihrem System.

Mit dem modularen Installationsprogramm können Sie *Workloads* auswählen und installieren, die Gruppen von Funktionen sind, die für die bevorzugte Programmiersprache oder Plattform erforderlich sind. Damit Sie die Schritte zum [Erstellen eines Programms](#create-a-program) ausführen können, müssen Sie während der Installation die Workload **Plattformübergreifende .NET Core-Entwicklung** auswählen.

![Workload für die plattformübergreifende .NET Core-Entwicklung im Visual Studio-Installer](../ide/media/dotnet-core-cross-platform-workload.png)

Wenn Sie Visual Studio zum ersten Mal starten, können Sie sich optional mit Ihrem Microsoft-Konto oder Ihrem Arbeits- oder Schulkonto [anmelden](signing-in-to-visual-studio.md).

## <a name="tour-of-the-ide"></a>Einführung in die IDE

Damit Sie eine visuelle Übersicht von Visual Studio bekommen, zeigt die folgende Abbildung Visual Studio mit einem geöffneten Projekt und mehreren wichtigen Toolfenstern, die Sie höchstwahrscheinlich verwenden werden.

![Die Visual Studio-IDE](../ide/media/visualstudioide.png)

- Im [**Projektmappen-Explorer**](../ide/solutions-and-projects-in-visual-studio.md) (oben rechts) können Sie Ihre Codedateien anzeigen, in ihnen navigieren und sie verwalten. Der **Projektmappen-Explorer** kann Sie beim Ordnen Ihres Codes unterstützen, indem er die Dateien in [Projektmappen und Projekte](quickstart-projects-solutions.md) gruppiert.

- Im [Editorfenster](../ide/writing-code-in-the-code-and-text-editor.md) (Mitte), in dem Sie die meiste Zeit verbringen werden, werden Dateiinhalte angezeigt. Hier können Sie Code bearbeiten oder eine Benutzeroberfläche wie etwa ein Fenster mit Schaltflächen und Textfeldern entwerfen.

- Das Fenster [Ausgabe](../ide/reference/output-window.md) (Mitte unten) ist der Ort, an den Visual Studio Benachrichtigungen sendet, z.B. Debug- und Fehlermeldungen, Compilerwarnungen, Nachrichten zum Veröffentlichungsstatus und mehr. Jede Nachrichtenquelle verfügt über eine eigene Registerkarte.

- Im [Team Explorer](/vsts/user-guide/work-team-explorer) (unten rechts) können Sie Arbeitselemente nachverfolgen und Code mithilfe von Techniken zur Versionskontrolle, wie etwa [Git](https://git-scm.com/) und [Team Foundation-Versionskontrolle (Team Foundation Version Control, TFVC)](/vsts/tfvc/overview), mit anderen teilen.

### <a name="popular-productivity-features"></a>Gängige Features zur Steigerung der Produktivität

Einige gängige Features in Visual Studio, mit denen Sie bei der Entwicklung von Software noch produktiver sind:

- [Refactoring](../ide/refactoring-in-visual-studio.md)

   Refactoring umfasst Vorgänge wie das intelligente Umbenennen von Variablen, das Extrahieren von Codezeilen in eine neue Methode, das Ändern der Reihenfolge von Methodenparametern und vieles mehr.

   ![Refactoring in Visual Studio](../ide/media/refactoring-menu.png)

- [IntelliSense](../ide/using-intellisense.md)

   IntelliSense ist der Begriff für eine Gruppe von Features, mit denen Informationen zum Code direkt im Editor angezeigt und in einigen Fällen kleine Codeabschnitte für Sie geschrieben werden. Damit verfügen Sie über eine grundlegende Dokumentation, die in den Editor integriert ist, sodass Sie die Typinformationen nicht mehr an anderer Stelle nachsehen müssen. Die Features von IntelliSense variieren je nach Sprache. Weitere Informationen finden Sie unter [C#-IntelliSense](../ide/visual-csharp-intellisense.md), [Visual C++ IntelliSense](../ide/visual-cpp-intellisense.md), [JavaScript IntelliSense](../ide/javascript-intellisense.md) und [Visual Basic IntelliSense](../ide/visual-basic-specific-intellisense.md). In der folgenden Abbildung ist dargestellt, wie mit IntelliSense eine Memberliste für einen Typ angezeigt wird:

   ![Visual Studio, Member-Liste](../ide/media/intellisense-list-members.png)

- [Schnellstart](../ide/reference/quick-launch-environment-options-dialog-box.md)

   Visual Studio kann angesichts der zahlreichen Menüs, Optionen und Eigenschaften zuweilen übermächtig wirken. Mit dem Suchfeld **Schnellstart** finden Sie in Visual Studio schnell, was Sie suchen. Wenn Sie beginnen, den Namen dessen einzugeben, wonach Sie suchen, listet Visual Studio Ergebnisse auf, mit denen Sie ans gewünschte Ziel gelangen. Wenn Sie Visual Studio Funktionalitäten wie etwa die Unterstützung für eine zusätzliche Programmiersprache hinzufügen müssen, liefert **Schnellstart** Ergebnisse, mit denen Sie Visual Studio-Installer zum Installieren einer Workload oder einer einzelnen Komponente öffnen können.

   ![Suchfeld „Schnellstart“ in Visual Studio](../ide/media/quick-launch-nuget.png)

- Wellenlinien und [schnelle Aktionen](../ide/quick-actions.md)

   Wellenlinien sind wellenförmige Unterstreichungen, die Sie auf Fehler oder mögliche Probleme in Ihrem Code hinweisen. Dank dieser visuellen Hinweisen können Sie Probleme sofort beheben, ohne zu warten, bis der Fehler beim Kompilieren oder beim Ausführen des Programms entdeckt wird. Wenn Sie auf eine Wellenlinie zeigen, werden zusätzliche Informationen zum Fehler angezeigt. Am linken Rand wird ggf. auch eine Glühbirne mit Aktionen, schnelle Aktionen genannt, zum Beheben des Fehlers angezeigt.

   ![Wellenlinien in Visual Studio](../ide/media/squiggles-error.png)

- [Aufrufhierarchie](../ide/reference/call-hierarchy.md)

   Im Fenster **Aufrufhierarchie** werden die Methoden angezeigt, mit denen eine ausgewählte Methode aufgerufen wird. Diese Informationen können nützlich sein, wenn Sie die Methode ändern oder entfernen oder einen Fehler aufspüren möchten.

   ![Fenster „Aufrufhierarchie“](../ide/reference/media/call-hierarchy-csharp-expanded.png)

- [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md)

   Mit CodeLens können Sie nach Verweisen auf Ihren Code, Änderungen an Ihrem Code, verknüpften Fehlern, Arbeitsaufgaben, Codeüberprüfungen und Komponententests suchen, ohne den Editor verlassen zu müssen.

   ![CodeLens](../ide/media/codelensoverview.png)

- [Gehe zu Definition](../ide/go-to-and-peek-definition.md)

  Mit der Funktion „Gehe zu Definition“ gelangen Sie direkt zu der Stelle, an der eine Funktion oder ein Typ definiert ist.

   ![Zur Definition wechseln](../ide/media/go-to-definition-menu.png)

- [Definitionsvorschau](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

   Im Fenster **Definitionsvorschau** wird die Definition einer Methode oder eines Typs angezeigt, ohne eine separate Datei zu öffnen.

   ![Definitionsvorschau](../ide/media/peek-definition.png)

## <a name="create-a-program"></a>Erstellen eines Programms

Darum werden wir mit Ihnen jetzt ein neues, einfaches Programm erstellen.

1. Öffnen Sie Visual Studio. Klicken Sie im Menü auf **Datei** > **Neu** > **Projekt**.

   ![„Datei“ > „Neu“ > „Projekt“ in der Menüleiste](../ide/media/file-new-project-menu.png)

1. Im Dialogfeld **Neues Projekt** werden mehrere *Projektvorlagen* angezeigt. Eine Vorlage enthält die grundlegenden Dateien und Einstellungen, die für einen bestimmten Projekttyp erforderlich sind. Wählen Sie unterhalb von **Visual C#**die Kategorie**.NET Core** aus, und wählen Sie dann die Vorlage **Konsolen-App (.NET Core)**. Geben Sie **HelloWorld** im Textfeld **Name** ein, und klicken Sie auf **OK**.

   ![.NET Core-App-Vorlage](../ide/media/overview-new-project-dialog.png)

   Visual Studio erstellt daraufhin das Projekt. Die Vorlage erstellt eine einfache „Hello World“-Anwendung, mit der die <xref:System.Console.WriteLine?displayProperty=nameWithType>-Methode aufgerufen wird, um die Literalzeichenfolge „Hello World!“ im Konsolenfenster (Programmausgabe).

  > [!NOTE]
  > Wenn die Kategorie **.NET Core** nicht angezeigt wird, müssen Sie die Workload **Plattformübergreifende .NET Core-Entwicklung** installieren. Klicken Sie hierfür im Dialogfeld **Neues Projekt** unten links auf den Link **Visual Studio-Installer öffnen**. Nachdem der Visual Studio-Installer geöffnet wurde, wählen Sie die Workload **Plattformübergreifende .NET Core-Entwicklung** aus, und klicken Sie dann auf **Ändern**.

   Kurz darauf sollte nun etwa Folgendes angezeigt werden:

   ![Visual Studio-IDE](../ide/media/overview-ide-console-app.png)

   Der C#-Code für Ihre Anwendung wird im Editor-Fenster angezeigt, der den meisten Raum einnimmt. Beachten Sie, dass der Text automatisch farbig hervorgehoben wird, um verschiedene Bestandteile des Codes anzuzeigen, z.B. Schlüsselwörter und Typen. Darüber hinaus zeigen kleine, vertikale gestrichelte Linien im Code an, welche geschweiften Klammern zusammengehören, und anhand der Zeilennummern können Sie sich später im Code orientieren. Sie können die kleinen Minuszeichen in Kästchen auswählen, um Codeblöcke ein- oder auszublenden. Mit dieser Codegliederungsfunktion können Sie Code ausblenden, den Sie nicht benötigen, um die Übersichtlichkeit des Bildschirms zu optimieren. Auf der rechten Seite werden im Fenster **Projektmappen-Explorer** die Projektdateien aufgelistet.

  ![Visual Studio-IDE mit roten Markierungen](../ide/media/overview-ide-console-app-red-boxes.png)

  Es sind noch mehr Menüs und Toolfenster verfügbar, aber für den Moment wenden wir uns Anderem zu.

1. Starten Sie nun die App. Wählen Sie hierzu auf der Menüleiste im Menü **Debuggen** die Option **Ohne Debuggen starten** aus. Alternativ können Sie auch die Tastenkombination **STRG**+**F5** drücken.

  ![Menü „Debuggen“ > „Ohne Debuggen starten“](../ide/media/overview-start-without-debugging.png)

  Visual Studio erstellt die App, und es wird ein Konsolenfenster mit der Meldung **Hello World!** geöffnet. Sie haben nun eine funktionierende App!

  ![Konsolenfenster](../ide/media/overview-console-window.png)

1. Drücken Sie eine beliebige Taste auf der Tastatur, um das Konsolenfenster zu schließen.

1. Fügen wir der App weiteren Code hinzu. Fügen Sie vor der Zeile `Console.WriteLine("Hello World!");` den folgenden Code ein:

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   Der Code zeigt **What is your name?** (Wie heißen Sie?) im Konsolenfenster an und wartet, bis der Benutzer Text eingegeben und die **EINGABETASTE** gedrückt hat.

1. Ändern Sie die Zeile `Console.WriteLine("Hello World!");` in den folgenden Code:

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

1. Führen Sie die App erneut aus, indem Sie **Debuggen** > **Ohne Debuggen starten** auswählen oder **STRG**+**F5** drücken.

   Visual Studio erstellt die App neu, und Sie werden im nun geöffneten Konsolenfenster zur Eingabe Ihres Namens aufgefordert.

1. Geben Sie Ihren Namen im Konsolenfenster ein, und drücken Sie die **EINGABETASTE**.

   ![Konsolenfenstereingabe](media/overview-console-input.png)

1. Drücken Sie eine beliebige Taste, um das Konsolenfenster zu schließen und das ausgeführte Programm zu beenden.

## <a name="use-refactoring-and-intellisense"></a>Verwenden von Refactoring und IntelliSense

Im Folgenden werden einige Methoden erläutert, wie Sie mit [Refactoring](refactoring-in-visual-studio.md) und [IntelliSense](using-intellisense.md) effizienter programmieren können.

Benennen Sie zunächst die Variable `name` um:

1. Doppelklicken Sie auf die Variable `name`, um sie auszuwählen.

1. Geben Sie den neuen Namen (**username**) der Variable ein.

   Achten Sie auf das graue Feld, das die Variable umgibt und auf die Glühbirne, die am Rand angezeigt wird.

1. Klicken Sie auf das Glühbirnensymbol, um die verfügbaren [Schnellaktionen](quick-actions.md) anzuzeigen. Klicken Sie auf **'name' in 'username' umbenennen**.

   ![Umbenennen einer Aktion in Visual Studio](media/rename-quick-action.png)

   Die Variable wird für im gesamten Projekt umbenannt, in diesem Fall betrifft dies nur zwei Stellen.

   ![Animiertes GIF, das das Refactoring „Umbenennen“ in Visual Studio anzeigt](media/rename-refactoring.gif)

1. Im Folgenden wird IntelliSense näher erläutert. Geben Sie **DateTime now = DateTime.** unterhalb der Zeile `Console.WriteLine($"\nHello {username}!");` ein.

   Ein Feld zeigt die Members der Klasse <xref:System.DateTime> an. Darüber hinaus wird die Beschreibung des aktuell ausgewählten Members in einem separaten Feld angezeigt.

   ![Auflistung von Members durch IntelliSense in Visual Studio](media/intellisense-list-members.png)

1. Wählen Sie den Member **Now** aus, bei dem es sich um eine Eigenschaft der Klasse handelt, indem Sie auf diesen doppelklicken oder die **TAB-Taste** drücken. Vervollständigen Sie die Codezeile, indem Sie ein Semikolon (**;**) hinzufügen.

1. Geben Sie darunter folgende Codezeilen ein, oder kopieren Sie diese:

   ```csharp
   int dayOfYear = now.DayOfYear;

   Console.Write("Day of year: ");
   Console.WriteLine(dayOfYear);
   ```

   > [!TIP]
   > <xref:System.Console.Write%2A?displayProperty=nameWithType> ist ein wenig anders als <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, denn es fügt nach dem Einfügen kein Zeilenabschlusszeichen hinzu. Das bedeutet, dass der nächste Textabschnitt, der an die Ausgabe gesendet wird, in der gleichen Zeile ausgegeben wird. Sie können auf jede dieser Methoden in Ihrem Code zeigen, um deren Beschreibung anzuzeigen.

1. Anschließend wird erneut ein Refactoring durchgeführt, um den Code etwas präziser zu gestalten. Klicken Sie in der Zeile `DateTime now = DateTime.Now;` auf die Variable `now`.

   Beachten Sie, dass ein kleines Schraubendrehersymbol am Rand dieser Zeile angezeigt wird.

1. Klicken Sie auf das Schraubendrehersymbol, um zu sehen, welche Vorschläge Visual Studio macht. In diesem Fall zeigt es das Refactoring [Inline temporär variabel](reference/inline-temporary-variable.md) an, um eine Codezeile zu entfernen, ohne das gesamte Verhalten zu ändern:

   ![Refactoring „Inline temporär variabel“ in Visual Studio](media/inline-temporary-variable-refactoring.png)

1. Klicken Sie auf **Inline temporär variabel**, um den Code umzugestalten.

1. Führen Sie das Programm erneut aus, indem Sie **STRG**+**F5** drücken. Die Ausgabe sieht in etwa folgendermaßen aus:

   ![Konsolenfenster mit Programmausgabe](../ide/media/overview-console-final.png)

## <a name="debug-code"></a>Debuggen von Code

Wenn Sie Code schreiben, müssen Sie ihn auszuführen und auf Fehler prüfen. Mit dem Debugsystem von Visual Studio können Sie Ihren Code Anweisung für Anweisung durchlaufen und dabei die Variablen untersuchen. Sie können *Breakpoints* festlegen, mit denen die Codeausführung an einer bestimmten Zeile beendet wird. Sie können sehen, wie sich der Wert einer Variablen bei der Codeausführung ändert, und vieles mehr.

Legen Sie einen Breakpoint fest, um den Wert der Variable `username` zu sehen, während das Programm ausgeführt wird.

1. Suchen Sie die Codezeile `Console.WriteLine($"\nHello {username}!");`. Wenn Sie einen Breakpoint für diese Codezeile festlegen, damit die Ausführung des Programms an dieser Zeile angehalten wird, klicken Sie auf den äußeren linken Rand des Editors. Sie können auch an einer anderen Stelle der Codezeile klicken und dann **F9** drücken.

   Ein roter Kreis wird am äußeren linken Rand angezeigt, und der Code wird rot hervorgehoben.

   ![Breakpoint an einer Codezeile in Visual Studio](media/breakpoint.png)

1. Starten Sie das Debuggen, indem Sie auf **Debuggen** > **Debuggen starten** klicken oder **F5** drücken.

1. Wenn das Konsolenfenster angezeigt wird und Sie nach Ihrem Namen fragt, geben Sie diesen ein, und drücken Sie die **EINGABETASTE**.

   Beachten Sie, dass der Fokus zum Code-Editor von Visual Studio zurückkehrt und die Codezeile mit dem Breakpoint gelb hervorgehoben wird. Das bedeutet, dass dies die nächste Codezeile ist, die vom Programm ausgeführt wird.

1. Zeigen Sie mit der Maus auf die Variable `username`, um deren Wert anzuzeigen. Alternativ können Sie mit der rechten Maustaste auf `username` klicken und **Überwachung hinzufügen** auswählen, um die Variable zum **Überwachungsfenster** hinzuzufügen. Dort wird deren Wert ebenfalls angezeigt.

   ![Variablenwert während des Debuggens in Visual Studio](media/debugging-variable-value.png)

1. Drücken Sie erneut **F5**, damit das Programm bis zum Abschluss ausgeführt wird.

Weitere Informationen über den Debugprozess in Visual Studio finden Sie unter [Tour zu den Debuggerfeatures](../debugger/debugger-feature-tour.md).

## <a name="customize-visual-studio"></a>Anpassen von Visual Studio

Sie können die Benutzeroberfläche von Visual Studio personalisieren und beispielsweise das Standardfarbdesign ändern. So ändern Sie das Design in **Dunkel**:

1. Klicken Sie auf der Menüleiste auf **Extras** > **Optionen**, um das Dialogfeld **Optionen** zu öffnen.

1. Ändern Sie auf der Optionsseite **Umgebung** > **Allgemein** die Auswahl für **Farbdesign** in **Dunkel**, und klicken Sie dann auf **OK**.

   Das Farbdesign wird für die gesamte IDE in **Dunkel** geändert.

   ![Visual Studio in einem Design „Dunkel“](media/quickstart-personalize-dark-theme.png)

Weitere Informationen dazu, wie Sie die IDE personalisieren können, finden Sie unter [Personalisieren der Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="learn-more"></a>Weitere Informationen

Möchten Sie eine App für ein Android- oder ein iOS-Telefon erstellen? Möchten Sie lieber ein 3D-Spiel oder eine cloudfähige App erstellen? Weitere Informationen zu diesen und anderen Features von Visual Studio finden Sie unter [Features of Visual Studio 2017 (Features von Visual Studio 2017)](../ide/advanced-feature-overview.md).

Wenn Sie nun mit dem Programmieren beginnen möchten, wählen Sie eines der Schnellstartthemen aus dem Inhaltsverzeichnis aus, z.B. [Schnellstart: Verwenden von Visual Studio zum Erstellen Ihrer ersten ASP.NET Core-Web-App](quickstart-aspnet-core.md).

Sie können ebenfalls die kostenlosen Visual Studio-Kurse nutzen, die unter [Microsoft Virtual Academy](https://mva.microsoft.com/product-training/visual-studio-courses#!index=2&lang=1033) verfügbar sind.

## <a name="see-also"></a>Siehe auch

* [More Visual Studio features (Features von Visual Studio 2017)](../ide/advanced-feature-overview.md)
* [visualstudio.microsoft.com](https://visualstudio.microsoft.com/vs/)
* [Der Visual Studio-Blog](https://blogs.msdn.microsoft.com/visualstudio/)
* [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)