---
title: Einführung in die Visual Studio-IDE
ms.date: 11/15/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fd72de016e9f44987fae43e7b49820e21af0a288
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="quickstart-first-look-at-the-visual-studio-ide"></a>Schnellstart: Ein erster Blick auf die Visual Studio-IDE

In dieser fünf- bis zehnminütigen Einführung in die integrierte Entwicklungsumgebung (IDE) von Visual Studio unternehmen wir eine Tour durch einige der Fenster, Menüs und andere Funktionen der Benutzeroberfläche.

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) kostenlos herunterladen.

## <a name="start-page"></a>Startseite

Das erste, was Sie nach dem Start von Visual Studio sehen, ist wahrscheinlich die **Startseite**. Die **Startseite** ist als „Hub“ konzipiert, um Ihnen zu helfen, die benötigten Befehle und Projektdateien schneller zu finden. Der Abschnitt **Aktuell** zeigt Projekte und Ordner an, an denen Sie zuletzt gearbeitet haben. Unter **Neues Projekt** können Sie auf einen Link klicken, um das Dialogfeld **Neues Projekt** aufzurufen, oder Sie können unter **Öffnen** ein vorhandenes Projekt oder einen Codeordner öffnen. Auf der rechten Seite befindet sich ein Feed mit den neuesten Entwicklernews.

![VS-Startseite](media/quickstart-IDE-start-page.png)

Wenn Sie die **Startseite** schließen und dann erneut anzeigen möchten, können Sie sie im Menü **Datei** erneut öffnen.

![Datei (Menü)](media/quickstart-IDE-file-menu-large.png)

Um die IDE weiter zu untersuchen, erstellen wir ein neues Projekt.

1. Geben Sie auf der **Startseite** im Suchfeld unter **Neues Projekt** `console` ein, um die Liste der Projekttypen zu filtern. Wählen Sie eine C#- oder VB-**Konsolen-App (.NET Framework)** aus. (Wenn Sie ein C++-, Javascript- oder anderer Sprachentwickler sind, können Sie alternativ ein Projekt in einer dieser Sprachen erstellen. Die Benutzeroberfläche, die angezeigt wird, ist für alle Sprachen ähnlich.)

1. Übernehmen Sie im Dialogfeld **Neues Projekt** den Standardprojektnamen, und wählen Sie dann **OK** aus.

   Das Projekt wird erstellt, und eine Datei namens *Program.cs* oder *Program.vb* wird im Fenster **Editor** geöffnet. Der **Editor** zeigt den Inhalt von Dateien an und ist der Ort, an dem Sie den Großteil Ihrer Codierungsaufgaben in Visual Studio erledigen.

## <a name="solution-explorer"></a>Projektmappen-Explorer

Der **Projektmappen-Explorer** zeigt eine grafische Darstellung der Hierarchie von Dateien und Ordnern in Ihrem Projekt-, Projektmappen- oder Codeordner an. Sie können die Hierarchie durchsuchen und im **Projektmappen-Explorer** zu einer Datei navigieren.

![Projektmappen-Explorer](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>Menüs

Die Menüleiste am oberen Rand der IDE-Gruppen gruppiert Befehle in Kategorien. Beispielsweise enthält das Menü **Projekt** Befehle, die sich auf das Projekt beziehen, in dem Sie zurzeit arbeiten. Im Menü **Extras** können Sie die IDE anpassen, indem Sie **Optionen** auswählen, oder Ihrer Installation Features hinzufügen, indem Sie auf **Get Tools and Features** (Tools und Features abrufen) klicken.

![Menüleiste](media/quickstart-IDE-menu-bar.png)

Öffnen Sie das Fenster **Fehlerliste**, indem Sie erst auf das Menü **Ansicht** und dann auf **Fehlerliste** klicken.

## <a name="error-list"></a>Fehlerliste

Die **Fehlerliste** zeigt Fehler, Warnungen und Meldungen zum aktuellen Zustand Ihres Codes an. Wenn in Ihrer Datei oder Ihrem Projekt Fehler vorhanden sind (z.B. Syntaxschreibfehler), werden diese hier aufgelistet.

![Fehlerliste](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>Ausgabefenster

Das Fenster **Ausgabe** zeigt die Ausgabemeldungen der Build- und Quellcodeverwaltung an.

Erstellen Sie das Projekt, um die Ausgabeprotokollierung anzuzeigen. Wählen Sie im Menü **Erstellen** die Option **Projektmappe erstellen**aus. Das Fenster **Ausgabe** erhält den Fokus automatisch und zeigt eine Meldung zu einem erfolgreichen Buildvorgang an.

![Ausgabefenster](media/quickstart-IDE-output.png)

## <a name="quick-launch"></a>Schnellstart

Das Feld **Schnellstart** bietet eine schnelle und einfache Möglichkeit, fast alle Aufgaben in der IDE auszuführen. Sie können Text eingeben, der sich auf die gewünschte Aufgabe bezieht. Dann wird eine Liste von Optionen angezeigt, die sich für den Text eignen. Angenommen, Sie möchten z.B. die Ausführlichkeit der Buildausgabe erhöhen, um zusätzliche Protokollierungsinformationen dazu anzuzeigen, was genau im Build vorgeht:

1. Geben Sie `verbosity` in das Feld **Schnellstart** ein, und klicken Sie dann auf **Projekte und Projektmappen > Erstellen und ausführen**  unter der Kategorie **Optionen**.

   ![Feld „Schnellstart“](media/quickstart-IDE-quick-launch.png)

   Das Dialogfeld **Optionen** wird mit der Seite **Erstellen und ausführen** geöffnet.

1. Wählen Sie unter **Ausführlichkeit der MSBuild-Projektbuildausgabe** die Option **Normal** aus, und klicken Sie dann auf die Schaltfläche **OK**.

1. Jetzt erstellen Sie das Projekt erneut, indem Sie mit der rechten Maustaste auf das Projekt **ConsoleApp1** im **Projektmappen-Explorer** klicken und **Neu erstellen** aus dem Kontextmenü auswählen.

   Nun zeigt das Fenster **Ausgabe** eine ausführlichere Protokollierung des Erstellungsprozesses an, z.B. auch, wohin welche Dateien kopiert wurden.

## <a name="send-feedback-menu"></a>Menü „Feedback senden“

Wenn Sie Probleme bei der Verwendung von Visual Studio oder Vorschläge zur Verbesserung des Produkts haben, können Sie das Menü **Feedback senden** oben in der IDE neben dem Feld **Schnellstart** verwenden.

![Menü „Feedback senden“](media/quickstart-IDE-send-feedback.png)

## <a name="next-steps"></a>Nächste Schritte

Wir haben uns nur einige der Features der Visual Studio-IDE angesehen, um uns mit der Benutzeroberfläche vertraut zu machen. Weitere mögliche Schritte:

- Lesen Sie den Abschnitt **Allgemeine Elemente der Benutzeroberfläche** der VS-Dokumentation, der sich ausführlicher mit Fenstern wie [Fehlerliste](../ide/reference/error-list-window.md), [Ausgabefenster](../ide/reference/output-window.md), [Eigenschaftenfenster](../ide/reference/properties-window.md) und dem [Dialogfeld „Optionen“](../ide/reference/options-dialog-box-visual-studio.md) befasst.

- Erfahren Sie mehr über die IDE, und versuchen Sie sich im Debuggen unter [Übersicht über die Visual Studio-IDE](../ide/visual-studio-ide.md).

## <a name="see-also"></a>Siehe auch

- [Schnellstart: Personalisieren der IDE](../ide/personalizing-the-visual-studio-ide.md)
- [Schnellstart: Codieren im Editor](../ide/quickstart-editor.md)
- [Schnellstart: Projekte und Projektmappen](../ide/quickstart-projects-solutions.md)