---
title: Debuggen mit C++
description: Debuggen von nativem Code mithilfe des Visual Studio-Debuggers
ms.custom: mvc
ms.date: 08/06/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: 639e430b-6d2d-46bd-b738-8c60dfb384f1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 33d96729507e0e85318ee357240580d3f3a1c328
ms.sourcegitcommit: 35bebf794f528d73d82602e096fd97d7b8f82c25
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2018
ms.locfileid: "53561761"
---
# <a name="quickstart-debug-with-c-using-the-visual-studio-debugger"></a>Schnellstart: Debuggen mit C++ mithilfe des Visual Studio-Debuggers

Der Visual Studio-Debugger umfasst viele nützliche Features zum Debuggen von Apps. In diesem Thema werden einige der grundlegenden Funktionen erläutert.

## <a name="create-a-new-project"></a>Erstellt ein neues Projekt 

1. Klicken Sie in Visual Studio auf **Datei > Neues Projekt**.

2. Klicken Sie unter **Visual C++** auf **Windows-Desktop** und dann im mittleren Bereich auf **Windows-Konsolenanwendung**.

    Wenn Ihnen die Projektvorlage **Windows-Konsolenanwendung** nicht angezeigt wird, klicken Sie im linken Bereich des Dialogfelds **Neues Projekt** auf den Link **Visual Studio-Installer öffnen**. Der Visual Studio-Installer wird gestartet. Wählen Sie die Workload **Desktopentwicklung mit C++**, und klicken Sie dann auf **Ändern**.

3. Geben Sie einen Namen wie **MyDbgApp** ein, und klicken Sie auf **OK**.

    Visual Studio erstellt daraufhin das Projekt.

4. Ersetzen Sie in „MyDbgApp.cpp“ den folgenden Code

    ```c++
    int main()
    {
        return 0;
    }
    ```

    durch den folgenden (`#include "stdafx.h"` nicht entfernen):

    ```c++
    #include <list>  
    #include <iostream>

    using namespace std;

    void doWork()
    {
        list <int> c1;

        c1.push_back(10);
        c1.push_back(20);

        const list <int> c2 = c1;
        const int &i = c2.front();
        const int &j = c2.front();
        cout << "The first element is " << i << endl;
        cout << "The second element is " << j << endl;

    }

    int main()
    {
        doWork();
    }
    ```

## <a name="set-a-breakpoint"></a>Haltepunkt festlegen

Ein *Breakpoint* gibt an, an welcher Stelle Visual Studio ausgeführten Code anhalten soll. So können Sie einen Blick auf die Werte von Variablen oder das Speicherverhalten werfen oder überprüfen, ob eine Verzweigung im Code ausgeführt wird. Es handelt sich dabei um ein grundlegendes Debugfeature.

1. Wenn Sie einen Breakpoint festlegen möchten, klicken Sie im Bundsteg auf den Bereich links neben dem Funktionsaufruf `doWork`. Alternativ können Sie aber auch die Codezeile auswählen und **F9** drücken.

    ![Breakpoint festlegen](../debugger/media/dbg-qs-set-breakpoint.png "Set a breakpoint")

2. Drücken Sie dann **F5**, oder klicken Sie auf **Debuggen > Debuggen starten**.

    ![Breakpoint treffen](../debugger/media/dbg-qs-hit-breakpoint.png "Hit a breakpoint")

    Der Debugger hält an dem Breakpoint an, den Sie festlegen. Der gelbe Pfeil deutet auf die Anweisung, bei der der Debugger und die App-Ausführung ausgesetzt werden. Die Zeile mit dem Funktionsaufruf `doWork` wurde noch nicht ausgeführt.

    > [!TIP]
    > Verwenden Sie bei Breakpoints in einer Schleife oder Rekursion oder bei sehr vielen Breakpoints, die Sie häufig schrittweise durchlaufen, einen [bedingten Breakpoint](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression), damit die Codeausführung NUR unterbrochen wird, wenn bestimmte Bedingungen erfüllt sind. Wenn Sie mit einem bedingten Breakpoint arbeiten, sparen Sie Zeit und erleichtern sich möglicherweise das Debuggen von Problemen, die nur schwierig zu reproduzieren sind.

    Wenn Sie versuchen, in C++ Fehler zu debuggen, die im Zusammenhang mit dem Arbeitsspeicher stehen, können Sie Breakpoints auch dazu verwenden, Adresswerte (suchen Sie nach NULL-Werten) und die Anzahl von Verweisen zu untersuchen. 

## <a name="navigate-code"></a>Navigieren durch den Code

Es gibt verschiedene Befehle, über die der Debugger zum Fortfahren angewiesen werden kann. In diesem Artikel wird ein nützlicher Befehl zur Codenavigation erläutert, der neu für Visual Studio 2017 ist.

Wenn der Vorgang am Breakpoint ausgesetzt wurde, zeigen Sie auf die Anweisung `c1.push_back(20)`, bis die Schaltfläche **Run to click** (Ausführen bis Klick) ![Ausführen bis Klick](../debugger/media/dbg-tour-run-to-click.png "Run to Click") angezeigt wird, und klicken Sie diese an.

![Ausführen bis Klick](../debugger/media/dbg-qs-run-to-click.png "Run to Click")

Dann wird die App weiter ausgeführt, ruft `doWork` auf, und wird bei der Codezeile ausgesetzt, bei der Sie die Schaltfläche angeklickt haben.

Häufig werden die Tastaturbefehle **F10** und **F11** verwendet, um Code durchzugehen. Weitere ausführliche Anweisungen finden Sie unter [Ein erster Blick auf den Visual Studio-Debugger](../debugger/debugger-feature-tour.md).

## <a name="inspect-variables-in-a-datatip"></a>Untersuchen von Variablen in einem Datentipp

1. Zeigen Sie in der aktuellen Codezeile (zu erkennen an dem Ausführungszeiger in gelb) mit der Maus auf das `c1`-Objekt, um Datentipps anzuzeigen.

    ![Datentipp anzeigen](../debugger/media/dbg-qs-data-tip.png "View a datatip")

    Der aktuelle Wert der Variable `c1` wird angezeigt, und Sie können die Eigenschaften untersuchen. Wenn Sie beim Debuggen einen nicht erwarteten Wert antreffen, enthalten die vorhergehenden oder die aufrufenden Codezeilen möglicherweise einen Fehler. 

2. Erweitern Sie den Datentipp, um die Eigenschaftswerte des `c1`-Objekts einzusehen.

3. Wenn Sie den Datentipp anheften möchten, damit bei der Codeausführung weiterhin der Wert von `c1` angezeigt wird, klicken Sie auf das Stecknadelsymbol. (Sie können den angehefteten Datentipp an eine geeignete Stelle verschieben.)

## <a name="edit-code-and-continue-debugging"></a>Bearbeiten von Code und Fortsetzen des Debuggens

Wenn Sie in einer Debugsitzung eine Änderung feststellen, die Sie in Ihrem Code testen möchten, ist dies auch kein Problem.

1. Klicken Sie auf die zweite Instanz von `c2.front()`, und ändern Sie `c2.front()` in `c2.back()`.

2. Drücken Sie wiederholt **F10** (oder klicken Sie auf **Debuggen > Prozedurschritt**), um den Debugger fortzusetzen und den bearbeiteten Code auszuführen.

    ![Bearbeiten und fortfahren](../debugger/media/dbg-qs-edit-and-continue.gif "Edit and continue")

    Wenn Sie **F10** drücken, führt der Debugger jeweils nur eine Anweisung aus, überspringt Funktionen aber, anstatt diese schrittweise auszuführen (der Code, den Sie überspringen, wird weiter ausgeführt).

Weitere Informationen zum Bearbeiten und Fortfahren und zu Einschränkungen von Features finden Sie unter [Edit and Continue (Bearbeiten und Fortfahren)](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie gelernt, wie Sie den Debugger starten, Code schrittweise durchlaufen und Variablen untersuchen. Sie sollten sich einen allgemeinen Überblick über die Debugger-Features verschaffen und die zugehörigen Links aufrufen, um weitere Informationen hierzu zu erhalten.

> [!div class="nextstepaction"]
> [Debugger – Featuretour](../debugger/debugger-feature-tour.md)
