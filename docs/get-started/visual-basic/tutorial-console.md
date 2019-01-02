---
title: 'Tutorial: Erste Schritte mit Visual Basic'
description: Erfahren Sie anhand einer exemplarischen Vorgehensweise, wie Sie Visual Basic-Konsolenanwendungen in Visual Studio erstellen.
ms.custom: seodec18, get-started
ms.date: 08/10/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: tutorial
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 076d8ed69e742ccb228af26a10ec5f9e76767a70
ms.sourcegitcommit: a715de2ba8c703f37aa2102567b1aa2c0f05a117
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2018
ms.locfileid: "53442043"
---
# <a name="tutorial-get-started-with-visual-basic-in-visual-studio"></a>Tutorial: Erste Schritte mit Visual Basic in Visual Studio

In diesem Tutorial für Visual Basic (VB) lernen Sie die Entwicklung mit Visual Studio kennen und erstellen und führen verschiedene Konsolen-Apps aus. Außerdem machen Sie sich währenddessen mit einigen Features der [integrierten Entwicklungsumgebung (Integrated Development Environment, IDE)](visual-studio-ide.md) von Visual Studio vertraut.

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) kostenlos herunterladen.

## <a name="create-a-project"></a>Erstellen eines Projekts

Erstellen wir zunächst ein Visual Basic-Anwendungsprojekt. Der Projekttyp enthält, schon bevor Sie mit der Bearbeitung beginnen, alle Vorlagendateien, die Sie benötigen.

1. Öffnen Sie Visual Studio 2017.

2. Klicken Sie in der Menüleiste im oberen Bereich auf **Datei** > **Neu** > **Projekt**.

3. Erweitern Sie im Dialogfeld **Neues Projekt** links den Eintrag **Visual Basic**, und klicken Sie auf **.NET Core**. Wählen Sie im mittleren Bereich die Option **Konsolenanwendung (.NET Core)** aus. Nennen Sie die Datei *HelloWorld*.

   ![Projektvorlage „Console App (.NET Core)“ im Dialogfeld „Neues Projekt“ in der Visual Studio-IDE](media/new-project-vb-dotnetcore-whatisyourname-console-app.png)

### <a name="add-a-workgroup-optional"></a>Hinzufügen einer Workgroup (optional)

Wenn Ihnen die Projektvorlage **Console App (.NET Core)** (Konsolen-App (.NET Core)) fehlt, fügen Sie einfach die Workload **Plattformübergreifende .NET Core-Entwicklung** hinzu. Sie haben folgende Möglichkeiten für das Hinzufügen der Workload, je nachdem, welche Visual Studio 2017-Updates auf dem Computer installiert sind.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Option 1: Verwenden des Dialogfelds „Neues Projekt“

1. Klicken Sie im Dialogfeld **Neues Projekt** im linken Bereich auf den Link **Visual Studio-Installer öffnen**.

   ![Klicken Sie auf den Link „Visual Studio-Installer öffnen“ im Dialogfeld „Neues Projekt“](../media/vs-open-visual-studio-installer-generic.png)

1. Der Visual Studio-Installer wird gestartet. Wählen Sie die Workload **Plattformübergreifende .NET Core-Entwicklung** aus, und klicken Sie dann auf **Anpassen**.

   ![Workload für die plattformübergreifende .NET Core-Entwicklung im Visual Studio-Installer](../media/tutorial-aspnet-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>Option 2: Verwenden der Menüleiste „Extras“

1. Schließen Sie das Dialogfeld **Neues Projekt**, und klicken Sie in der Menüleiste oben auf **Extras** > **Tools und Features abrufen…**.

1. Der Visual Studio-Installer wird gestartet. Wählen Sie die Workload **Plattformübergreifende .NET Core-Entwicklung** aus, und klicken Sie dann auf **Anpassen**.

## <a name="create-a-what-is-your-name-application"></a>Erstellen einer „What is your name“-Anwendung

Erstellen wir eine App, die Sie nach Ihrem Namen fragt und ihn anschließend zusammen mit dem Datum und der Uhrzeit anzeigt. Gehen Sie dabei folgendermaßen vor:

1. Wenn es nicht bereits geöffnet ist, öffnen Sie das Projekt *WhatIsYourName*.

1. Geben Sie unmittelbar nach der öffnenden Klammer, die auf die Zeile `Sub Main(args As String())` folgt, und vor der Zeile `End Sub` den folgenden Visual Basic-Code ein:

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    Dieser Code ersetzt die bestehenden Anweisungen <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> und <xref:System.Console.ReadKey%2A>.

   ![Codefenster mit „What is your name“-Code](media/vb-codewindow-what-name.png)

1. Wenn sich das Konsolenfenster öffnet, geben Sie Ihren Namen ein. Das Konsolenfenster sollte so wie der folgende Screenshot aussehen:

   ![Konsolenfenster mit „What is your name“, der Uhrzeit und dem Datum sowie der Nachricht „Drücken Sie eine beliebige Taste, um fortzufahren“](media/vb-console-what-name.png)

1. Drücken Sie eine beliebige Taste, um das Konsolenfenster zu schließen.

## <a name="create-a-calculate-this-application"></a>Erstellen einer Rechenanwendung

1. Öffnen Sie Visual Studio 2017, und klicken Sie in der Menüleiste oben auf **Datei** > **Neu** > **Projekt**.

1. Erweitern Sie im Dialogfeld **Neues Projekt** links den Eintrag **Visual Basic**, und klicken Sie auf **.NET Core**. Wählen Sie im mittleren Bereich die Option **Konsolenanwendung (.NET Core)** aus. Nennen Sie die Datei *CalculateThis*.

1. Geben Sie zwischen den Zeilen `Module Program` und `End Module` den folgenden Code ein:

   ```vb
   Public num1 As Integer
   Public num2 As Integer
   Public answer As Integer
   Sub Main()
       Console.WriteLine("Type a number and press Enter")
       num1 = Console.ReadLine()
       Console.WriteLine("Type another number to add to it and press Enter")
       num2 = Console.ReadLine()
       answer = num1 + num2
       Console.WriteLine("The answer is " & answer)
       Console.ReadLine()
   End Sub
   ```

   Das Codefenster sollte wie der folgende Screenshot aussehen:

   ![Codefenster mit „Calulate This“-Code](media/vb-codewindow-calculate-this.png)

1. Klicken Sie auf **CalculateThis**, um das Programm auszuführen. Das Konsolenfenster sollte so wie der folgende Screenshot aussehen:

    ![Konsolenfenster mit CalculateThis-App und Aufforderungen zu den erwarteten Benutzeraktionen](media/vb-console-calculate-this.png)

## <a name="quick-answers-faq"></a>Schnelle Antworten zu häufig gestellten Fragen

Im folgenden kurzen Abschnitt zu häufig gestellten Fragen werden einige wichtige Konzepte besprochen.

### <a name="what-is-visual-basic"></a>Was ist Visual Basic?

Visual Basic ist eine typsichere Programmiersprache, die einfach zu erlernen ist. Sie wurde von BASIC abgeleitet, was für „Beginner's All-purpose Symbolic Instruction Code“ (nicht zweckgebundener, symbolischer Anweisungscode für Anfänger) steht.

### <a name="what-is-visual-studio"></a>Was ist Visual Studio?

Visual Studio ist eine integrierte Zusammenstellung von Entwicklertools, die die Produktivität fördern. Es ist also ein Programm zum Erstellen von Programmen und Anwendungen.

### <a name="what-is-a-console-app"></a>Was ist eine Konsolen-App?

Eine Konsolen-App nimmt eine Eingabe und zeigt die Ausgabe in einem Befehlszeilenfenster (Konsole) an.

### <a name="what-is-net-core"></a>Was ist .NET Core?

.NET Core ist die Weiterentwicklung von .NET Framework. In .NET Framework war es nur möglich, Code programmiersprachenübergreifend zu verwenden. Mit .NET Core kann er auch plattformübergreifend genutzt werden. Und die Technologie ist sogar Open Source. (Sowohl .NET Framework als auch .NET Core enthalten Bibliotheken mit vorgefertigter Funktionalität und eine Common Language Runtime (CLR), die als virtueller Computer fungiert, auf dem der Code ausgeführt wird.)

## <a name="next-steps"></a>Nächste Schritte

Damit haben Sie das Tutorial erfolgreich abgeschlossen. Weitere Informationen finden Sie im folgenden Tutorial.

> [!div class="nextstepaction"]
> [Videotutorial: Visual Basic Fundamentals for Absolute Beginners (Visual Basic-Grundlagen für Einsteiger)](https://mva.microsoft.com/en-us/training-courses/visual-basic-fundamentals-for-absolute-beginners-16507)

## <a name="see-also"></a>Siehe auch

* [Neues in Visual Basic](/dotnet/visual-basic/getting-started/whats-new)
* [IntelliSense für Visual Basic-Codedateien](../../ide/visual-basic-specific-intellisense.md)
* [Sprachreferenz zu Visual Basic](/dotnet/visual-basic/language-reference/index)