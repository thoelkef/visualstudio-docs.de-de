---
redirect_url: /visualstudio/ide/visual-studio-ide
ms.openlocfilehash: 5f1fa39d6e6cde1664a8aaa34aed7cba726b1d56
ms.sourcegitcommit: 64c7682ec3a2cbea684e716803398d4278b591d1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2017
---
# <a name="get-started-with-visual-studio"></a>Erste Schritte mit Visual Studio
Visual Studio ist ein leistungsstarkes Tool zum Entwickeln von Apps. Wenn Sie es noch nicht getan haben, sollten Sie gleich loslegen und [Visual Studio](https://www.visualstudio.com/vs/) herunterladen und installieren. Weitere Informationen zum Herunterladen von Visual Studio und zum Vornehmen der gewünschten Konfigurationen finden Sie im Video [Getting Started with Visual Studio – Setting up your IDE](https://www.youtube.com/watch?v=xLCedknQkN0&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=1) (Erste Schritte mit Visual Studio: Einrichten der IDE).

## <a name="visual-studio-tour"></a>Visual Studio-Tour
Visual Studio weist eine Reihe von Toolfenstern, Menüs und Symbolleisten auf, die zusammen als integrierte Entwicklungsumgebung, kurz IDE, bezeichnet werden. Die Visual Studio-IDE hilft Ihnen beim Verwirklichen Ihrer Entwicklungsaufgaben. Hier finden Sie eine Kurzübersicht der IDE-Elemente, die Sie vermutlich besonders häufig verwenden werden.

### <a name="code-editor"></a>Code-Editor
Eins der besonders intensiv verwendeten Toolfenster in Visual Studio – dies ist der Ort, an dem Sie Ihren Code erstellen, anzeigen und in ihm navigieren.

![Code-Editor](../ide/media/VSIDE_CodeWindow.png)

Wenn Sie Code eingeben, hilft Ihnen der Code-Editor mithilfe von Features wie Anweisungsvervollständigung, farbiger Syntaxhervorhebung, Zuordnungsmodus und mehr, Ihren Code schneller und einfacher zu erstellen und zu finden. Weitere Informationen finden Sie im Video [Getting Started with Visual Studio - Editing and navigating your code](https://www.youtube.com/watch?v=4glwwioCVjA&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=5) (Erste Schritte mit Visual Studio: Bearbeiten von und Navigieren in Code)

Einige Projektmappentypen enthalten möglicherweise als *Formulare* bezeichnete Fenster, z.B. Formulare für Windows Presentation Foundation (WPF), Windows-Formulare, Formulare für Extensible Application Markup Language (XAML) und andere. In diesen Fällen finden Sie in diesem Bereich auch einen visuellen Designer, in dem Sie Steuerelemente wie Schaltflächen und Listenfelder auf das Formular, mit dem Benutzer bei der Ausführung Ihrer App interagieren können, ziehen und dort ablegen können.

### <a name="solution-explorer"></a>Projektmappen-Explorer
Ein Toolfenster mit dem Namen **Projektmappen-Explorer** listet Ihre sämtlichen Codedateien auf. Der Projektmappen-Explorer kann Sie beim Ordnen Ihres Codes unterstützen, indem er dessen Dateien in Projektmappen und Projekte gruppiert. Das fett formatierte Projekt wird als *Startprojekt* bezeichnet. Das ist der erste Code, der beim Starten Ihrer Projektmappe ausgeführt wird. Sie können das Startprojekt ändern. Weitere Informationen finden Sie im Video [Getting Started with Visual Studio – Building blocks of the IDE](https://www.youtube.com/watch?v=JHc3_gsCmZg&index=2&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK) (Erste Schritte mit Visual Studio: Bausteine der IDE)

![Zugeklappte Knoten im Projektmappen-Explorer](../ide/media/VSIDE_SolutionExplorer2_callouts.png)

 Über Projektmappen und Projekte hinaus sind im Projektmappen-Explorer alle Dateien in den einzelnen Projekten aufgelistet, wenn Sie den Knoten des jeweiligen Projekts aufklappen. Jedes Projekt enthält mindestens eine Datei, meistens aber mehrere, wie etwa Quellcodedateien und Ressourcendateien, so etwa Bilder und Bibliotheken.

![Projektmappen-Explorer](../ide/media/VSIDE_SolutionExplorer3.png)

Um Eigenschaften für Projektmappen, Projekte und Dateien anzuzeigen, wählen Sie im Kontextmenü (das Sie über die rechte Maustaste erreichen) den Befehl **Eigenschaften** aus, oder wählen Sie im Menü **Ansicht > Eigenschaftenfenster** aus.

![Eigenschaftenfenster](../ide/media/VSIDE_SolutionExplorer4.png)

Sie brauchen aber keine Projektmappe und kein Projekt zu erstellen, um mit der Codeerstellung zu beginnen. Sie können einfach direkt einsteigen und Codedateien in Visual Studio öffnen, z. B. aus einem Git-Repository geklonte Dateien, und direkt mit der Bearbeitung beginnen. Die Dateien werden im Projektmappen-Explorer angezeigt und erhalten farbige Syntaxhervorhebung, einfache Anweisungsvervollständigung und mehr, ganz wie herkömmliche Projektmappen. Weitere Informationen finden Sie unter [Entwickeln von Code in Visual Studio ohne Projekte oder Projektmappen](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

### <a name="toolbar-and-menus"></a>Symbolleisten und Menüs
Um Ihr Projekt auszuführen, neue Projektmappen zu erstellen, Dateien zu speichern und mehr, verwenden Sie die Symbolleiste und die Menübefehle von Visual Studio. Sobald Ihr Code beispielsweise zur Ausführung zum Debuggen bereit ist, können Sie die Schaltfläche **Start** auf der Symbolleiste oder im Menü **Debuggen > Debuggen starten** auswählen. Um eine neue Projektmappe zu erstellen, wählen Sie die Schaltfläche **Neues Projekt** oder im Menü **Datei > Neues Projekt** usw. aus.

![Visual Studio-Symbolleiste](../ide/media/VSIDE_SolutionExplorer5_callouts.png)

Beachten Sie, dass sich die Symbole der Symbolleiste und die in Menüs verfügbaren Befehle abhängig vom Kontext – das ist das aktuell ausgewählte Element – ändern können. Fast alle Befehle können sowohl über Tastenkombinationen als auch per Maus aufgerufen werden.

### <a name="team-explorer"></a>Team Explorer
**Team Explorer** ermöglicht Ihnen das Herstellen von Verbindungen mit Tools zur Quellcodeverwaltung, wie etwa [Git](https://git-scm.com/) und [Team Foundation-Versionskontrolle (Team Foundation Version Control, TFVC)](https://www.visualstudio.com/en-us/docs/tfvc/overview), um Ihren Code lokal zu speichern oder ihn mit anderen in einem gehosteten Dienst zu teilen. Sie können diese Tools auch zum Nachverfolgen von Aufgaben und mehr verwenden.

Weitere Informationen finden Sie in den Videos [Getting Started with Visual Studio – Building blocks of the IDE](https://www.youtube.com/watch?v=JHc3_gsCmZg&index=2&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK) (Erste Schritte mit Visual Studio: Bausteine der IDE) und [Getting Started with Visual Studio – Opening a project from Source Control](https://www.youtube.com/watch?v=pc9vX_4RGV4&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=3) (Erste Schritte mit Visual Studio: Öffnen eines Projekts aus der Quellcodeverwaltung).

![Team Explorer](../ide/media/TeamExplorer.png)

### <a name="output-window"></a>Ausgabefenster
Das Fenster **Ausgabe** ist der Ort, an den Visual Studio Benachrichtigungen sendet, z. B. Debug- und Fehlermeldungen, Compilerwarnungen, Nachrichten zum Veröffentlichungsstatus und mehr. Jeder Nachrichtentyp verfügt über eine eigene Registerkarte.

![Ausgabefenster](../ide/media/VSIDE_OutputWindow.png)

Weitere Informationen zum Verwenden des Ausgabefensters beim Debuggen finden Sie unter [The Output window while debugging with Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2015/02/09/the-output-window-while-debugging-with-visual-studio/) (Das Ausgabefenster beim Debuggen mit Visual Studio).

## <a name="first-steps"></a>Erste Schritte
- **Verschaffen Sie sich einen Überblick**: Wenn Sie einen Überblick über viele der wichtigsten Features in Visual Studio wünschen, schauen Sie sich um! Siehe [Visual Studio-IDE](../ide/visual-studio-ide.md).
- **Setup**: Informationen zum Herunterladen und Installieren von Visual Studio finden Sie unter [Installieren von Visual Studio 2017 RC](../install/install-visual-studio.md).
- **Die Grundlagen**: Weitere Informationen über die Funktionsweise von Visual Studio finden Sie unter [Get Started Developing with Visual Studio](../ide/get-started-developing-with-visual-studio.md) (Einstieg in das Entwickeln mit Visual Studio).
- **Einstellungen**: Hier erfahren Sie, wie Sie Visual Studio Ihrer Arbeitsweise anpassen können. Weitere Informationen finden Sie unter [Personalisieren der Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).
- **Tutorials**: Mehr über das Entwickeln von Code in Visual Studio erfahren Sie, wenn Sie ein Tutorial absolvieren, z. B. [Erste Schritte mit Visual C# und Visual Basic](../ide/getting-started-with-visual-csharp-and-visual-basic.md) oder [Erste Schritte mit C++ in Visual Studio](../ide/getting-started-with-cpp-in-visual-studio.md).
- **Videos**: Mehr Informationen über weitere Features und Aspekte von Visual Studio finden Sie in den Videos im [Microsoft Visual Studio-Kanal](https://www.youtube.com/user/VisualStudio/videos) auf YouTube, den Visual Studio-Videos auf [Channel 9](https://channel9.msdn.com/Tags/visual+studio) oder in der [Microsoft Virtual Academy](https://mva.microsoft.com/product-training/visual-studio-courses#!jobf=Developer).

## <a name="access-cloud-based-resources"></a>Zugriff auf cloudbasierte Ressourcen
Wenn Sie cloudbasierte Ressourcen in Ihrer App oder Ihrem Spiel verwenden möchten, können Sie dies durch die Aufnahme von [Azure-Diensten](https://azure.microsoft.com/en-us/services/) erreichen. Sie können das Azure SDK für .NET nutzen, indem Sie mithilfe des neuen Visual Studio-Installationsprogramms die Arbeitsauslastung für **Azure-Entwicklung** installieren. Die Pakete, die installiert werden, befinden sich auf der gleichen Funktionsebene wie die 2.9.5-Version des SDKs. Bei dieser und allen zukünftigen Versionen von Visual Studio ist das Azure SDK für .NET nur vom Visual Studio-Installer aus verfügbar.

Nach dem Installieren der Arbeitsauslastung für Azure-Entwicklung ist in Visual Studio ein neues Toolfenster mit dem Namen **Cloud-Explorer** verfügbar. Mit Cloud-Explorer können Sie Ihre Azure-Objekte und Ressourcen aus Visual Studio heraus durchsuchen und verwalten. Wenn für einen bestimmten Vorgang das Azure-Portal erforderlich ist, stellt Cloud-Explorer Verknüpfungen bereit, mit denen Sie an den richtigen Ort im Azure-Portal gelangen.

![Cloud-Explorer](../ide/media/VSIDE_CloudExplorer.png)

Weitere Informationen zur Verwendung von Cloud-Explorer finden Sie unter [Verwalten von Azure-Ressourcen mit dem Cloud-Explorer](https://azure.microsoft.com/en-us/documentation/articles/vs-azure-tools-resources-managing-with-cloud-explorer/).
Durch das Installieren der Arbeitsauslastung für Azure-Entwicklung erhalten Sie außerdem Zugriff auf die [Visual Studio Tools für Azure](https://www.visualstudio.com/vs/azure-tools/) sowie auf weitere zugehörige Tools.

## <a name="tips-and-tricks"></a>Tipps und Tricks
Abkürzungen und praktische Tipps und Tricks, mit denen Sie Visual Studio besser nutzen können, finden Sie in den folgenden Themen.
- [Getting Started with Visual Studio - Tips & Tricks](https://www.youtube.com/watch?v=vmXqGwn1Glk&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=4) (Erste Schritte mit Visual Studio: Tipps und Tricks)
- [Produktivitätstipps für Visual Studio](../ide/productivity-tips-for-visual-studio.md)
- [Visual Studio Tips and Tricks](https://channel9.msdn.com/events/TechEd/2013/DEV-B353) (Tipps und Tricks für Visual Studio)
- [C++ Debugging Tips and Tricks](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/C-Plus-Plus-Debugging-Tips-and-Tricks) (Tipps und Tricks zum Debuggen in C++)
- [Äußerst nützliche (und viel zu wenig genutzte) Tipps zu Visual Studio [Blog von Scott Hanselman]](https://www.hanselman.com/blog/VisualStudiosMostUsefulAndUnderusedTips.aspx)
- [Getting Started with Visual Studio - Installing Visual Studio extensions](https://www.youtube.com/watch?v=MWLLQaknRZY&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=7) (Erste Schritte mit Visual Studio: Installieren von Visual Studio Extensions)
