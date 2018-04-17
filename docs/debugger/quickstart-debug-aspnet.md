---
title: Debuggen von ASP.NET - Visual Studio | Microsoft Docs
ms.custom: mvc
ms.date: 03/16/2018
ms.technology:
- vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 27072fda7535db5cd7307523c7e1732fef79c9e2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="debug-aspnet-with-the-visual-studio-debugger"></a>Debuggen von ASP.NET mit Visual Studio-debugger

Der Visual Studio-Debugger bietet viele leistungsstarke Funktionen zum Debuggen von apps zu erleichtern. In diesem Thema werden einige der grundlegenden Funktionen erläutert.

## <a name="create-a-new-project"></a>Erstellt ein neues Projekt 

1. Klicken Sie in Visual Studio auf **Datei > Neues Projekt**.

1. Klicken Sie unter **Visual C#-**, wählen Sie **Web**, und wählen Sie dann im mittleren Bereich **ASP.NET-Webanwendung für Core**.

1. Geben Sie einen Namen wie **MyDbgApp** , und klicken Sie auf **OK**.

1. Wählen Sie im angezeigten Dialogfeld **Webanwendung** im mittleren Bereich, und klicken Sie dann auf **OK**.

     Wenn Sie sehen die **Webanwendung** -Projektvorlage aus, klicken Sie auf die **Installer für Visual Studio öffnen** Link im linken Bereich des der **neues Projekt** (Dialogfeld). Der Visual Studio-Installer wird gestartet. Wählen Sie die **ASP.NET** und **.NET Core** arbeitsauslastung, wählen Sie dann **ändern**.

    ![Wählen Sie eine Webanwendung](../debugger/media/dbg-qs-aspnet-choose-web-app.png)

    Visual Studio erstellt daraufhin das Projekt.

1. Klicken Sie im Projektmappen-Explorer öffnen Sie About.cshtml.cs (unter Pages/About.cshtml), und Ersetzen Sie den folgenden code

    ```c#
    public void OnGet()
    {
        Message = "Your application description page.";
    }
    ```

    durch den folgenden:

    ```c#
    public void OnGet()
    {
        LinkedList<int> result = doWork();
        Message = "Result of work: " + result.First.Value + ", " + result.First.Value;
    }

    private static LinkedList<int> doWork()
    {
        LinkedList<int> c1 = new LinkedList<int>();

        c1.AddLast(10);
        c1.AddLast(20);

        LinkedList<int> c2 = new LinkedList<int>(c1);

        return c2;

    }
    ```

## <a name="set-a-breakpoint"></a>Haltepunkt festlegen

Ein *Haltepunkt* ist der code eines Markers, der angibt, wo Visual Studio die Ausführung angehalten werden soll, so dass Sie einen Blick auf die Werte von Variablen oder das Verhalten der Arbeitsspeicher, ob eine Verzweigung des Codes Speicherverhalten oder ausgeführt wird. Es ist die grundlegendste Funktion Debuggen.

1. Um den Haltepunkt festzulegen, klicken Sie im Bundsteg auf der linken Seite des auf der `doWork` Funktion (oder wählen Sie die Zeile des Codes, und drücken Sie **F9**).

    ![Haltepunkt festlegen](../debugger/media/dbg-qs-set-breakpoint-aspnet.png)

    Der Haltepunkt festgelegt ist, auf der linken Seite der öffnenden Klammer (`{`).

1. Drücken Sie jetzt **F5** (oder wählen Sie **Debuggen > Debuggen starten**).

1. Wenn die Webseite geladen wird, klicken Sie auf die **zu** Link am oberen Rand der Webseite.

    Der Debugger hält, wo Sie den Haltepunkt festlegen. Die Anweisung, in denen die Debugger und die app die Ausführung angehalten wird, wird durch den gelben Pfeil angegeben. Die Zeile mit der öffnenden geschweiften Klammer (`{`) nach der `doWork` Funktionsdeklaration noch nicht ausgeführt.

    ![Treffen eines Haltepunkts](../debugger/media/dbg-qs-hit-breakpoint-aspnet.png)

    > [!TIP]
    > Wenn Sie einen in einer Schleife oder Rekursion Haltepunkt oder wenn Sie viele Haltepunkte, die Sie häufig, Durchlaufen einer [bedingter Haltepunkt](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) um sicherzustellen, dass Ihr Code angehalten wird, nur, wenn bestimmte Bedingungen erfüllt sind. Dies spart Zeit und kann auch einfacher Debuggen von Problemen, die schwer reproduzierbar sind.

## <a name="navigate-code"></a>Navigieren durch den Code

Es gibt verschiedene Befehle zum anweisen des Debuggers zum fortfahren. Wir zeigen einen nützlichen Code Navigation-Befehl, der in Visual Studio 2017 neu ist.

Während am Haltepunkt angehalten wird, zeigen Sie auf die Anweisung `return c2` bis über die grüne **ausführen, klicken Sie auf** Schaltfläche ![ausführen, klicken Sie auf](../debugger/media/dbg-tour-run-to-click.png) angezeigt wird, und drücken Sie dann die **ausführen, klicken Sie auf** Schaltfläche ".

![Klicken Sie auf Ausführen](../debugger/media/dbg-qs-run-to-click-aspnet.png)

Die app wird die Ausführung fortgesetzt, und hält auf die Codezeile, in dem Sie die Schaltfläche geklickt haben.

Allgemeine Tastenkombinationen Befehle verwendet, um den Code schrittweise durchlaufen enthalten **F10** und **F11**. Weitere ausführlichen Anweisungen finden Sie in der [Einsteigerhandbuch](../debugger/getting-started-with-the-debugger.md).

## <a name="inspect-variables-in-a-datatip"></a>Prüfen Sie die Variablen in einem datatip

1. In der aktuellen Zeile des Codes (gekennzeichnet durch den gelben Ausführungszeiger), zeigen Sie auf die `c2` Objekt mit der Maus auf einen Datatip angezeigt.

    ![Einen Datatip anzeigen](../debugger/media/dbg-qs-data-tip-aspnet.png)

    Der Datatip zeigt den aktuellen Wert der `c2` Variablen und ermöglicht es Ihnen, ihre Eigenschaften zu überprüfen. Beim Debuggen, wenn einen Wert angezeigt wird, die, den Sie nicht erwarten, müssen Sie wahrscheinlich einen Fehler in der vorhergehenden oder die aufrufenden Codezeilen. 

2. Erweitern Sie den Datatip betrachten Sie die aktuellen Eigenschaftswerte die `c2` Objekt.

3. Wenn Sie möchten den Datatip anzuheften, sodass fortgesetzt werden kann, um den Wert der anzuzeigen `c2` während Sie Code ausführen, klicken Sie auf das kleine Nadel-Symbol. (Sie können den angehefteten Datatip an einem geeigneten Speicherort verschieben.)

## <a name="edit-code-and-continue-debugging"></a>Bearbeiten Sie Code und fortfahren Sie, Debuggen

Wenn Sie eine Änderung, die Sie in Ihrem Code mitten in einer Debugsitzung testen möchten identifizieren, können Sie dies, zu tun.

1. In der `OnGet` -Methode, klicken Sie auf der zweiten Instanz von `result.First.Value` , und ändern Sie `result.First.Value` auf `result.Last.Value`.

1. Drücken Sie **F10** (oder **Debuggen > Prozedurschritt**) wenige Male auf, um den Debugger zu gelangen, und führen Sie den bearbeiteten Code.

    ![Bearbeiten und Fortfahren](../debugger/media/dbg-qs-edit-and-continue-aspnet.png "bearbeiten und fortfahren")

    **F10** wechselt die eine Debuggeranweisung auf eine Zeit, doch Schritte über Funktionen, die nicht im Einzelschritt sie (der Code, die Sie überspringen noch ausgeführt) zu.

Weitere Informationen zur Verwendung von bearbeiten und fortfahren und funktionseinschränkungen finden Sie unter [bearbeiten und Fortfahren](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Nächste Schritte

In diesem Lernprogramm haben Sie gelernt, starten Sie den Debugger, Code durchlaufen und Variablen überprüfen. Sie möchten eine allgemeine Beschreibung zur Debuggerfunktionen zusammen mit Links zu weiteren Informationen zu erhalten.

> [!div class="nextstepaction"]
> [Debugger – Featuretour](../debugger/debugger-feature-tour.md)
