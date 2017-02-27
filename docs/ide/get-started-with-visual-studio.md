---
title: Erste Schritte mit Visual Studio | Microsoft-Dokumentation
description: Lernen Sie die Grundlagen zum Einstieg in Visual Studio kennen
ms.custom: 
ms.date: 12/05/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, getting started
ms.assetid: 38e90339-1da5-410c-8ba4-437fc556cba7
caps.latest.revision: 65
author: kempb
ms.author: kempb
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
translationtype: Human Translation
ms.sourcegitcommit: 27493b53229d9ceb6bc215fcf3d57a60fe4358b0
ms.openlocfilehash: 452f8dbd2c7eb4bcc2f0310da1f04c6dd031f629

---
# <a name="get-started-with-visual-studio"></a>Erste Schritte mit Visual Studio

Visual Studio ist ein leistungsstarkes Tool zum Entwickeln von Apps. Wenn Sie es noch nicht getan haben, sollten Sie gleich loslegen und [Visual Studio](https://aka.ms/vs/15/preview/vs_enterprise) herunterladen und installieren. Weitere Informationen zum Herunterladen von Visual Studio und zum Vornehmen der gewünschten Konfigurationen finden Sie im Video [Getting Started with Visual Studio – Setting up your IDE](https://www.youtube.com/watch?v=xLCedknQkN0&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=1) (Erste Schritte mit Visual Studio: Einrichten der IDE).

## <a name="visual-studio-tour"></a>Visual Studio-Tour
Visual Studio weist eine Reihe von Toolfenstern, Menüs und Symbolleisten auf, die zusammen als integrierte Entwicklungsumgebung, kurz IDE, bezeichnet werden. Die Visual Studio-IDE hilft Ihnen beim Verwirklichen Ihrer Entwicklungsaufgaben. Hier finden Sie eine Kurzübersicht der IDE-Elemente, die Sie vermutlich besonders häufig verwenden werden.

### <a name="code-editor"></a>Code-Editor
Eins der besonders intensiv verwendeten Toolfenster in Visual Studio – dies ist der Ort, an dem Sie Ihren Code erstellen, anzeigen und in ihm navigieren.

![Code-Editor](../ide/media/VSIDE_CodeWindow.png)

Wenn Sie Code eingeben, hilft Ihnen der Code-Editor mithilfe von Features wie Anweisungsvervollständigung, farbiger Syntaxhervorhebung, Zuordnungsmodus und mehr, Ihren Code schneller und einfacher zu erstellen und zu finden. Weitere Informationen finden Sie im Video [Getting Started with Visual Studio - Editing and navigating your code](https://www.youtube.com/watch?v=4glwwioCVjA&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=5) (Erste Schritte mit Visual Studio: Bearbeiten von und Navigieren in Code)

Einige Typen von Projektmappen können Formulare enthalten, wie etwa WPF oder Windows Forms. In diesen Fällen finden Sie in diesem Bereich auch einen visuellen Designer, in dem Sie dem Formular visuell Steuerelemente hinzufügen können, wie etwa Schaltflächen und Listenfelder.

### <a name="solution-explorer"></a>Projektmappen-Explorer

Ein Toolfenster mit dem Namen **Projektmappen-Explorer** listet Ihre sämtlichen Codedateien auf. Der Projektmappen-Explorer kann Sie beim Ordnen Ihres Codes unterstützen, indem er dessen Dateien in Projektmappen und Projekte gruppiert. Das fett formatierte Projekt wird als Startprojekt bezeichnet. Das ist der erste Code, der beim Starten Ihrer Projektmappe ausgeführt wird. Sie können das Startprojekt ändern. Weitere Informationen finden Sie im Video [Getting Started with Visual Studio – Building blocks of the IDE](https://www.youtube.com/watch?v=JHc3_gsCmZg&index=2&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK) (Erste Schritte mit Visual Studio: Bausteine der IDE)

![Zugeklappte Knoten im Projektmappen-Explorer](../ide/media/VSIDE_SolutionExplorer2_callouts.png)

 Über Projektmappen und Projekte hinaus sind im Projektmappen-Explorer alle Dateien in den einzelnen Projekten aufgelistet, wenn Sie den Knoten des jeweiligen Projekts aufklappen. Jedes Projekt enthält mindestens eine Datei, meistens aber mehrere, wie etwa Quellcodedateien und Ressourcendateien, so etwa Bilder und Bibliotheken.

![Projektmappen-Explorer](../ide/media/VSIDE_SolutionExplorer3.png)

Um Eigenschaften für Projektmappen, Projekte und Dateien anzuzeigen, wählen Sie im Kontextmenü (das Sie über die rechte Maustaste erreichen) den Befehl **Eigenschaften** aus, oder wählen Sie im Menü **Ansicht > Eigenschaftenfenster** aus.

![Eigenschaftenfenster](../ide/media/VSIDE_SolutionExplorer4.png)

Sie brauchen aber keine Projektmappe und kein Projekt zu erstellen, um mit der Codeerstellung zu beginnen. Sie können einfach direkt einsteigen und Codedateien in Visual Studio öffnen, z. B. aus einem Git-Repository geklonte Dateien, und direkt mit der Bearbeitung beginnen. Die Dateien werden im Projektmappen-Explorer angezeigt und erhalten farbige Syntaxhervorhebung, einfache Anweisungsvervollständigung und mehr, ganz wie herkömmliche Projektmappen. Weitere Informationen finden Sie unter [Open Any Folder](https://blogs.msdn.microsoft.com/visualstudio/2016/04/12/open-any-folder-with-visual-studio-15-preview/) (Öffnen von beliebigen Ordnern).

### <a name="toolbar-and-menus"></a>Symbolleisten und Menüs
Um Ihr Projekt auszuführen, neue Projektmappen zu erstellen, Dateien zu speichern und mehr, verwenden Sie die Symbolleiste und die Menübefehle von Visual Studio. Sobald Ihr Code beispielsweise zur Ausführung zum Debuggen bereit ist, können Sie die Schaltfläche **Start** auf der Symbolleiste oder im Menü **Debuggen > Debuggen starten** auswählen. Um eine neue Projektmappe zu erstellen, wählen Sie die Schaltfläche **Neues Projekt** oder im Menü **Datei > Neues Projekt** usw. aus.

![Visual Studio-Symbolleiste](../ide/media/VSIDE_SolutionExplorer5_callouts.png)

Beachten Sie, dass sich die Symbole der Symbolleiste und die in Menüs verfügbaren Befehle abhängig vom Kontext – das ist das aktuell ausgewählte Element – ändern können.

### <a name="team-explorer"></a>Team Explorer
**Team Explorer** ermöglicht Ihnen das Herstellen von Verbindungen mit Tools zur Quellcodeverwaltung, wie etwa [Git](https://git-scm.com/) und [Team Foundation-Versionskontrolle (Team Foundation Version Control, TFVC)](https://www.visualstudio.com/en-us/docs/tfvc/overview), um Ihren Code lokal zu speichern oder ihn mit anderen in einem gehosteten Dienst zu teilen. Sie können diese Tools auch zum Nachverfolgen von Aufgaben und mehr verwenden.

Weitere Informationen finden Sie in den Videos [Getting Started with Visual Studio – Building blocks of the IDE](https://www.youtube.com/watch?v=JHc3_gsCmZg&index=2&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK) (Erste Schritte mit Visual Studio: Bausteine der IDE) und [Getting Started with Visual Studio – Opening a project from Source Control](https://www.youtube.com/watch?v=pc9vX_4RGV4&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=3) (Erste Schritte mit Visual Studio: Öffnen eines Projekts aus der Quellcodeverwaltung).

![Team Explorer](../ide/media/TeamExplorer.png)

### <a name="output-window"></a>Ausgabefenster
Das Fenster **Ausgabe** ist der Ort, an den Visual Studio Benachrichtigungen sendet, z. B. Debug- und Fehlermeldungen, Compilerwarnungen, Nachrichten zum Veröffentlichungsstatus und mehr. Jeder Nachrichtentyp verfügt über eine eigene Registerkarte.

![Ausgabefenster](../ide/media/VSIDE_OutputWindow.png)

Weitere Informationen zum Verwenden des Ausgabefensters beim Debuggen finden Sie unter [The Output window while debugging with Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2015/02/09/the-output-window-while-debugging-with-visual-studio/) (Das Ausgabefenster beim Debuggen mit Visual Studio).

## <a name="first-steps"></a>Erste Schritte
- **Setup**: Informationen zum Herunterladen und Ausführen des Setups von Visual Studio finden Sie unter [Setup & Installation](https://go.microsoft.com/fwlink/?linkid=833223) (Setup und Installation).
- **Die Grundlagen**: Weitere Informationen über die Funktionsweise von Visual Studio finden Sie unter [Get Started Developing with Visual Studio](../ide/get-started-developing-with-visual-studio.md) (Einstieg in das Entwickeln mit Visual Studio).
- **Einstellungen**: Passen Sie Visual Studio an Ihre Arbeitsweise an. Weitere Informationen finden Sie unter [Personalisieren der Visual Studio-IDE](https://msdn.microsoft.com/en-us/library/mt269425.aspx).
- **Tutorials**: Mehr über das Entwickeln von Code in Visual Studio erfahren Sie, wenn Sie ein Tutorial absolvieren, z. B. [Erste Schritte mit Visual C# und Visual Basic](https://msdn.microsoft.com/en-us/library/dd492171.aspx) oder [Erste Schritte mit C++ in Visual Studio](https://msdn.microsoft.com/en-us/library/jj620919.aspx).
- **Videos**: Mehr Informationen über weitere Features und Aspekte von Visual Studio finden Sie in den Videos im [Microsoft Visual Studio-Kanal](https://www.youtube.com/user/VisualStudio/videos) auf YouTube oder den Visual Studio-Videos auf [Channel 9](https://channel9.msdn.com/Tags/visual+studio).

## <a name="access-cloud-based-resources"></a>Zugriff auf cloudbasierte Ressourcen

Wenn Sie cloudbasierte Ressourcen in Ihrer App oder Ihrem Spiel verwenden möchten, können Sie dies durch die Aufnahme von [Azure-Diensten](https://azure.microsoft.com/en-us/services/) erreichen. Sie können das Azure SDK für .NET nutzen, indem Sie mithilfe des neuen Visual Studio-Installationsprogramms die Azure-Arbeitsauslastung installieren. Die Pakete, die installiert werden, befinden sich auf der gleichen Funktionsebene wie die 2.9.5-Version des SDKs. Bei dieser und allen zukünftigen Versionen von Visual Studio ist das Azure SDK für .NET nur vom Visual Studio-Installer aus verfügbar.

Nach dem Installieren von Azure SDK für .NET ist in Visual Studio ein neues Toolfenster mit dem Namen **Cloud-Explorer** verfügbar. Mit Cloud-Explorer können Sie Ihre Azure-Objekte und Ressourcen aus Visual Studio heraus durchsuchen und verwalten. Wenn für einen bestimmten Vorgang das Azure-Portal erforderlich ist, stellt Cloud-Explorer Verknüpfungen bereit, mit denen Sie an den richtigen Ort im Azure-Portal gelangen.

![Cloud-Explorer](../ide/media/VSIDE_CloudExplorer.png)

Weitere Informationen zur Verwendung von Cloud-Explorer finden Sie unter [Verwalten von Azure-Ressourcen mit dem Cloud-Explorer](https://azure.microsoft.com/en-us/documentation/articles/vs-azure-tools-resources-managing-with-cloud-explorer/).
Durch das Installieren des Azure SDKs erhalten Sie außerdem Zugriff auf die [Visual Studio Tools für Azure](https://www.visualstudio.com/vs/azure-tools/) sowie auf weitere Tools.

## <a name="tips-and-tricks"></a>Tipps und Tricks
Abkürzungen und praktische Tipps und Tricks, mit denen Sie Visual Studio besser nutzen können, finden Sie in den folgenden Themen.
- [Getting Started with Visual Studio - Tips & Tricks](https://www.youtube.com/watch?v=vmXqGwn1Glk&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=4) (Erste Schritte mit Visual Studio: Tipps und Tricks)
- [Produktivitätstipps für Visual Studio](https://msdn.microsoft.com/en-us/library/jj153218.aspx)
- [Visual Studio Tips and Tricks](https://channel9.msdn.com/events/TechEd/2013/DEV-B353) (Tipps und Tricks für Visual Studio)
- [C++ Debugging Tips and Tricks](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/C-Plus-Plus-Debugging-Tips-and-Tricks) (Tipps und Tricks zum Debuggen in C++)
- [Getting Started with Visual Studio - Installing Visual Studio extensions](https://www.youtube.com/watch?v=MWLLQaknRZY&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=7) (Erste Schritte mit Visual Studio: Installieren von Visual Studio Extensions)



<!--HONumber=Feb17_HO4-->


