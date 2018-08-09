---
title: Debuggen des verwalteten Codes | Microsoft-Dokumentation
description: Debuggen von c# oder Visual Basic in Visual Studio-debugger
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
ms.openlocfilehash: 2ba06156a8fa44a61b489deba6104673e8fb08ce
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39637522"
---
# <a name="quickstart-debug-with-managed-code-using-the-visual-studio-debugger"></a>Schnellstart: Debuggen Sie mit verwaltetem Code mithilfe von Visual Studio-debugger

Visual Studio-Debugger bietet viele leistungsstarke Features, damit Sie Ihre apps Debuggen können. In diesem Thema werden einige der grundlegenden Funktionen erläutert.

## <a name="create-a-new-project"></a>Erstellt ein neues Projekt 

1. Klicken Sie in Visual Studio auf **Datei > Neues Projekt**.

2. Klicken Sie unter **Visual C#-** oder **Visual Basic**, wählen Sie **.NET Core**, und wählen Sie dann im mittleren Bereich **Konsolen-App ((.NET Core)**.

     Falls Sie die Projektvorlage **Konsolenanwendung (.NET Core)** nicht finden, klicken Sie auf den Link **Visual Studio-Installer öffnen** auf der linken Seite des Dialogfelds **Neues Projekt**. Der Visual Studio-Installer wird gestartet. Wählen Sie die **.NET Desktopentwicklung** und **.NET Core** Workload, wählen Sie dann **ändern**.

3. Geben Sie einen Namen wie **MyDbgApp** , und klicken Sie auf **OK**.

    Visual Studio erstellt daraufhin das Projekt.

4. In *"Program.cs"* oder *"Module1.vb"*, ersetzen Sie den folgenden Code.

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

Ein *Haltepunkt* ist der code eines Markers, der angibt, in denen Visual Studio die Ausführung angehalten werden soll, können Sie einen Blick auf die Werte von Variablen oder das Verhalten des Arbeitsspeichers oder angibt, ob eine Verzweigung des Codes ausführen erste nutzen. Es ist das grundlegendste Feature beim Debuggen.

1. Um den Haltepunkt festzulegen, klicken Sie auf den Bundsteg links neben der `doWork` Funktionsaufruf (oder wählen Sie die Codezeile aus, und drücken Sie **F9**).

    ![Festlegen eines Haltepunkts](../debugger/media/dbg-qs-set-breakpoint-csharp.png "Festlegen eines Haltepunkts")

2. Drücken Sie nun **F5** (oder wählen Sie **Debuggen > Debuggen starten**).

    ![Erreichen eines Haltepunkts](../debugger/media/dbg-qs-hit-breakpoint-csharp.png "erreichen eines Haltepunkts")

    Der Debugger hält, in dem Sie den Haltepunkt festgelegt, ist. Die Anweisung, in denen die Debugger und die app-Ausführung angehalten wird, wird durch den gelben Pfeil angegeben. Die Zeile mit der `doWork` Funktionsaufruf noch nicht noch ausgeführt.

    > [!TIP]
    > Wenn Sie einen in einer Schleife oder Rekursion Haltepunkt oder wenn Sie viele Haltepunkte, die Sie häufig verfügen schrittweise, Durchlaufen einer [bedingten Haltepunkt](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) um sicherzustellen, dass Ihr Code angehalten wird, nur, wenn bestimmte Bedingungen erfüllt sind. Ein bedingter Haltepunkt kann Zeit sparen, und sie können auch eine einfachere zum Debuggen von Problemen, die schwer reproduzierbar sind.

## <a name="navigate-code"></a>Navigieren durch den Code

Es gibt verschiedene Befehle anweisen des Debuggers zum fortfahren. Wir zeigen es sich um einen nützlichen Code Navigationsbefehl die neuen Visual Studio 2017.

Während die Ausführung am Haltepunkt angehalten wird, zeigen Sie die Anweisung `c1.AddLast(20)` bis Grün **Ausführung bis Klick** Schaltfläche ![Ausführung bis Klick](../debugger/media/dbg-tour-run-to-click.png "RunToClick") angezeigt wird, und drücken Sie dann die **Ausführung bis Klick** Schaltfläche.

![Ausführung bis Klick](../debugger/media/dbg-qs-run-to-click-csharp.png "Ausführung bis Klick")

Die app weiterhin Ausführung Aufrufen `doWork`, und hält bei der Codezeile, in dem Sie die Schaltfläche geklickt haben.

Allgemeine Tastenkombinationen, die zum Einschließen von Code schrittweise durchlaufen **F10** und **F11**. Weitere ausführlichen Anweisungen finden Sie in der [Handbuch für Anfänger](../debugger/getting-started-with-the-debugger.md).

## <a name="inspect-variables-in-a-datatip"></a>Überprüfen von Variablen in einem datatip

1. In der aktuellen Zeile des Codes (gekennzeichnet durch die gelbe Ausführungszeiger), zeigen Sie auf die `c1` Objekt mit der Maus auf einen Datatip angezeigt.

    ![Zeigen Sie einen Datatip](../debugger/media/dbg-qs-data-tip-csharp.png "einen Datatip anzeigen")

    Der Datatip erfahren Sie, den aktuellen Wert des der `c1` Variablen und ermöglicht Ihnen, ihre Eigenschaften zu überprüfen. Beim Debuggen, wenn einen Wert angezeigt wird, die, den Sie nicht erwarten, müssen Sie wahrscheinlich einen Fehler in den vorhergehenden oder die aufrufenden Codezeilen. 

2. Erweitern Sie den Datatip Betrachten der aktuellen Eigenschaftswerte für die `c1` Objekt.

3. Sollten Sie den Datatip anzuheften, damit Sie fortfahren können, um den Wert der anzuzeigen `c1` während Sie Code ausführen, klicken Sie auf das kleine Pinsymbol. (Sie können den angehefteten Datatip an einem geeigneten Speicherort verschieben.)

## <a name="edit-code-and-continue-debugging"></a>Bearbeiten von Code und Fortsetzen des Debuggens

Wenn Sie eine Änderung, die Sie in Ihrem Code während einer Debugsitzung testen möchten identifizieren, können Sie dies, zu tun.

1. Klicken Sie auf der zweiten Instanz von `c2.First.Value` , und ändern Sie `c2.First.Value` zu `c2.Last.Value`.

2. Drücken Sie **F10** (oder **Debuggen > Prozedurschritt**) mehrmals fahren fort, um den Debugger, und führen Sie den bearbeiteten Code.

    ![Bearbeiten und Fortfahren](../debugger/media/dbg-qs-edit-and-continue-csharp.gif "bearbeiten und fortfahren")

    **F10** wechselt die eine Debuggeranweisung auf eine Zeit, doch die Schritte für Funktionen, anstatt den Einzelschritt in diese (der Code, den Sie überspringen, immer noch ausgeführt).

Weitere Informationen zur Verwendung von bearbeiten und fortfahren und Einschränkungen für Funktionen, finden Sie unter [bearbeiten und Fortfahren](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie gelernt, starten Sie den Debugger, Code durchlaufen und untersuchen Sie Variablen. Sie sollten einen allgemeinen Überblick über die Debugger-Features sowie Links zu weiteren Informationen zu erhalten.

> [!div class="nextstepaction"]
> [Debugger – Featuretour](../debugger/debugger-feature-tour.md)
