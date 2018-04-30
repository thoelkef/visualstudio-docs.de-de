---
title: 'Arbeiten mit Python, Schritt 1: Erstellen eines Projekts'
description: Dies ist Schritt 1 eines zentralen Tutorials für die Arbeit mit Python in Visual Studio, in dem das gesamte Tutorial zusammengefasst wird, die Voraussetzungen beschrieben werden und das Verfahren zum Erstellen eines neuen Python-Projekts Schritt für Schritt erläutert wird.
ms.date: 01/16/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 5857f06deea3bc4e7c8af481330e6c66162e2f2a
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="working-with-python-in-visual-studio"></a>Arbeiten mit Python in Visual Studio

Python ist eine beliebte Programmiersprache, die zuverlässig, flexibel, leicht zu erlernen und für alle Betriebssysteme kostenlos ist und sowohl von einer starken Entwicklercommunity als auch vielen kostenlosen Bibliotheken unterstützt wird. Die Programmiersprache unterstützt alle Arten von Entwicklung, einschließlich Webanwendungen, Webdienste, Desktop-Apps, Skripts und wissenschaftliche Berechnungen, und wird gleichermaßen von vielen Universitäten, Wissenschaftlern sowie hobbymäßigen und professionellen Entwicklern verwendet.

Visual Studio bietet erstklassige Unterstützung für Python. In diesem Tutorial finden Sie Informationen zu den folgenden Vorgängen:

- [Step 0: Installation (Schritt 0: Installation)](tutorial-working-with-python-in-visual-studio-step-00-installation.md)
- [Schritt 1: Erstellen eines Python-Projekts (wird in diesem Artikel beschrieben)](#step-1-create-a-new-python-project)
- [Step 2: Writing and running code to see Visual Studio IntelliSense at work (Schritt 2: Schreiben und Ausführen von Code, um mit Visual Studio IntelliSense in der Praxis zu arbeiten)](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)
- [Step 3: Create more code in the interactive REPL window (Schritt 3: Erstellen von weiterem Code im interaktivem REPL-Fenster)](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)
- [Step 4: Run the completed program in the Visual Studio debugger (Schritt 4: Ausführen eines abgeschlossenen Programms im Visual Studio-Debugger)](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)
- [Step 5: Installing packages and managing Python environments (Schritt 5: Installieren von Paketen und Verwalten von Python-Umgebungen)](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)
- [Step 6: Working with Git (Schritt 6: Arbeiten mit Git)](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

## <a name="prerequisites"></a>Erforderliche Komponenten

- Visual Studio 2017 mit installierter Python-Workload. Anweisungen finden Sie in [Schritt 0](tutorial-working-with-python-in-visual-studio-step-00-installation.md).

## <a name="step-1-create-a-new-python-project"></a>Schritt 1: Erstellen eines neuen Python-Projekts

Visual Studio verwaltet in einem *Projekt* sämtliche Dateien, die zusammen eine einzige Anwendung erstellen, einschließlich Quellcode, Ressourcen, Konfigurationen, etc. Ein Projekt formalisiert und verwaltet die Beziehung zwischen allen Projektdateien und externen Ressourcen, die für mehrere Projekte freigegeben sind. In Projekten kann Ihre Anwendung problemlos erweitert und vergrößert werden, anders als dies beim Verwalten der Beziehungen eines Projekts in Ad-Hoc-Ordnern, Skripten, Textdateien oder ohne andere technische Optionen der Fall wäre.

In diesem Tutorial beginnen Sie mit einem einfachen Projekt, das nur eine leere Codedatei enthält.

1. Klicken Sie in Visual Studio auf **Datei > Neu > Projekt** (STRG+UMSCHALT+N), wodurch das Dialogfeld **Neues Projekt** geöffnet wird. An dieser Stelle durchsuchen Sie sprachenübergreifende Vorlagen und wählen anschließend eine Sprache für Ihr Projekt aus und geben an, wo Visual Studio Dateien speichern soll.

1. Klicken Sie auf der linken Seite auf **Installiert > Python**, oder suchen Sie nach „Python“, um Python-Vorlagen abzurufen. Über die Suchfunktion können Sie leicht Vorlagen finden, wenn Sie deren Speicherorte in der Sprachenstruktur nicht kennen.

    ![Dialogfeld „Neues Projekt“ mit Python-Projekten](media/vs-getting-started-python-01-new-project.png)

    Beachten Sie, dass die Python-Unterstützung in Visual Studio eine Reihe von Projektvorlagen, einschließlich Webanwendungen, unter Verwendung der Bottle-, Flask- und Django-Frameworks beinhaltet. Im Rahmen dieser exemplarischen Vorgehensweise beginnen wir jedoch mit einem leeren Projekt.

1. Klicken Sie auf die Vorlage **Python-Anwendung**, geben Sie einen Namen für das Projekt an, und klicken Sie auf **OK**.

1. Nach einigen Augenblicken zeigt Visual Studio die Projektstruktur im **Projektmappen-Explorer**-Fenster (1) an. Die Standardcodedatei ist im Editor (2) geöffnet. Das Eigenschaftenfenster (3) wird ebenfalls angezeigt. Darin sind zusätzliche Informationen zu jedem im Projektmappen-Explorer ausgewählten Element enthalten, einschließlich Informationen zum genauen Speicherort auf dem Datenträger.

    ![Projektmappen-Explorer mit einem Python-Projekt](media/vs-getting-started-python-02-windows.png)

1. Nehmen Sie sich einige Minuten Zeit, um sich mit dem Projektmappen-Explorer vertraut zu machen. Über diese Funktion durchsuchen Sie Dateien und Ordner in Ihrem Projekt.

    ![Erweiterter Projektmappen-Explorer zum Anzeigen von verschiedenen Funktionen](media/vs-getting-started-python-03-solution-explorer.png)

    (1) Ihr Projekt wird fettgedruckt dargestellt, mit dem Namen, den Sie im Dialogfeld „Neues Projekt“ festgelegt haben. Auf dem Datenträger wird dieses Projekt von einer `.pyproj`-Datei im Projektordner dargestellt.

    (2) Auf der oberen Ebene finden Sie eine *Projektmappe*, die standardmäßig denselben Namen hat wie Ihr Projekt. Bei einer Projektmappe, die von einer `.sln`-Datei dargestellt wird, handelt es sich um einen Container für mindestens ein zugehöriges Projekt. Wenn Sie z.B. eine C++-Erweiterung für Ihre Python-Anwendung schreiben, kann das C++-Projekt in derselben Projektmappe gespeichert werden. Die Projektmappe enthält unter Umständen neben Projekten für dedizierte Projektprogramme ein Projekt für einen Webdienst. 

    (3) Unter Ihrem Projekt werden Quelldateien angezeigt – in diesem Fall eine einzelne `.py`-Datei. Wenn Sie auf eine Datei klicken, werden deren Eigenschaften im Eigenschaftenfenster angezeigt. Wenn Sie auf eine Datei doppelklicken, wird diese je nach Dateityp auf die vorgesehene Weise geöffnet.

    (4) Unter diesem Projekt wird außerdem der Knoten **Python-Umgebungen** angezeigt. Wenn der Knoten erweitert ist, werden die für Sie verfügbaren Python-Interpreters angezeigt. Erweitern Sie einen Interpreterknoten, um die in dieser Umgebung (5) installierten Bibliotheken abzurufen.

    Klicken Sie mit der rechten Maustaste im Projektmappen-Explorer auf einen beliebigen Knoten oder ein beliebiges Element, um auf ein Menü der entsprechenden Befehle zuzugreifen. Beispielsweise können Sie über den Befehl **Umbenennen** den Namen jedes beliebigen Knotens oder Elements umbenennen, einschließlich des Projekts und der Projektmappe.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Writing and running code (Schreiben und Ausführen von Code)](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)

## <a name="going-deeper"></a>Vertiefung

- [Python-Projekte in Visual Studio](managing-python-projects-in-visual-studio.md)
- [Erfahren Sie mehr über die Python-Sprache unter python.org](https://www.python.org)
- [Python für Anfänger](https://www.python.org/about/gettingstarted/)
- [Kostenlose Python-Kurse in der Microsoft Virtual Academy](https://mva.microsoft.com/search/SearchResults.aspx#!q=python)
- [Top Python Questions at Microsoft Virtual Academy (Meistgestellte Fragen an der Microsoft Virtual Academy)](https://aka.ms/mva-top-python-questions)
