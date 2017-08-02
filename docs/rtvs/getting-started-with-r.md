---
title: "Erste Schritte mit R für Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 4/26/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 39228cf0-8d21-43bb-a2ce-5e5fdc81ec41
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 27c16d7315acaa0efd4aa8b866b44784ffe056a4
ms.contentlocale: de-de
ms.lasthandoff: 05/12/2017

---

# <a name="getting-started-with-r-tools-for-visual-studio"></a>Erste Schritte mit R Tools für Visual Studio

Sobald Sie R Tools für Visual Studio (RTVS) installiert haben (siehe [Installation](installation.md)), erhalten Sie schnell einen Vorgeschmack der Funktionalität, die diese Tools bieten. In den folgenden Abschnitten werden Sie näher an das Thema herangeführt:

- [Erstellen eines R-Projekts](#create-an-r-project)
- [Erkunden des interaktiven Fensters und IntelliSense](#explore-the-interactive-window-and-intellisense)
- [Features zur Codebearbeitung](#experience-code-editing-features)
- [Debuggen Ihres Codes](#debugging-your-code)
- [Nächste Schritte](#next-steps)

## <a name="create-an-r-project"></a>Erstellen eines R-Projekts

1. Starten Sie Visual Studio.
1. Wählen Sie **Datei > Neu > Projekt...** aus. (Strg+Umschalt+N)
1. Wählen Sie unter **Vorlagen > R** „R-Projekt“ aus, weisen Sie dem Projekt einen Namen und Speicherort zu, und wählen Sie **OK** aus:

   ![Dialogfeld „Neues Projekt“ für R in Visual Studio (RTVS in VS2017)](~/docs/rtvs/media/getting-started-01-new-project.png)

1. Sobald das Projekt erstellt wurde, sehen Sie Folgendes:

    - Auf der rechten Seite ist der Visual Studio-Projektmappen-Explorer dargestellt, in dem Sie Ihr Projekt innerhalb einer *Projektmappe* sehen. (Projektmappen können eine beliebige Anzahl von Projekten verschiedenen Typs enthalten. Informationen finden Sie unter [Projekte](projects.md).)
    - Oben links befindet sich eine neue R-Datei (`script.R`), wobei Sie Quellcode mit allen Bearbeitungsfunktionen von Visual Studio bearbeiten können.
    - Unten links sehen Sie das Fenster **R Interactive**, in dem Sie Code interaktiv entwickeln und testen können.

> [!Note]
> Sie können das **R Interactive**-Fenster verwenden, selbst wenn Sie keine Projekte geöffnet haben und auch wenn ein anderer Projekttyp geladen wird. Wählen Sie einfach jederzeit **R Tools > Fenster > R Interactive** aus.

## <a name="explore-the-interactive-window-and-intellisense"></a>Erkunden des interaktiven Fensters und IntelliSense

1. Überprüfen Sie, ob das interaktive Fenster funktioniert, indem Sie `3 + 4` eingeben und dann die EINGABETASTE drücken, um das Ergebnis anzuzeigen:

    ![„R Interactive“-Fenster in Visual Studio 2017 (VS2017)](~/docs/rtvs/media/getting-started-02-interactive1.png)

1. Geben Sie etwas komplizierteres ein, `ds <- c(1.5, 6.7, 8.9) * 1:12`, und geben Sie `ds` ein, um das Ergebnis anzuzeigen:

    ![Zusätzliches interaktives Beispiel für R in Visual Studio](~/docs/rtvs/media/getting-started-03-interactive2.png)

1. Geben Sie `mean(ds)` ein, beachten Sie jedoch, dass sobald Sie `m` oder `me` eingeben, Visual Studio IntelliSense Optionen zur automatischen Vervollständigung bereitstellt, so wie unten dargestellt. Wenn die gewünschte Vervollständigung in der Liste ausgewählt ist, drücken Sie die TAB-TASTE, um sie einzufügen. Sie können zudem Ihre Auswahl mit den Pfeiltasten oder der Maus bearbeiten.

    ![IntelliSense erscheint, wenn Sie Code eingeben](~/docs/rtvs/media/getting-started-04-intellisense1.png)

1. Nachdem Sie `mean` abgeschlossen haben, geben Sie die öffnende Klammer `(` ein, und achten Sie darauf, wie IntelliSense Ihnen Inline-Hilfe für die Funktion bietet:

    ![IntelliSense gibt Hilfestellung für eine Funktion](~/docs/rtvs/media/getting-started-05-intellisense2.png)

1. Schließen Sie die Zeile `mean(ds)` ab, und drücken Sie die EINGABETASTE, um das Ergebnis anzuzeigen (`[1] 39.51667`).

1. Das „Interactive“-Fenster wird mit Hilfe integriert, geben Sie deshalb z.B. `?mean` ein, um die Hilfe für diese Funktion im Fenster **R-Hilfe** in Visual Studio anzuzeigen. Zusätzliche Details zu dieser Funktion finden Sie unter [Help in R Tools for Visual Studio (Hilfe in R Tools für Visual Studio)](getting-started-help.md).

    ![Fenster „R-Hilfe“ in Visual Studio](~/docs/rtvs/media/getting-started-06-help.png)

1. Einige Befehle, z.B. `plot(1:100)`, öffnen ein neues Fenster in Visual Studio, wenn die Ausgabe nicht direkt im interaktiven Fenster angezeigt werden kann.

    ![Darstellung eines Plots in Visual Studio](~/docs/rtvs/media/getting-started-07-plot-window.png)

Mit dem interaktiven Fenster können Sie auch Ihre Versionsgeschichte überprüfen, Arbeitsbereiche laden und speichern, an den Debugger anfügen sowie mit Quellcodedateien in verknüpften Kopier- und Einfügevorgängen interagieren. Weitere Informationen finden Sie unter [Arbeiten mit dem interaktiven R-Fenster](interactive-repl.md).

## <a name="experience-code-editing-features"></a>Features zur Codebearbeitung

Durch die kurze Arbeit mit dem interaktiven Fenster weiter oben haben Sie grundlegende Bearbeitungsfunktionen kennengelernt, z.B. IntelliSense, die auch im Code-Editor funktionieren. Wenn Sie denselben Code wie zuvor eingeben, erhalten Sie die gleichen Aufforderungen für die automatische Vervollständigung und IntelliSense, jedoch natürlich nicht die Ausgabe.

Durch das Schreiben von Code in eine `.R`-Datei können Sie Ihren gesamten Code auf einmal anzeigen und dadurch einfacher kleine Änderungen an unterschiedlichen Teilen des Codes vornehmen. Dann können Sie die Ergebnisse anzeigen, indem Sie den Code schnell im interaktiven Fenster ausführen. Außerdem können Sie so viele Dateien in einem Projekt haben, wie Sie möchten. Wenn sich Code in einer Datei befindet, können Sie ihn auch schrittweise im Debugger ausführen (so wie später beschrieben). All dies ist sehr hilfreich, wenn es um das Entwickeln von Computeralgorithmen und das Schreiben von Code zum Bearbeiten von einem oder mehreren Datasets geht, besonders, wenn Sie alle Zwischenergebnisse untersuchen möchten.

Als Beispiel erstellen die folgenden Schritte einen kleinen Code zum Erforschen des [Zentralen Grenzwertsatzes](https://en.wikipedia.org/wiki/Central_limit_theorem) (Wikipedia). (Dieses Beispiel ist aus dem *R Cookbook* von Paul Teetor abgeleitet.)

1. Geben Sie im `script.R`-Editor den folgenden Code ein:

    ```R
    mu <- 50
    stddev <- 1
    N <- 10000
    pop <- rnorm(N, mean = mu, sd = stddev)
    plot(density(pop), main = "Population Density", xlab = "X", ylab = "")
    ```

1. Um schnell Ergebnisse anzuzeigen, wählen Sie den gesamten Code aus (STRG+A), drücken Sie STRG+EINGABE, oder führen Sie einen Rechtsklick aus und wählen **Interaktiv ausführen** aus. Dadurch wird der ausgewählte Code in das interaktive Fenster eingefügt, so als hätten Sie ihn manuell eingegeben, und das Ergebnis wird in einem Plotfenster angezeigt.

    ![Darstellung eines Plots in Visual Studio](~/docs/rtvs/media/getting-started-08-plot1.png)

1. Für eine einzelne Zeile können Sie einfach jederzeit STRG+EINGABE drücken, um diese Zeile im interaktiven Fenster auszuführen.

> [!Tip]
> Lernen Sie die Muster kennen, mit denen Sie Bearbeitungen durchführen und STRG+EINGABE drücken (oder alles mit STRG+A auswählen und danach STRG+EINGABE drücken), um den Code schnell auszuführen. Das ist viel effizienter, als wenn Sie für denselben Vorgang die Maus verwenden.
> 
> Sie können zusätzlich das Plotfenster durch Drag & Drop aus dem Visual Studio-Rahmen nehmen und es beliebig auf Ihrem Bildschirm platzieren. Dadurch können Sie die Größe des Plotfensters einfach wie gewünscht ändern und es dann in einer Bild- oder PDF-Datei speichern.

1. Fügen Sie weitere Codezeilen hinzu, um einen zweiten Plot einzuschließen:

    ```R
    n <- 30
    samp.means <- rnorm(N, mean = mu, sd = stddev / sqrt(n))    
    lines(density(samp.means))
    ```

1. Drücken Sie erneut STRG+A und STRG+EINGABE, um den Code erneut auszuführen, um Folgendes zu erhalten:

    ![Aktualisierter dualer Plot in Visual Studio](~/docs/rtvs/media/getting-started-09-plot2.png)

1. Das Problem ist, dass der erste Plot die vertikale Skala bestimmt, weshalb der zweite Plot (mit `lines`) nicht passt. Sie müssen den `ylim`-Parameter auf dem `plot`-Aufruf festlegen, um dies zu korrigieren, aber Sie müssen für eine ordnungsgemäße Ausführung Code hinzufügen, um den maximalen vertikalen Wert zu berechnen. Dies Zeile für Zeile im interaktiven Fenster auszuführen, ist sehr umständlich, da Sie den Code neu anordnen müssen, um `samp.means` zu verwenden, bevor Sie `plot` aufrufen. In einer Codedatei können Sie jedoch einfach die geeigneten Bearbeitungen ausführen:

    ```R
    mu <- 50
    stddev <- 1
    N <- 10000
    pop <- rnorm(N, mean = mu, sd = stddev)

    n <- 30
    samp.means <- rnorm(N, mean = mu, sd = stddev / sqrt(n))
    max.samp.means <- max(density(samp.means)$y)

    plot(density(pop), main = "Population Density",
        ylim = c(0, max.samp.means),
        xlab = "X", ylab = "")
    lines(density(samp.means))
    ```

1. Drücken Sie wieder STRG+A und STRG+EINGABE, um das Ergebnis anzuzeigen:

    ![Aktualisierter dualer Plot in Visual Studio, richtig skaliert](~/docs/rtvs/media/getting-started-10-plot3.png)

Sie können noch viel mehr im Editor tun. Weitere Informationen finden Sei unter [Editing R code in Visual Studio (Bearbeiten von R-Code in Visual Studio)](code-editing.md), [IntelliSense](code-intellisense.md) und [Code snippets (Codeausschnitte)](code-snippets.md).

## <a name="debugging-your-code"></a>Debuggen von Code

Eine der größten Stärken von Visual Studio ist die Debugger-Benutzeroberfläche. RTVS ist auf dieser starken Grundlage aufgebaut und kommt mit einer innovativen Benutzeroberfläche wie z.B. dem [Variablen-Explorer und die Datentabellenanzeige](variable-explorer.md). Fangen Sie nun mit dem Debuggen an.

1. Um zu starten, setzen Sie den aktuellen Arbeitsbereich zurück, um alles, was Sie bisher gemacht haben, zu löschen. Hierzu verwenden Sie den Menübefehl **R Tools > Sitzung > Zurücksetzen**. Standardmäßig wird alles, was Sie im interaktiven Fenster tun, in die aktuelle Sitzung übertragen, die dann auch vom Debugger verwendet wird. Indem Sie die Sitzung zurücksetzen, stellen Sie sicher, dass Sie eine Debugsitzung ohne schon vorhandene Daten starten (falls Sie das möchten!). Beachten Sie, dass dies nicht Ihre `script.R`-Quelldatei beeinträchtigt, da diese außerhalb des Arbeitsbereichs verwaltet und gespeichert wird.

1. Mit der im vorherigen Abschnitt erstellten `script.R`-Datei legen Sie einen Haltepunkt auf der Zeile fest, die mit `pop <-` beginnt, indem Sie das Caretzeichen auf dieser Zeile platzieren und F9 drücken. Alternativ können Sie auch den Menübefehl **Debuggen > Haltepunkt ein/aus** auswählen. Sie können dies in einem Schritt durchführen, indem Sie in den linken Rand (oder den Bundsteg) für diese Zeile klicken, wo der rote Punkt erscheint, der den Haltepunkt anzeigt:

    ![Festlegen eines Haltepunkts im Editor](~/docs/rtvs/media/getting-started-11-debug1.png)

1. Starten Sie den Debugger mit dem Code in `script.R`, indem Sie entweder die Schaltfläche **Source startup file** (Quellstartdatei) auf der Symbolleiste verwenden, die Menüelemente **Debuggen > Source startup file** (Quellstartdatei) auswählen oder F5 drücken. Dadurch wird Visual Studio in den Debugmodus versetzt und beginnt damit, den Code auszuführen. Visual Studio hält jedoch auf der Zeile an, auf der Sie den Haltepunkt festgelegt haben.

    ![Anhalten am Haltepunkt im Visual Studio-Debugger](~/docs/rtvs/media/getting-started-12-debug2.png)

1. Während des Debuggens stellt Visual Studio die Funktion bereit, Zeile für Zeile durch den Code zu gehen, einschließlich der Möglichkeit, Funktionen zu durchlaufen, diese zu überspringen oder einen Rücksprung zum aufrufenden Kontext ausführen. Diese Funktionen können – zusammen mit anderen – im Menü **Debuggen** im Kontextmenü im Editor gefunden werden, das Sie mit einem Rechtsklick öffnen, sowie in der Symbolleiste „Debuggen“:

    ![Symbolleiste „Debuggen“ in Visual Studio](~/docs/rtvs/media/getting-started-13-debug3.png)

1. Wenn an einem Haltepunkt angehalten wird, können Sie die Werte von Variablen untersuchen. Finden Sie das **Auto**-Fenster in Visual Studio, und wählen Sie die Registerkarte am unteren Rand mit dem Namen **Locals** (Lokale) aus. Das Fenster **Locals** (Lokale) zeigt lokale Variablen im Programm zum aktuellen Zeitpunkt an. Wenn Sie am zuvor festgelegten Haltepunkt angehalten haben, sehen Sie, dass die `pop`-Variable noch nicht definiert ist. Verwenden Sie nun den Befehl **Debuggen > Prozedurschritt** (F10), und es erscheint der Wert für POP:

    ![Fenster „R-Hilfe“ in Visual Studio](~/docs/rtvs/media/getting-started-14-debug4.png)

1. Um Variablen in unterschiedlichen Bereichen zu untersuchen, einschließlich des globalen Bereichs und der Paketbereiche, können Sie den unten dargestellten [Variablen-Explorer](variable-explorer.md) verwenden. Mithilfe des Variablen-Explorers können Sie auch in eine Tabellenansicht mit sortierbaren Spalten wechseln und Daten in eine CSV-Datei exportieren.

    ![Erweiterte Ansicht des Variablen-Explorers](~/docs/rtvs/media/variable-explorer-expanded-results.png)

1. Sie können weiter das Programm Zeile für Zeile durchlaufen oder **Fortsetzen** (F5) auswählen, um es vollständig auszuführen (oder um zum nächsten Haltepunkt zu gelangen).

Ausführlichere Details finden Sie unter [Debugging](debugging.md) und [Variable Explorer (Variablen-Explorer)](variable-explorer.md).

## <a name="next-steps"></a>Nächste Schritte

In dieser exemplarischen Vorgehensweise haben Sie die Grundlagen von R-Projekten, die Verwendung des interaktiven Fensters, die Codebearbeitung und das Debuggen in Visual Studio kennengelernt. Um weitere Funktionen kennenzulernen, sehen Sie sich die folgenden Themen an sowie jene, die im Inhaltsverzeichnis aufgeführt sind:

- [Beispielprojekte](getting-started-samples.md)
- [Bearbeiten von Code](code-editing.md)
- [Debuggen](debugging.md)
- [Arbeitsbereiche](workspaces.md)
- [Visualisieren von Daten](visualizing-data.md)

