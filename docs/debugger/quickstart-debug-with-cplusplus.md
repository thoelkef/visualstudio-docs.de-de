---
title: Debuggen mit C++, Visual Studio-Debugger mit | Microsoft Docs
ms.custom: 
ms.date: 03/18/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: 639e430b-6d2d-46bd-b738-8c60dfb384f1
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fce20f8c17b52b109b469bd439905e0edd66c9d3
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2018
---
# <a name="debug-with-c-using-the-visual-studio-debugger"></a>Debuggen Sie mit C++, die mit dem Visual Studio-debugger

Der Visual Studio-Debugger bietet viele leistungsstarke Funktionen zum Debuggen von apps zu erleichtern. In diesem Thema werden einige der grundlegenden Funktionen erläutert.

## <a name="create-a-new-project"></a>Erstellt ein neues Projekt 

1. Klicken Sie in Visual Studio auf **Datei > Neues Projekt**.

2. Klicken Sie unter **Visual C++** auf **Windows-Desktop** und dann im mittleren Bereich auf **Windows-Konsolenanwendung**.

    Wenn Sie sehen die **Windows-Konsolenanwendung** -Projektvorlage aus, klicken Sie auf die **Installer für Visual Studio öffnen** Link im linken Bereich des der **neues Projekt** (Dialogfeld). Der Visual Studio-Installer wird gestartet. Wählen Sie die **Desktopentwicklung mit C++** arbeitsauslastung, wählen Sie dann **ändern**.

3. Geben Sie einen Namen wie **MyDbgApp** , und klicken Sie auf **OK**.

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

Ein *Haltepunkt* ist der code eines Markers, der angibt, wo Visual Studio die Ausführung angehalten werden soll, so dass Sie einen Blick auf die Werte von Variablen oder das Verhalten der Arbeitsspeicher, ob eine Verzweigung des Codes Speicherverhalten oder ausgeführt wird. Es ist die grundlegendste Funktion Debuggen.

1. Um den Haltepunkt festzulegen, klicken Sie im Bundsteg auf der linken Seite des auf der `doWork` Funktionsaufruf (oder wählen Sie die Zeile des Codes, und drücken Sie **F9**).

    ![Festlegen eines Haltepunkts](../debugger/media/dbg-qs-set-breakpoint.png "Festlegen eines Haltepunkts")

2. Drücken Sie jetzt **F5** (oder wählen Sie **Debuggen > Debuggen starten**).

    ![Einen Haltepunkt erreicht](../debugger/media/dbg-qs-hit-breakpoint.png "eines Haltepunkts")

    Der Debugger hält, wo Sie den Haltepunkt festlegen. Die Anweisung, in denen die Debugger und die app die Ausführung angehalten wird, wird durch den gelben Pfeil angegeben. Die Zeile mit der `doWork` Funktionsaufruf noch nicht ausgeführt.

    > [!TIP]
    > Wenn Sie einen in einer Schleife oder Rekursion Haltepunkt oder wenn Sie viele Haltepunkte, die Sie häufig, Durchlaufen einer [bedingter Haltepunkt](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) um sicherzustellen, dass Ihr Code angehalten wird, nur, wenn bestimmte Bedingungen erfüllt sind. Ein bedingter Haltepunkt spart Zeit und kann auch einfacher Debuggen von Problemen, die schwer reproduzierbar sind.

    Beim Debuggen von speicherbezogenen Fehler in C++ können Sie Haltepunkte auch verwenden, um Adresswerte (Suche nach NULL) zu überprüfen und zählt verweisen. 

## <a name="navigate-code"></a>Navigieren durch den Code

Es gibt verschiedene Befehle zum anweisen des Debuggers zum fortfahren. Wir zeigen einen nützlichen Code Navigation-Befehl, der in Visual Studio 2017 neu ist.

Während am Haltepunkt angehalten wird, zeigen Sie auf die Anweisung `c1.push_back(20)` bis über die grüne **ausführen, klicken Sie auf** Schaltfläche ![ausführen, klicken Sie auf](../debugger/media/dbg-tour-run-to-click.png "RunToClick") angezeigt wird, und drücken Sie dann die **Ausführen, klicken Sie auf** Schaltfläche.

![Führen Sie auf](../debugger/media/dbg-qs-run-to-click.png "ausführen, klicken Sie auf")

Die Anwendung setzt die Ausführung, Aufrufen von `doWork`, und hält Sie auf die Codezeile, in dem Sie die Schaltfläche geklickt haben.

Allgemeine Tastenkombinationen Befehle verwendet, um den Code schrittweise durchlaufen enthalten **F10** und **F11**. Weitere ausführlichen Anweisungen finden Sie in der [Einsteigerhandbuch](../debugger/getting-started-with-the-debugger.md).

## <a name="inspect-variables-in-a-datatip"></a>Prüfen Sie die Variablen in einem datatip

1. In der aktuellen Zeile des Codes (gekennzeichnet durch den gelben Ausführungszeiger), zeigen Sie auf die `c1` Objekt mit der Maus auf einen Datatip angezeigt.

    ![Anzeigen von einem Datatip](../debugger/media/dbg-qs-data-tip.png "einen Datatip anzeigen")

    Der Datatip zeigt den aktuellen Wert der `c1` Variablen und ermöglicht es Ihnen, ihre Eigenschaften zu überprüfen. Beim Debuggen, wenn einen Wert angezeigt wird, die, den Sie nicht erwarten, müssen Sie wahrscheinlich einen Fehler in der vorhergehenden oder die aufrufenden Codezeilen. 

2. Erweitern Sie den Datatip betrachten Sie die aktuellen Eigenschaftswerte die `c1` Objekt.

3. Wenn Sie möchten den Datatip anzuheften, sodass fortgesetzt werden kann, um den Wert der anzuzeigen `c1` während Sie Code ausführen, klicken Sie auf das kleine Nadel-Symbol. (Sie können den angehefteten Datatip an einem geeigneten Speicherort verschieben.)

## <a name="edit-code-and-continue-debugging"></a>Bearbeiten Sie Code und fortfahren Sie, Debuggen

Wenn Sie eine Änderung, die Sie in Ihrem Code mitten in einer Debugsitzung testen möchten identifizieren, können Sie dies, zu tun.

1. Klicken Sie auf der zweiten Instanz von `c2.front()` , und ändern Sie `c2.front()` auf `c2.back()`.

2. Drücken Sie **F10** (oder **Debuggen > Prozedurschritt**) wenige Male auf, um den Debugger zu gelangen, und führen Sie den bearbeiteten Code.

    ![Bearbeiten und Fortfahren](../debugger/media/dbg-qs-edit-and-continue.gif "bearbeiten und fortfahren")

    **F10** wechselt die eine Debuggeranweisung auf eine Zeit, doch Schritte über Funktionen, die nicht im Einzelschritt sie (der Code, die Sie überspringen noch ausgeführt) zu.

Weitere Informationen zur Verwendung von bearbeiten und fortfahren und funktionseinschränkungen finden Sie unter [bearbeiten und Fortfahren](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Nächste Schritte

In diesem Lernprogramm haben Sie gelernt, starten Sie den Debugger, Code durchlaufen und Variablen überprüfen. Sie möchten eine allgemeine Beschreibung zur Debuggerfunktionen zusammen mit Links zu weiteren Informationen zu erhalten.

> [!div class="nextstepaction"]
> [Debugger – Featuretour](../debugger/debugger-feature-tour.md)
