---
title: Einführung in die Visual Studio-IDE
ms.date: 07/12/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aeb7156998b7c6ea91205bd2c05de690b597490a
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081536"
---
# <a name="quickstart-first-look-at-the-visual-studio-ide"></a>Schnellstart: Ein erster Blick auf die Visual Studio-IDE

In dieser fünf- bis zehnminütigen Einführung in die integrierte Entwicklungsumgebung (IDE) von Visual Studio unternehmen wir eine Tour durch einige der Fenster, Menüs und andere Funktionen der Benutzeroberfläche.

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) kostenlos herunterladen.

## <a name="start-page"></a>Startseite

Das erste, was Sie nach dem Start von Visual Studio sehen, ist wahrscheinlich die **Startseite**. Die **Startseite** ist als „Hub“ konzipiert, um Ihnen zu helfen, die benötigten Befehle und Projektdateien schneller zu finden. Der Abschnitt **Aktuell** zeigt Projekte und Ordner an, an denen Sie zuletzt gearbeitet haben. Unter **Neues Projekt** können Sie auf einen Link klicken, um das Dialogfeld **Neues Projekt** aufzurufen, oder Sie können unter **Öffnen** ein vorhandenes Codeprojekt oder einen Codeordner öffnen. Auf der rechten Seite befindet sich ein Feed mit den neuesten Entwicklernews.

![Startseite in Visual Studio](media/start-page-dark.png)

Wenn Sie die **Startseite** schließen und dann erneut anzeigen möchten, können Sie sie im Menü **Datei** erneut öffnen.

![Dateimenü in Visual Studio](media/file-menu-start-page-dark.png)

## <a name="create-a-project"></a>Erstellen eines Projekts

Erstellen Sie ein neues Projekt, um die Features in Visual Studio besser kennenzulernen.

1. Geben Sie auf der **Startseite** im Suchfeld unter **Neues Projekt** **Konsole** ein, um die Liste der Projekttypen nach denen zu filtern, die „Konsole“ im Namen enthalten.

   ![Suchen von Projektvorlagen auf der Visual Studio-Startseite](media/start-page-search-templates-dark.png)

   Visual Studio stellt mehrere Arten von Projektvorlagen bereit, durch die Sie schnell mit dem Programmieren beginnen können. Wählen Sie die C#-Projektvorlage **Konsolen-App (.NET Framework)** aus. (Wenn Sie mit Visual Basic, C++, JavaScript oder einer anderen Sprache entwickeln, können Sie alternativ ein Projekt in einer dieser Sprachen erstellen. Die Benutzeroberfläche, die angezeigt wird, ist für alle Programmiersprachen ähnlich.)

1. Übernehmen Sie im angezeigten Dialogfeld **Neues Projekt** den Standardprojektnamen, und klicken Sie anschließend auf **OK**.

   Das Projekt wird erstellt, und eine Datei namens *Program.cs* wird im Fenster **Editor** geöffnet. Der **Editor** zeigt den Inhalt von Dateien an und ist der Ort, an dem Sie den Großteil Ihrer Codierungsaufgaben in Visual Studio erledigen.

   ![Editor in Visual Studio](media/editor-dark.png)

## <a name="solution-explorer"></a>Projektmappen-Explorer

Im **Projektmappen-Explorer**, der sich in Visual Studio üblicherweise auf der rechten Seite befindet, wird eine grafische Darstellung der Hierarchie von Dateien und Ordnern in Ihrem Projekt-, Projektmappen- oder Codeordner angezeigt. Sie können die Hierarchie durchsuchen und im **Projektmappen-Explorer** zu einer Datei navigieren.

![Projektmappen-Explorer in Visual Studio](media/solution-explorer-console-app-dark.png)

## <a name="menus"></a>Menüs

Die Menüleiste am oberen Rand der Visual Studio-Gruppen gruppiert Befehle in Kategorien. Beispielsweise enthält das Menü **Projekt** Befehle, die sich auf das Projekt beziehen, in dem Sie zurzeit arbeiten. Im Menü **Extras** können Sie das Verhalten von Visual Studio anpassen, indem Sie auf **Optionen** klicken, oder Features zu Ihrer Installation hinzufügen, indem Sie auf **Tools und Features abrufen** klicken.

![Menüleiste in Visual Studio](media/menu-bar-dark.png)

Öffnen Sie das Fenster **Fehlerliste**, indem Sie erst auf das Menü **Ansicht** und dann auf **Fehlerliste** klicken.

## <a name="error-list"></a>Fehlerliste

Die **Fehlerliste** zeigt Fehler, Warnungen und Meldungen zum aktuellen Zustand Ihres Codes an. Wenn in Ihrer Datei oder Ihrem Projekt Fehler vorhanden sind (z.B. eine fehlende Klammer oder ein fehlendes Semikolon), werden diese hier aufgelistet.

![Fehlerliste in Visual Studio](media/error-list-dark.png)

## <a name="output-window"></a>Ausgabefenster

Im **Ausgabefenster** werden Ausgabemeldungen von der Erstellung Ihres Projekts sowie vom Anbieter der Quellcodeverwaltung angezeigt.

Erstellen Sie das Projekt, um die Buildausgaben anzuzeigen. Wählen Sie im Menü **Erstellen** die Option **Projektmappe erstellen**aus. Das Fenster **Ausgabe** erhält den Fokus automatisch und zeigt eine Meldung zu einem erfolgreichen Buildvorgang an.

![Ausgabefenster in Visual Studio](media/output-window-dark.png)

## <a name="quick-launch"></a>Schnellstart

Das Feld **Schnellstart** bietet eine schnelle und einfache Möglichkeit, fast alle Aufgaben in Visual Studio auszuführen. Sie können Text eingeben, der sich auf die gewünschte Aufgabe bezieht. Dann wird eine Liste von Optionen angezeigt, die sich für den Text eignen. Angenommen, Sie möchten z.B. die Ausführlichkeit der Buildausgabe erhöhen, um Details dazu anzuzeigen, was genau im Build geschieht. Sie könnten folgendermaßen vorgehen:

1. Geben Sie im Feld **Schnellstart** **Ausführlichkeit** ein. Klicken Sie in den angezeigten Ergebnissen unter der Kategorie **Optionen** auf **Projekte und Projektmappen > Erstellen und ausführen**.

   ![Feld „Schnellstart“ in Visual Studio](media/quick-launch-verbosity-dark.png)

   Das Dialogfeld **Optionen** wird mit der Seite **Erstellen und ausführen** geöffnet.

1. Wählen Sie unter **Ausführlichkeit der MSBuild-Projektbuildausgabe** die Option **Normal** aus, und klicken Sie dann auf die Schaltfläche **OK**.

1. Erstellen Sie das Projekt erneut, indem Sie mit der rechten Maustaste auf das Projekt **ConsoleApp1** im **Projektmappen-Explorer** klicken und **Neu erstellen** aus dem Kontextmenü auswählen.

   Nun zeigt das Fenster **Ausgabe** eine ausführlichere Protokollierung des Erstellungsprozesses an, z.B. auch, wohin welche Dateien kopiert wurden.

   ![Ausführliche Buildausgabe in Visual Studio](media/build-output-verbose-dark.png)

## <a name="send-feedback-menu"></a>Menü „Feedback senden“

Wenn Sie Probleme bei der Verwendung von Visual Studio oder Vorschläge zur Verbesserung des Produkts haben, können Sie das Menü **Feedback senden** im oberen Bereich des Visual Studio-Fensters neben dem Feld **Schnellstart** verwenden.

![Menü „Feedback senden“ in Visual Studio](media/send-feedback-dark.png)

## <a name="next-steps"></a>Nächste Schritte

Wir haben uns nur einige der Features von Visual Studio angesehen, um uns mit der Benutzeroberfläche vertraut zu machen. Weitere mögliche Schritte:

- Erfahren Sie mehr über Visual Studio, und versuchen Sie sich im Debuggen unter [Übersicht über die Visual Studio-IDE](../ide/visual-studio-ide.md).

- Lesen Sie den Abschnitt **Allgemeine Elemente der Benutzeroberfläche** der VS-Dokumentation, der sich ausführlicher mit Fenstern wie [Fehlerliste](../ide/reference/error-list-window.md), [Ausgabefenster](../ide/reference/output-window.md), [Eigenschaftenfenster](../ide/reference/properties-window.md) und dem Dialogfeld [Optionen](../ide/reference/options-dialog-box-visual-studio.md) befasst.

## <a name="see-also"></a>Siehe auch

- [Schnellstart: Personalisieren der IDE](../ide/personalizing-the-visual-studio-ide.md)
- [Schnellstart: Schreiben von Code im Editor](../ide/quickstart-editor.md)
- [Schnellstart: Projekte und Projektmappen](../ide/quickstart-projects-solutions.md)