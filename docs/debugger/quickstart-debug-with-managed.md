---
title: Debuggen des verwalteten Codes | Microsoft Docs
description: Debuggen von c# oder Visual Basic mit dem Visual Studio-debugger
ms.custom: mvc
ms.date: 03/18/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 4dc9c9acfed229e4215c32e2e924ba1601ce88b6
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2018
ms.locfileid: "34476881"
---
# <a name="quickstart-debug-with-managed-code-using-the-visual-studio-debugger"></a>Schnellstart: Debuggen Sie mit verwaltetem Code mithilfe von Visual Studio-debugger

Der Visual Studio-Debugger bietet viele leistungsstarke Funktionen zum Debuggen von apps zu erleichtern. In diesem Thema werden einige der grundlegenden Funktionen erläutert.

## <a name="create-a-new-project"></a>Erstellt ein neues Projekt 

1. Klicken Sie in Visual Studio auf **Datei > Neues Projekt**.

2. Klicken Sie unter **Visual C#-** oder **Visual Basic**, wählen Sie **.NET Core**, und wählen Sie dann im mittleren Bereich **Konsolen-App (.NET Core)**.

     Falls Sie die Projektvorlage **Konsolenanwendung (.NET Core)** nicht finden, klicken Sie auf den Link **Visual Studio-Installer öffnen** auf der linken Seite des Dialogfelds **Neues Projekt**. Der Visual Studio-Installer wird gestartet. Wählen Sie die **.NET Desktopentwicklung** und **.NET Core** arbeitsauslastung, wählen Sie dann **ändern**.

3. Geben Sie einen Namen wie **MyDbgApp** , und klicken Sie auf **OK**.

    Visual Studio erstellt daraufhin das Projekt.

4. Ersetzen Sie den folgenden Code in "Program.cs" oder "Module1.vb"

    ```csharp
    class Program
    {
        static void Main(string[] args)
        {
        }
    }
    ```

    ```vb
    Module Module1
        Sub Main()
        End Sub
    End Module
    ```

    durch den folgenden:

    ```csharp
    class Program
    {
        private static void doWork()
        {
            LinkedList<int> c1 = new LinkedList<int>();

            c1.AddLast(10);
            c1.AddLast(20);

            LinkedList<int> c2 = new LinkedList<int>(c1);
            int i = c2.First.Value;
            int j = c2.First.Value;
            Console.Write("The first element is ");
            Console.Write(i);
            Console.Write("\n");
            Console.Write("The second element is ");
            Console.Write(j);
            Console.Write("\n");

        }

        static int Main()
        {
            // using namespace std;
            doWork();
            return 0;

        }
    }
    ```

    ```vb
    Imports System.Collections.Generic

    Namespace MyDbgApp
        Class Program
            Private Shared Sub doWork()
                Dim c1 As New LinkedList(Of Integer)()

                c1.AddLast(10)
                c1.AddLast(20)

                Dim c2 As New LinkedList(Of Integer)(c1)
                Dim i As Integer = c2.First.Value
                Dim j As Integer = c2.First.Value
                Console.Write("The first element is ")
                Console.Write(i)
                Console.Write(vbLf)
                Console.Write("The second element is ")
                Console.Write(j)
                Console.Write(vbLf)

            End Sub

            Public Shared Function Main() As Integer
                ' using namespace std;
                doWork()
                Return 0

            End Function
        End Class
    End Namespace
    ```

    > [!NOTE]
    > Stellen Sie in Visual Basic sicher, dass das Startobjekt auf `Sub Main` festgelegt ist (**Eigenschaften > Anwendung > Startobjekt**).

## <a name="set-a-breakpoint"></a>Haltepunkt festlegen

Ein *Haltepunkt* ist der code eines Markers, der angibt, wo Visual Studio die Ausführung angehalten werden soll, so dass Sie einen Blick auf die Werte von Variablen oder das Verhalten der Arbeitsspeicher, ob eine Verzweigung des Codes Speicherverhalten oder ausgeführt wird. Es ist die grundlegendste Funktion Debuggen.

1. Um den Haltepunkt festzulegen, klicken Sie im Bundsteg auf der linken Seite des auf der `doWork` Funktionsaufruf (oder wählen Sie die Zeile des Codes, und drücken Sie **F9**).

    ![Festlegen eines Haltepunkts](../debugger/media/dbg-qs-set-breakpoint-csharp.png "Festlegen eines Haltepunkts")

2. Drücken Sie jetzt **F5** (oder wählen Sie **Debuggen > Debuggen starten**).

    ![Einen Haltepunkt erreicht](../debugger/media/dbg-qs-hit-breakpoint-csharp.png "eines Haltepunkts")

    Der Debugger hält, wo Sie den Haltepunkt festlegen. Die Anweisung, in denen die Debugger und die app die Ausführung angehalten wird, wird durch den gelben Pfeil angegeben. Die Zeile mit der `doWork` Funktionsaufruf wurde noch nicht noch ausgeführt.

    > [!TIP]
    > Wenn Sie einen in einer Schleife oder Rekursion Haltepunkt oder wenn Sie viele Haltepunkte, die Sie häufig, Durchlaufen einer [bedingter Haltepunkt](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) um sicherzustellen, dass Ihr Code angehalten wird, nur, wenn bestimmte Bedingungen erfüllt sind. Ein bedingter Haltepunkt kann Zeit sparen, und es kann auch einfacher Debuggen von Problemen, die schwer reproduzierbar sind.

## <a name="navigate-code"></a>Navigieren durch den Code

Es gibt verschiedene Befehle zum anweisen des Debuggers zum fortfahren. Wir zeigen einen nützlichen Code Navigation-Befehl, der in Visual Studio 2017 neu ist.

Während am Haltepunkt angehalten wird, zeigen Sie auf die Anweisung `c1.AddLast(20)` bis über die grüne **ausführen, klicken Sie auf** Schaltfläche ![ausführen, klicken Sie auf](../debugger/media/dbg-tour-run-to-click.png "RunToClick") angezeigt wird, und drücken Sie dann die **Ausführen, klicken Sie auf** Schaltfläche.

![Führen Sie auf](../debugger/media/dbg-qs-run-to-click-csharp.png "ausführen, klicken Sie auf")

Die Anwendung setzt die Ausführung, Aufrufen von `doWork`, und hält Sie auf die Codezeile, in dem Sie die Schaltfläche geklickt haben.

Allgemeine Tastenkombinationen Befehle verwendet, um den Code schrittweise durchlaufen enthalten **F10** und **F11**. Weitere ausführlichen Anweisungen finden Sie in der [Einsteigerhandbuch](../debugger/getting-started-with-the-debugger.md).

## <a name="inspect-variables-in-a-datatip"></a>Prüfen Sie die Variablen in einem datatip

1. In der aktuellen Zeile des Codes (gekennzeichnet durch den gelben Ausführungszeiger), zeigen Sie auf die `c1` Objekt mit der Maus auf einen Datatip angezeigt.

    ![Anzeigen von einem Datatip](../debugger/media/dbg-qs-data-tip-csharp.png "einen Datatip anzeigen")

    Der Datatip zeigt den aktuellen Wert der `c1` Variablen und ermöglicht es Ihnen, ihre Eigenschaften zu überprüfen. Beim Debuggen, wenn einen Wert angezeigt wird, die, den Sie nicht erwarten, müssen Sie wahrscheinlich einen Fehler in der vorhergehenden oder die aufrufenden Codezeilen. 

2. Erweitern Sie den Datatip betrachten Sie die aktuellen Eigenschaftswerte die `c1` Objekt.

3. Wenn Sie möchten den Datatip anzuheften, sodass fortgesetzt werden kann, um den Wert der anzuzeigen `c1` während Sie Code ausführen, klicken Sie auf das kleine Nadel-Symbol. (Sie können den angehefteten Datatip an einem geeigneten Speicherort verschieben.)

## <a name="edit-code-and-continue-debugging"></a>Bearbeiten Sie Code und fortfahren Sie, Debuggen

Wenn Sie eine Änderung, die Sie in Ihrem Code mitten in einer Debugsitzung testen möchten identifizieren, können Sie dies, zu tun.

1. Klicken Sie auf der zweiten Instanz von `c2.First.Value` , und ändern Sie `c2.First.Value` auf `c2.Last.Value`.

2. Drücken Sie **F10** (oder **Debuggen > Prozedurschritt**) wenige Male auf, um den Debugger zu gelangen, und führen Sie den bearbeiteten Code.

    ![Bearbeiten und Fortfahren](../debugger/media/dbg-qs-edit-and-continue-csharp.gif "bearbeiten und fortfahren")

    **F10** wechselt die eine Debuggeranweisung auf eine Zeit, doch Schritte über Funktionen, die nicht im Einzelschritt sie (der Code, die Sie überspringen noch ausgeführt) zu.

Weitere Informationen zur Verwendung von bearbeiten und fortfahren und funktionseinschränkungen finden Sie unter [bearbeiten und Fortfahren](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Nächste Schritte

In diesem Lernprogramm haben Sie gelernt, starten Sie den Debugger, Code durchlaufen und Variablen überprüfen. Sie möchten eine allgemeine Beschreibung zur Debuggerfunktionen zusammen mit Links zu weiteren Informationen zu erhalten.

> [!div class="nextstepaction"]
> [Debugger – Featuretour](../debugger/debugger-feature-tour.md)
