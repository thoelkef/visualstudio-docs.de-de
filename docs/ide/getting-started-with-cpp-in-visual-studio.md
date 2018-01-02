---
title: Erste Schritte mit C++ in Visual Studio | Microsoft-Dokumentation
ms.custom: mvc
ms.date: 12/04/2017
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: 99c73344-86ba-4b08-9e15-f6111cc04185
author: corob-msft
ms.author: tglee
manager: ghogen
ms.openlocfilehash: c86e7bcfe43eeaa6554efeed6654f34e140d9ea7
ms.sourcegitcommit: ebe9fb5eda724936f7a059d35d987c29dffdb50d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2017
---
# <a name="get-started-with-c-in-visual-studio"></a>Erste Schritte mit C++ in Visual Studio

Arbeiten Sie sich durch diesen Schnellstart, um mit den vielen Tools und Dialogfeldern vertraut zu werden, die Sie beim Entwickeln von Anwendungen mit C++ in Visual Studio verwenden können. Erstellen Sie eine „Hallo Welt“-Anwendung, und lernen Sie mehr über das Arbeiten in der integrierten Entwicklungsumgebung (IDE).

## <a name="prerequisites"></a>Erforderliche Komponenten

Sie müssen sich nicht mit C++ auskennen, um diesen Schnellstart durchzuführen, aber Sie sollten grundlegende Programmier- und Debuggingkonzepte kennen. Die Visual Studio-Dokumentation bringt Ihnen nicht bei, wie man mit C++ programmiert. Nützliche Informationen über Lernressourcen zu C++ finden Sie unter [Get Started (Erste Schritte)](https://isocpp.org/get-started) auf der Website von ISO C++.

Um diesen Schritten folgen zu können, benötigen Sie Visual Studio 2017 Version 15.3 oder höher, und die Workload **Desktopentwicklung mit C++** muss installiert sein. Einen kurzen Leitfaden zur Installation finden Sie unter [Install C++ support in Visual Studio (Installieren von C++-Unterstützung in Visual Studio)](/cpp/build/vscpp-step-0-installation).

## <a name="create-a-console-app"></a>Erstellen einer Konsolenanwendung

Starten Sie Visual Studio, falls es noch nicht ausgeführt wird.

![IDE mit angewendeten Visual C++-Einstellungen](../ide/media/get-started-cpp-ide-layout.png "IDE with Visual C++ settings applied")

Wenn Sie Visual Studio geöffnet haben, können Sie die drei grundlegenden Teile der IDE sehen: Toolsfenster, Menüs und Symbolleisten und den Hauptfensterbereich. Toolfenster sind auf der linken und rechten Seite an das Fenster der Anwendung angedockt. Das Feld **Schnellstart**, die Menüleiste und die Standardsymbolleiste finden Sie oben. In der Mitte des Fensters befindet sich die **Startseite**. Wenn Sie eine Projektmappe oder ein Projekt öffnen, werden Editoren und Designer in diesem Bereich angezeigt. Wenn Sie eine Anwendung entwickeln, verbringen Sie die meiste Zeit in diesem zentralen Bereich.

Visual Studio verwendet *Projekte*, um Code für eine App zu ordnen, und *Projektmappen*, um Ihre Projekte zu ordnen. Ein Projekt beinhaltet alle Optionen, Einstellungen und Regeln, die Sie zum Erstellen Ihrer Anwendung verwendet haben. Es verwaltet auch die Beziehungen zwischen allen Projektdateien und externen Dateien. Erstellen Sie zunächst ein neues Projekt und eine Projektmappe, um ihre Anwendung zu erstellen.

### <a name="to-create-a-console-app-project"></a>Erstellen eines Konsolenanwendungsprojekts

1. Wählen Sie auf der Menüleiste die Optionen **Datei > Neu > Projekt** aus, um das Dialogfeld **Neues Projekt** zu öffnen.

   ![Wählen Sie auf der Menüleiste die Optionen Datei > Neu > Projekt aus](../ide/media/get-started-cpp-file-new-project-menu.png "On the menu bar, choose File > New > Project")

1. Wählen Sie im Dialogfeld **Neues Projekt** **Installiert > Visual C++** aus, sofern es noch nicht ausgewählt ist. Wählen Sie im mittleren Bereich die Vorlage **Windows-Konsolenanwendung** aus. Geben Sie *HelloApp* im Bearbeitungsfeld **Name** ein.

   ![Erstellen Ihres Anwendungsprojekts mit dem Dialogfeld „Neues Projekt“](../ide/media/get-started-cpp-new-project-dialog.png "Use the New Project dialog to create your app project")

   Abhängig von Ihren installierten Visual Studio-Workloads und Komponenten kann Ihr Dialogfeld andere Auswahlmöglichkeiten enthalten. Falls Ihnen keine Visual C++-Projektvorlagen angezeigt werden, müssen Sie den Visual Studio-Installer erneut ausführen, und die Workload **Desktopentwicklung mit C++** installieren. Sie können dies direkt im Dialogfeld **Neues Projekt** durchführen. Klicken Sie im Dialogfeld auf den Link **Visual Studio-Installer öffnen**, um den Installer zu starten.

1. Klicken Sie auf die Schaltfläche **OK**, um das Projekt und die Projektmappe zu erstellen.

   Das Projekt und die Projektmappe „HelloApp“, mit den grundlegenden Dateien für eine Windows-Konsolenanwendung, werden erstellt und automatisch in den **Projektmappen-Explorer** geladen. Die Datei „HelloApp.cpp“ wird im Code-Editor geöffnet. Diese Elemente werden im **Projektmappen-Explorer** angezeigt:

   ![Dateien für die Projektmappe im Projektmappen-Explorer](../ide/media/get-started-cpp-solution-explorer.png "Files for the solution in Solution Explorer")

## <a name="add-code-to-the-app"></a>Hinzufügen von Code zu einer App

Als Nächstes fügen Sie Code hinzu, um das Wort „Hallo“ im Konsolenfenster anzuzeigen.

### <a name="to-edit-code-in-the-editor"></a>Bearbeiten von Code im Editor

1. Fügen Sie in der Datei „HelloApp.cpp“ eine Leerzeile vor der Zeile `return 0;` ein, und geben Sie dann diesen Code ein:

   ```cpp
   cout << "Hello\n";
   ```

   Eine rote Wellenlinie wird unter `cout`angezeigt. Wenn Sie mit dem Mauszeiger darauf zeigen, erscheint eine Fehlermeldung.

   ![Fehlertext für cout](../ide/media/get-started-cpp-intellisense-error.png "Error text for cout")

   Die Fehlermeldung wird auch im Fenster **Fehlerliste** angezeigt. Sie können dieses Fenster anzeigen, indem Sie in der Menüleiste auf **Ansicht > Fehlerliste** klicken.

   ![Fehler im Fenster „Fehlerliste“](../ide/media/get-started-cpp-error-list.png "Error in Error List window")

   In Ihrem Code fehlt eine Deklaration für [std::cout](/cpp/standard-library/iostream), die Sie in der Headerdatei \<iostream> finden können.

1. Um den iostream-Header einzuschließen, geben Sie den folgenden Code nach `#include "stdafx.h"` ein:

   ```cpp
   #include <iostream>
   using namespace std;
   ```

   Sie werden vermutlich bereits festgestellt haben, dass ein Feld erschienen ist, während Sie den Code eingegeben haben. Dieses Feld enthält Vorschläge für die automatische Vervollständigung der Zeichen, die Sie eingeben. Es ist Teil von C++ IntelliSense, das Codeeingabeaufforderungen bietet, darunter Klassen- oder Schnittstellenmember sowie Parameterinformationen. Außerdem können Sie Codeausschnitte verwenden, wobei es sich um vordefinierte Codeblöcke handelt. Weitere Informationen finden Sie unter [Using IntelliSense](../ide/using-intellisense.md) und [Code Snippets](../ide/code-snippets.md).

   ![Der korrigierte Code im Editor](../ide/media/get-started-cpp-cout-fix.png "The fixed code in the editor")

   Die rote Wellenlinie unter `cout` wird ausgeblendet, wenn Sie den Fehler korrigieren.

1. Drücken Sie **STRG+S**, um die Änderungen in der Datei zu speichern.

## <a name="build-the-app"></a>Erstellen der App

Es ist einfach, Ihren Code zu erstellen. Klicken Sie in der Menüleiste auf **Erstellen > Projektmappe erstellen**. Visual Studio erstellt die Projektmappe „HelloApp“, und informiert über den Fortschritt im **Ausgabefenster**.

   ![Erstellen der HelloApp-Projektmappe](../ide/media/get-started-cpp-build-solution.gif "Build the HelloApp solution")

## <a name="debug-and-test-the-app"></a>Debuggen und Testen der App

Sie können „HelloApp“ debuggen, um festzustellen, ob das Wort „Hallo“ im Konsolenfenster angezeigt wird.

### <a name="to-debug-the-app"></a>Debuggen der App

1. Wählen Sie auf der Menüleiste **Debuggen > Debuggen starten** aus, um den Debugger zu starten.

   ![Befehl „Debuggen starten“ im Debuggermenü](../ide/media/get-started-cpp-start-debugging-menu.png "Start Debugging command on the Debug Menu")

   Die Debugger wird gestartet und führt den Code aus. Das Konsolenfenster (ein separates Fenster, das wie eine Eingabeaufforderung aussieht) wird ein paar Sekunden lang angezeigt, wird jedoch schnell geschlossen, wenn der Debugger anhält. Um den Text anzuzeigen, müssen Sie einen Haltepunkt festlegen, um die Ausführung des Programms zu beenden.

### <a name="to-add-a-breakpoint"></a>Hinzufügen eines Haltepunktes

1. Bewegen Sie den Mauszeiger im Editor auf die Zeile `return 0;`. Wählen Sie auf der Menüleiste **Debuggen > Haltepunkt umschalten** aus. Sie können auch auf den linken Rand klicken, um einen Haltepunkt zu setzen.

     ![Befehl „Haltepunkt umschalten“ im Debuggermenü](../ide/media/get-started-cpp-toggle-breakpoint-menu.png "Toggle Breakpoint command on the Debug menu")

     Am äußeren linken Rand des Editorfensters wird ein roter Kreis neben der Codezeile angezeigt.

     ![Am Fensterrand gekennzeichneter Haltepunkt](../ide/media/get-started-cpp-breakpoint-set.png "Breakpoint indicated in window margin")

1. Drücken Sie **F5**, um mit dem Debuggen zu beginnen.

   Der Debugger wird gestartet, und ein Konsolenfenster mit dem Wort **Hello**wird angezeigt.

   ![Text „Hallo“ im Konsolenfenster](../ide/media/get-started-cpp-helloapp-window.png "Hello text in the console window")

1. Drücken Sie **UMSCHALT+F5**, um das Debuggen zu beenden.

Weitere Informationen zum Debuggen von Konsolenprojekten finden Sie unter [Konsolenprojekte](../debugger/debugging-preparation-console-projects.md).

## <a name="build-a-release-version-of-the-app"></a>Erstellen einer Releaseversion der App

Nachdem Sie überprüft haben, dass alles funktioniert, können Sie einen Releasebuild der Anwendung vorbereiten. Releasebuilds lassen die Debuginformationen aus und verwenden Compileroptimierungsoptionen, um kürzeren und schnelleren Code zu erstellen.

### <a name="to-clean-the-solution-files-and-build-a-release-version"></a>Bereinigen der Projektmappendateien und Erstellen einer Releaseversion

1. Klicken Sie in der Menüleiste auf **Erstellen > Projektmappe bereinigen**, um Zwischendateien und Ausgabedateien zu löschen, die bei vorherigen Builds erstellt wurden.

   ![Befehl „Projektmappe bereinigen“ im Menü „Erstellen“](../ide/media/get-started-cpp-clean-solution-menu.png "ExploreIDE-CleanSolution")

1. Um die Projektmappenkonfiguration für „HelloApp“ von **Debuggen** auf **Release** zu ändern, klicken Sie auf das Dropdown-Feld in der Projektmappenkonfiguration, und wählen Sie dann **Release** aus.

   ![Erstellen einer Releaseversion der Anwendung](../ide/media/get-started-cpp-set-release-configuration.png "C++IDE_ChangingBuildtoRelease")

1. Erstellen Sie die Projektmappe. Klicken Sie in der Menüleiste auf **Erstellen > Projektmappe erstellen**.

Sobald dieser Build fertiggestellt ist, haben Sie eine App erstellt, die Sie in jedes Eingabeaufforderungsfenster kopieren und dort ausführen können. Sie macht zwar nicht viel, aber sie ist der Ausgangspunkt von vielem Anderen.

Damit haben Sie den Schnellstart erfolgreich abgeschlossen. Weitere Beispiele zum Durcharbeiten finden Sie unter [Visual Studio Samples](../ide/visual-studio-samples.md).

## <a name="see-also"></a>Siehe auch

[Verwenden der Visual Studio-IDE für C++-Desktopentwicklung](/cpp/ide/using-the-visual-studio-ide-for-cpp-desktop-development)  
[Exemplarische Vorgehensweise: Erstellen einer einfachen Anwendung mit Visual C# oder Visual Basic](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md)  
[Produktivitätstipps für Visual Studio](../ide/productivity-tips-for-visual-studio.md)  
[Visual Studio-Beispiele](../ide/visual-studio-samples.md)  
[Erste Schritte mit der Entwicklung in Visual Studio](../ide/get-started-developing-with-visual-studio.md)
