---
title: Debuggen von ASP.NET
description: Debuggen von ASP.NET mithilfe von Visual Studio-debugger
ms.custom: mvc
ms.date: 08/06/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 74671401b3e3eaeae5840110dfc37c926266f98a
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636986"
---
# <a name="quickstart-debug-aspnet-with-the-visual-studio-debugger"></a>Schnellstart: Debuggen von ASP.NET mit dem Visual Studio-debugger

Visual Studio-Debugger bietet viele leistungsstarke Features, damit Sie Ihre apps Debuggen können. In diesem Thema werden einige der grundlegenden Funktionen erläutert.

## <a name="create-a-new-project"></a>Erstellt ein neues Projekt 

1. Klicken Sie in Visual Studio auf **Datei > Neues Projekt**.

1. Klicken Sie unter **Visual C#-**, wählen Sie **Web**, und wählen Sie dann im mittleren Bereich **ASP.NET Core-Webanwendung**.

1. Geben Sie einen Namen wie **MyDbgApp** , und klicken Sie auf **OK**.

1. Wählen Sie im angezeigten Dialogfeld **Webanwendung** im mittleren Bereich, und klicken Sie dann auf **OK**.

     Wenn Sie nicht angezeigt wird der **Webanwendung** -Projektvorlage aus, klicken Sie auf die **Visual Studio-Installer öffnen** Link im linken Bereich des der **neues Projekt** Dialogfeld. Der Visual Studio-Installer wird gestartet. Klicken Sie auf die Workload **ASP.NET und Webentwicklung**, und klicken Sie anschließend auf **Ändern**.

    ![Wählen Sie eine Webanwendung](../debugger/media/dbg-qs-aspnet-choose-web-app.png)

    Visual Studio erstellt daraufhin das Projekt.

1. Klicken Sie im Projektmappen-Explorer öffnen Sie About.cshtml.cs (unter "Pages/About.cshtml), und Ersetzen Sie den folgenden code

    ```csharp
    public void OnGet()
    {
        Message = "Your application description page.";
    }
    ```

    durch den folgenden:

    ```csharp
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

Ein *Haltepunkt* ist der code eines Markers, der angibt, in denen Visual Studio die Ausführung angehalten werden soll, können Sie einen Blick auf die Werte von Variablen oder das Verhalten des Arbeitsspeichers oder angibt, ob eine Verzweigung des Codes ausführen erste nutzen. Es ist das grundlegendste Feature beim Debuggen.

1. Um den Haltepunkt festzulegen, klicken Sie auf den Bundsteg links neben der `doWork` Funktion (oder wählen Sie die Codezeile aus, und drücken Sie **F9**).

    ![Haltepunkt festlegen](../debugger/media/dbg-qs-set-breakpoint-aspnet.png)

    Der Haltepunkt festgelegt ist, auf der linken Seite von der öffnenden geschweiften Klammer (`{`).

1. Drücken Sie nun **F5** (oder wählen Sie **Debuggen > Debuggen starten**).

1. Wenn die Webseite geladen wird, klicken Sie auf die **zu** Link am oberen Rand der Webseite.

    Der Debugger hält, in dem Sie den Haltepunkt festgelegt, ist. Die Anweisung, in denen die Debugger und die app-Ausführung angehalten wird, wird durch den gelben Pfeil angegeben. Die Zeile mit der öffnenden geschweiften Klammer (`{`) nach der `doWork` Funktionsdeklaration wurde noch nicht ausgeführt.

    ![Treffen eines Haltepunkts](../debugger/media/dbg-qs-hit-breakpoint-aspnet.png)

    > [!TIP]
    > Wenn Sie einen in einer Schleife oder Rekursion Haltepunkt oder wenn Sie viele Haltepunkte, die Sie häufig verfügen schrittweise, Durchlaufen einer [bedingten Haltepunkt](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) um sicherzustellen, dass Ihr Code angehalten wird, nur, wenn bestimmte Bedingungen erfüllt sind. Dies spart Zeit und kann auch einfacher Debuggen von Problemen, die schwer reproduzierbar sind.

## <a name="navigate-code"></a>Navigieren durch den Code

Es gibt verschiedene Befehle anweisen des Debuggers zum fortfahren. Wir zeigen es sich um einen nützlichen Code Navigationsbefehl die neuen Visual Studio 2017.

Während die Ausführung am Haltepunkt angehalten wird, zeigen Sie die Anweisung `return c2` bis Grün **Ausführung bis Klick** Schaltfläche ![Ausführung bis Klick](../debugger/media/dbg-tour-run-to-click.png) angezeigt wird, und drücken Sie dann die **Ausführung bis Klick** Schaltfläche ".

![Ausführung bis Klick](../debugger/media/dbg-qs-run-to-click-aspnet.png)

Die app wird die Ausführung fortgesetzt, und hält auf die Codezeile, in dem Sie die Schaltfläche geklickt.

Allgemeine Tastenkombinationen, die zum Einschließen von Code schrittweise durchlaufen **F10** und **F11**. Weitere ausführlichen Anweisungen finden Sie in der [Handbuch für Anfänger](../debugger/getting-started-with-the-debugger.md).

## <a name="inspect-variables-in-a-datatip"></a>Überprüfen von Variablen in einem datatip

1. In der aktuellen Zeile des Codes (gekennzeichnet durch die gelbe Ausführungszeiger), zeigen Sie auf die `c2` Objekt mit der Maus auf einen Datatip angezeigt.

    ![Einen Datatip anzeigen](../debugger/media/dbg-qs-data-tip-aspnet.png)

    Der Datatip erfahren Sie, den aktuellen Wert des der `c2` Variablen und ermöglicht Ihnen, ihre Eigenschaften zu überprüfen. Beim Debuggen, wenn einen Wert angezeigt wird, die, den Sie nicht erwarten, müssen Sie wahrscheinlich einen Fehler in den vorhergehenden oder die aufrufenden Codezeilen. 

2. Erweitern Sie den Datatip Betrachten der aktuellen Eigenschaftswerte für die `c2` Objekt.

3. Sollten Sie den Datatip anzuheften, damit Sie fortfahren können, um den Wert der anzuzeigen `c2` während Sie Code ausführen, klicken Sie auf das kleine Pinsymbol. (Sie können den angehefteten Datatip an einem geeigneten Speicherort verschieben.)

## <a name="edit-code-and-continue-debugging"></a>Bearbeiten von Code und Fortsetzen des Debuggens

Wenn Sie eine Änderung, die Sie in Ihrem Code während einer Debugsitzung testen möchten identifizieren, können Sie dies, zu tun.

1. In der `OnGet` -Methode, klicken Sie auf der zweiten Instanz von `result.First.Value` , und ändern Sie `result.First.Value` zu `result.Last.Value`.

1. Drücken Sie **F10** (oder **Debuggen > Prozedurschritt**) mehrmals fahren fort, um den Debugger, und führen Sie den bearbeiteten Code.

    ![Bearbeiten und Fortfahren](../debugger/media/dbg-qs-edit-and-continue-aspnet.png "bearbeiten und fortfahren")

    **F10** wechselt die eine Debuggeranweisung auf eine Zeit, doch die Schritte für Funktionen, anstatt den Einzelschritt in diese (der Code, den Sie überspringen, immer noch ausgeführt).

Weitere Informationen zur Verwendung von bearbeiten und fortfahren und Einschränkungen für Funktionen, finden Sie unter [bearbeiten und Fortfahren](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie gelernt, starten Sie den Debugger, Code durchlaufen und untersuchen Sie Variablen. Sie sollten einen allgemeinen Überblick über die Debugger-Features sowie Links zu weiteren Informationen zu erhalten.

> [!div class="nextstepaction"]
> [Debugger – Featuretour](../debugger/debugger-feature-tour.md)
