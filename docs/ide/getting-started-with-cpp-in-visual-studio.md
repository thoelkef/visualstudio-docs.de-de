---
title: Erste Schritte mit C++ in Visual Studio
description: ''
ms.custom: mvc
ms.date: 12/04/2017
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: tutorial
author: corob-msft
ms.author: tglee
manager: douge
dev_langs:
- CPP
ms.workload:
- cplusplus
ms.openlocfilehash: cec2164cf248f9301a2e75f0babe4d6f71726ff2
ms.sourcegitcommit: 551f13774e8bb0eb47cbd973745628a956e866aa
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2018
ms.locfileid: "49459672"
---
# <a name="get-started-with-c-in-visual-studio"></a>Erste Schritte mit C++ in Visual Studio

Arbeiten Sie sich durch diesen Schnellstart, um mit den vielen Tools und Dialogfeldern vertraut zu werden, die Sie beim Entwickeln von Anwendungen mit C++ in Visual Studio verwenden können. Erstellen Sie eine „Hallo Welt“-Anwendung, und lernen Sie mehr über das Arbeiten in der integrierten Entwicklungsumgebung (IDE).

## <a name="prerequisites"></a>Erforderliche Komponenten

Sie müssen sich nicht mit C++ auskennen, um diesen Schnellstart durchzuführen, aber Sie sollten grundlegende Programmier- und Debuggingkonzepte kennen. Die Visual Studio-Dokumentation bringt Ihnen nicht bei, wie man mit C++ programmiert. Nützliche Informationen über Lernressourcen zu C++ finden Sie unter [Erste Schritte](https://isocpp.org/get-started) auf der Website von ISO C++.

Um diesen Schritten folgen zu können, benötigen Sie Visual Studio 2017 Version 15.3 oder höher, und die Workload **Desktopentwicklung mit C++** muss installiert sein. Einen kurzen Leitfaden zur Installation finden Sie unter [Install C++ support in Visual Studio (Installieren von C++-Unterstützung in Visual Studio)](/cpp/build/vscpp-step-0-installation).

## <a name="create-a-console-app"></a>Erstellen einer Konsolenanwendung

Starten Sie Visual Studio, falls es noch nicht ausgeführt wird.

![IDE mit angewendeten Visual C&#43;&#43;-Einstellungen](../ide/media/get-started-cpp-ide-layout.png)

Wenn Sie Visual Studio geöffnet haben, können Sie die drei grundlegenden Teile der IDE sehen: Toolsfenster, Menüs und Symbolleisten und den Hauptfensterbereich. Toolfenster sind auf der linken und rechten Seite an das Fenster der Anwendung angedockt. Das Feld **Schnellstart**, die Menüleiste und die Standardsymbolleiste finden Sie oben. In der Mitte des Fensters befindet sich die **Startseite**. Wenn Sie eine Projektmappe oder ein Projekt öffnen, werden Editoren und Designer in diesem Bereich angezeigt. Wenn Sie eine Anwendung entwickeln, verbringen Sie die meiste Zeit in diesem zentralen Bereich.

Visual Studio verwendet *Projekte*, um Code für eine App zu ordnen, und *Projektmappen*, um Ihre Projekte zu ordnen. Ein Projekt beinhaltet alle Optionen, Einstellungen und Regeln, die Sie zum Erstellen Ihrer Anwendung verwendet haben. Es verwaltet auch die Beziehungen zwischen allen Projektdateien und externen Dateien. Erstellen Sie zunächst ein neues Projekt und eine Projektmappe, um ihre Anwendung zu erstellen.

### <a name="to-create-a-console-app-project"></a>Erstellen eines Konsolenanwendungsprojekts

1. Wählen Sie auf der Menüleiste die Optionen **Datei > Neu > Projekt** aus, um das Dialogfeld **Neues Projekt** zu öffnen.

   ![Klicken Sie in der Menüleiste auf „Datei > Neu > Projekt“.](../ide/media/get-started-cpp-file-new-project-menu.png)

1. Wählen Sie im Dialogfeld **Neues Projekt** **Installiert > Visual C++** aus, sofern es noch nicht ausgewählt ist. Wählen Sie im mittleren Bereich die Vorlage **Windows-Konsolenanwendung** aus. Geben Sie *HelloApp* im Bearbeitungsfeld **Name** ein.

   ![Verwenden Sie das Dialogfeld „Neues Projekt“, um Ihr App-Projekt zu erstellen.](../ide/media/get-started-cpp-new-project-dialog.png)

   Abhängig von Ihren installierten Visual Studio-Workloads und Komponenten kann Ihr Dialogfeld andere Auswahlmöglichkeiten enthalten. Falls Ihnen keine Visual C++-Projektvorlagen angezeigt werden, müssen Sie den Visual Studio-Installer erneut ausführen, und die Workload **Desktopentwicklung mit C++** installieren. Sie können dies direkt im Dialogfeld **Neues Projekt** durchführen. Klicken Sie im Dialogfeld auf den Link **Visual Studio-Installer öffnen**, um den Installer zu starten.

1. Klicken Sie auf die Schaltfläche **OK**, um das Projekt und die Projektmappe zu erstellen.

   Das Projekt und die Projektmappe „HelloApp“, mit den grundlegenden Dateien für eine Windows-Konsolenanwendung, werden erstellt und automatisch in den **Projektmappen-Explorer** geladen. Die Datei *HelloApp.cpp* wird im Code-Editor geöffnet. Diese Elemente werden im **Projektmappen-Explorer** angezeigt:

   ![Dateien für die Projektmappe im Projektmappen-Explorer](../ide/media/get-started-cpp-solution-explorer.png)

## <a name="add-code-to-the-app"></a>Hinzufügen von Code zu einer App

Als Nächstes fügen Sie Code hinzu, um das Wort „Hallo“ im Konsolenfenster anzuzeigen.

### <a name="to-edit-code-in-the-editor"></a>Bearbeiten von Code im Editor

1. Fügen Sie in der Datei *HelloApp.cpp* eine Leerzeile vor der Zeile `return 0;` ein, und geben Sie dann diesen Code ein:

   ```cpp
   cout << "Hello\n";
   ```

   Eine rote Wellenlinie wird unter `cout`angezeigt. Wenn Sie mit dem Mauszeiger darauf zeigen, erscheint eine Fehlermeldung.

   ![Fehlertext für "cout"](../ide/media/get-started-cpp-intellisense-error.png)

   Die Fehlermeldung wird auch im Fenster **Fehlerliste** angezeigt. Sie können dieses Fenster anzeigen, indem Sie in der Menüleiste auf **Ansicht > Fehlerliste** klicken.

   ![Fehler im Fenster „Fehlerliste“](../ide/media/get-started-cpp-error-list.png)

   In Ihrem Code fehlt eine Deklaration für [std::cout](/cpp/standard-library/iostream), die Sie in der Headerdatei *\<iostream>* finden können.

1. Um den Header *iostream* einzuschließen, geben Sie den folgenden Code nach `#include "stdafx.h"` ein:

   ```cpp
   #include <iostream>
   using namespace std;
   ```

   Sie werden vermutlich bereits festgestellt haben, dass ein Feld erschienen ist, während Sie den Code eingegeben haben. Dieses Feld enthält Vorschläge für die automatische Vervollständigung der Zeichen, die Sie eingeben. Es ist Teil von C++ IntelliSense, das Codeeingabeaufforderungen bietet, darunter Klassen- oder Schnittstellenmember sowie Parameterinformationen. Außerdem können Sie Codeausschnitte verwenden, wobei es sich um vordefinierte Codeblöcke handelt. Weitere Informationen finden Sie unter [Verwenden von IntelliSense](../ide/using-intellisense.md) und [Codeausschnitte](../ide/code-snippets.md).

   ![Der geänderte Code im Editor](../ide/media/get-started-cpp-cout-fix.png)

   Die rote Wellenlinie unter `cout` wird ausgeblendet, wenn Sie den Fehler korrigieren.

1. Drücken Sie **STRG+S**, um die Änderungen in der Datei zu speichern.

## <a name="build-the-app"></a>Erstellen der App

Es ist einfach, Ihren Code zu erstellen. Klicken Sie in der Menüleiste auf **Erstellen > Projektmappe erstellen**. Visual Studio erstellt die Projektmappe „HelloApp“, und informiert über den Fortschritt im **Ausgabefenster**.

   ![Erstellen der HelloApp-Projektmappe](../ide/media/get-started-cpp-build-solution.gif)

## <a name="debug-and-test-the-app"></a>Debuggen und Testen der App

Sie können „HelloApp“ debuggen, um festzustellen, ob das Wort „Hallo“ im Konsolenfenster angezeigt wird.

### <a name="to-debug-the-app"></a>Debuggen der App

Wählen Sie auf der Menüleiste **Debuggen > Debuggen starten** aus, um den Debugger zu starten.

![Befehl "Debugging starten" im Menü "Debuggen"](../ide/media/get-started-cpp-start-debugging-menu.png)

Die Debugger wird gestartet und führt den Code aus. Das Konsolenfenster (ein separates Fenster, das wie eine Eingabeaufforderung aussieht) wird ein paar Sekunden lang angezeigt, wird jedoch schnell geschlossen, wenn der Debugger anhält. Um den Text anzuzeigen, müssen Sie einen Haltepunkt festlegen, um die Ausführung des Programms zu beenden.

### <a name="to-add-a-breakpoint"></a>Hinzufügen eines Haltepunktes

1. Bewegen Sie den Mauszeiger im Editor auf die Zeile `return 0;`. Wählen Sie auf der Menüleiste **Debuggen > Haltepunkt umschalten** aus. Sie können auch auf den linken Rand klicken, um einen Haltepunkt zu setzen.

     ![Befehl "Haltepunkt umschalten" im Menü "Debuggen"](../ide/media/get-started-cpp-toggle-breakpoint-menu.png)

     Am äußeren linken Rand des Editorfensters wird ein roter Kreis neben der Codezeile angezeigt.

     ![Am Rand des Fensters angegebener Breakpoint](../ide/media/get-started-cpp-breakpoint-set.png)

1. Drücken Sie **F5**, um mit dem Debuggen zu beginnen.

   Der Debugger wird gestartet, und ein Konsolenfenster mit dem Wort **Hello**wird angezeigt.

   ![Text „Hello“ im Konsolenfenster](../ide/media/get-started-cpp-helloapp-window.png)

1. Drücken Sie **UMSCHALT+F5**, um das Debuggen zu beenden.

Weitere Informationen zum Debuggen von Konsolenprojekten finden Sie unter [Konsolenprojekte](../debugger/debugging-preparation-console-projects.md).

## <a name="build-a-release-version-of-the-app"></a>Erstellen einer Releaseversion der App

Nachdem Sie überprüft haben, dass alles funktioniert, können Sie einen Releasebuild der Anwendung vorbereiten. Releasebuilds lassen die Debuginformationen aus und verwenden Compileroptimierungsoptionen, um kürzeren und schnelleren Code zu erstellen.

### <a name="to-clean-the-solution-files-and-build-a-release-version"></a>Bereinigen der Projektmappendateien und Erstellen einer Releaseversion

1. Klicken Sie in der Menüleiste auf **Erstellen > Projektmappe bereinigen**, um Zwischendateien und Ausgabedateien zu löschen, die bei vorherigen Builds erstellt wurden.

   ![Befehl "Projektmappe bereinigen" im Menü "Erstellen"](../ide/media/get-started-cpp-clean-solution-menu.png)

1. Um die Projektmappenkonfiguration für „HelloApp“ von **Debuggen** auf **Release** zu ändern, klicken Sie auf das Dropdown-Feld in der Projektmappenkonfiguration, und wählen Sie dann **Release** aus.

   ![Version der Anwendung erstellen](../ide/media/get-started-cpp-set-release-configuration.png)

1. Erstellen Sie die Projektmappe. Klicken Sie in der Menüleiste auf **Erstellen > Projektmappe erstellen**.

Sobald dieser Build fertiggestellt ist, haben Sie eine App erstellt, die Sie in jedes Eingabeaufforderungsfenster kopieren und dort ausführen können. Sie macht zwar nicht viel, aber sie ist der Ausgangspunkt von vielem Anderen.

Damit haben Sie den Schnellstart erfolgreich abgeschlossen.

## <a name="see-also"></a>Siehe auch

- [Verwenden der Visual Studio-IDE für C++-Desktopentwicklung](/cpp/ide/using-the-visual-studio-ide-for-cpp-desktop-development)
- [Exemplarische Vorgehensweise: Erstellen einer einfachen Anwendung mit C# oder Visual Basic](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md)
- [Produktivitätstipps für Visual Studio](../ide/productivity-tips-for-visual-studio.md)
