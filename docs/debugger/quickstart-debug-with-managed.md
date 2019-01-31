---
title: Debuggen von verwaltetem Code | Microsoft-Dokumentation
description: Informationen zum Debuggen in C# oder Visual Basic mithilfe des Visual Studio-Debuggers
ms.custom: mvc
ms.date: 03/18/2018
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 040b0f5f657b41a268f69d7f34d6c0072646a8e2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55034089"
---
# <a name="quickstart-debug-with-c-or-visual-basic-using-the-visual-studio-debugger"></a>Schnellstart: Informationen zum Debuggen in C# oder Visual Basic mithilfe des Visual Studio-Debuggers

Der Visual Studio-Debugger umfasst viele nützliche Features zum Debuggen von Apps. In diesem Thema werden einige der grundlegenden Funktionen erläutert.

## <a name="create-a-new-project"></a>Erstellt ein neues Projekt 

1. Klicken Sie in Visual Studio auf **Datei > Neues Projekt**.

2. Klicken Sie erst unter **Visual C#** oder **Visual Basic** auf **.NET Core** und dann im mittleren Bereich auf **Console App (.NET Core)** (Konsolen-App (.NET Core)).

     Falls Sie die Projektvorlage **Konsolenanwendung (.NET Core)** nicht finden, klicken Sie auf den Link **Visual Studio-Installer öffnen** auf der linken Seite des Dialogfelds **Neues Projekt**. Der Visual Studio-Installer wird gestartet. Wählen Sie die Workloads **.NET-Desktopentwicklung** und **.NET Core** aus, und klicken Sie anschließend auf **Ändern**.

3. Geben Sie einen Namen wie **MyDbgApp** ein, und klicken Sie auf **OK**.

    Visual Studio erstellt daraufhin das Projekt.

4. Ersetzen Sie in *Program.cs* oder *Module1.vb* diesen Code

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

Ein *Breakpoint* gibt an, an welcher Stelle Visual Studio ausgeführten Code anhalten soll. So können Sie einen Blick auf die Werte von Variablen oder das Speicherverhalten werfen oder überprüfen, ob eine Verzweigung im Code ausgeführt wird. Es handelt sich dabei um ein grundlegendes Debugfeature.

1. Wenn Sie einen Breakpoint festlegen möchten, klicken Sie im Bundsteg auf den Bereich links neben dem Funktionsaufruf `doWork`. Alternativ können Sie aber auch die Codezeile auswählen und **F9** drücken.

    ![Breakpoint festlegen](../debugger/media/dbg-qs-set-breakpoint-csharp.png "Set a breakpoint")

2. Drücken Sie dann **F5**, oder klicken Sie auf **Debuggen > Debuggen starten**.

    ![Breakpoint treffen](../debugger/media/dbg-qs-hit-breakpoint-csharp.png "Hit a breakpoint")

    Der Debugger hält an dem Breakpoint an, den Sie festlegen. Der gelbe Pfeil deutet auf die Anweisung, bei der der Debugger und die App-Ausführung ausgesetzt werden. Die Zeile mit dem Funktionsaufruf `doWork` wurde noch nicht ausgeführt.

    > [!TIP]
    > Verwenden Sie bei Breakpoints in einer Schleife oder Rekursion oder bei sehr vielen Breakpoints, die Sie häufig schrittweise durchlaufen, einen [bedingten Breakpoint](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression), damit die Codeausführung NUR unterbrochen wird, wenn bestimmte Bedingungen erfüllt sind. Wenn Sie mit einem bedingten Breakpoint arbeiten, sparen Sie Zeit und erleichtern sich möglicherweise das Debuggen von Problemen, die nur schwierig zu reproduzieren sind.

## <a name="navigate-code"></a>Navigieren durch den Code

Es gibt verschiedene Befehle, über die der Debugger zum Fortfahren angewiesen werden kann. In diesem Artikel wird ein nützlicher Befehl zur Codenavigation erläutert, der neu für Visual Studio 2017 ist.

Wenn der Vorgang am Breakpoint ausgesetzt wurde, zeigen Sie auf die Anweisung `c1.AddLast(20)`, bis die Schaltfläche **Run to click** (Ausführen bis Klick) ![Ausführen bis Klick](../debugger/media/dbg-tour-run-to-click.png "Run to Click") angezeigt wird, und klicken Sie diese an.

![Ausführen bis Klick](../debugger/media/dbg-qs-run-to-click-csharp.png "Run to Click")

Dann wird die App weiter ausgeführt, ruft `doWork` auf, und wird bei der Codezeile ausgesetzt, bei der Sie die Schaltfläche angeklickt haben.

Häufig werden die Tastaturbefehle **F10** und **F11** verwendet, um Code durchzugehen. Weitere ausführliche Anweisungen finden Sie unter [Ein erster Blick auf den Visual Studio-Debugger](../debugger/debugger-feature-tour.md).

## <a name="inspect-variables-in-a-datatip"></a>Untersuchen von Variablen in einem Datentipp

1. Zeigen Sie in der aktuellen Codezeile (zu erkennen an dem Ausführungszeiger in gelb) mit der Maus auf das `c1`-Objekt, um Datentipps anzuzeigen.

    ![Datentipp anzeigen](../debugger/media/dbg-qs-data-tip-csharp.png "View a datatip")

    Der aktuelle Wert der Variable `c1` wird angezeigt, und Sie können die Eigenschaften untersuchen. Wenn Sie beim Debuggen einen nicht erwarteten Wert antreffen, enthalten die vorhergehenden oder die aufrufenden Codezeilen möglicherweise einen Fehler. 

2. Erweitern Sie den Datentipp, um die Eigenschaftswerte des `c1`-Objekts einzusehen.

3. Wenn Sie den Datentipp anheften möchten, damit bei der Codeausführung weiterhin der Wert von `c1` angezeigt wird, klicken Sie auf das Stecknadelsymbol. (Sie können den angehefteten Datentipp an eine geeignete Stelle verschieben.)

## <a name="edit-code-and-continue-debugging"></a>Bearbeiten von Code und Fortsetzen des Debuggens

Wenn Sie in einer Debugsitzung eine Änderung feststellen, die Sie in Ihrem Code testen möchten, ist dies auch kein Problem.

1. Klicken Sie auf die zweite Instanz von `c2.First.Value`, und ändern Sie `c2.First.Value` in `c2.Last.Value`.

2. Drücken Sie wiederholt **F10** (oder klicken Sie auf **Debuggen > Prozedurschritt**), um den Debugger fortzusetzen und den bearbeiteten Code auszuführen.

    ![Bearbeiten und fortfahren](../debugger/media/dbg-qs-edit-and-continue-csharp.gif "Edit and continue")

    Wenn Sie **F10** drücken, führt der Debugger jeweils nur eine Anweisung aus, überspringt Funktionen aber, anstatt diese schrittweise auszuführen (der Code, den Sie überspringen, wird weiter ausgeführt).

Weitere Informationen zum Bearbeiten und Fortfahren und zu Einschränkungen von Features finden Sie unter [Edit and Continue (Bearbeiten und Fortfahren)](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie gelernt, wie Sie den Debugger starten, Code schrittweise durchlaufen und Variablen untersuchen. Sie sollten sich einen allgemeinen Überblick über die Debugger-Features verschaffen und die zugehörigen Links aufrufen, um weitere Informationen hierzu zu erhalten.

> [!div class="nextstepaction"]
> [Debugger – Featuretour](../debugger/debugger-feature-tour.md)
