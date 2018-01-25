---
title: Erste Schritte mit Visual Basic in Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 12/08/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: tutorial
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: ghogen
dev_langs: vb
ms.workload: multiple
ms.openlocfilehash: b1de10c76d6a974280bfe016490a7567d0807675
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/22/2018
---
# <a name="getting-started-with-visual-basic-in-visual-studio"></a>Erste Schritte mit Visual Basic in Visual Studio
In diesem Tutorial für Visual Basic (VB), lernen Sie die Entwicklung mit Visual Studio kennen und führen verschiedene Konsolen-Apps aus. Außerdem machen Sie sich währenddessen mit einigen Funktionen der [integrierten Entwicklungsumgebung (Integrated Development Environment, IDE)](visual-studio-ide.md) von Visual Studio vertraut.

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) kostenlos herunterladen.

## <a name="before-you-begin"></a>Bevor Sie beginnen
In den folgenden häufig gestellten Fragen werden einige wichtige Konzepte vorgestellt.
### <a name="what-is-visual-basic"></a>Was ist Visual Basic?
Visual Basic ist eine typsichere Programmiersprache, die einfach zu erlernen ist. Sie wurde von BASIC abgeleitet, was für „Beginner's All-purpose Symbolic Instruction Code“ (nicht zweckgebundener, symbolischer Anweisungscode für Anfänger) steht.
### <a name="what-is-visual-studio"></a>Was ist Visual Studio?
Visual Studio ist eine integrierte Zusammenstellung von Entwicklertools, die die Produktivität fördern. Es ist also ein Programm zum Erstellen von Programmen und Anwendungen.  
### <a name="what-is-a-console-app"></a>Was ist eine Konsolen-App?
Eine Konsolen-App nimmt eine Eingabe und zeigt die Ausgabe in einem Befehlszeilenfenster (Konsole) an.
### <a name="what-is-net-core"></a>Was ist .NET Core?
.NET Core ist die Weiterentwicklung von .NET Framework. In .NET Framework war es nur möglich, Code programmiersprachenübergreifend zu verwenden. Mit .NET Core kann er auch plattformübergreifend genutzt werden. Und die Technologie ist sogar Open Source. (Sowohl .NET Framework als auch .NET Core enthalten Bibliotheken mit vorgefertigter Funktionalität und eine Common Language Runtime (CLR), die als virtueller Computer fungiert, auf dem der Code ausgeführt wird.)

## <a name="start-developing"></a>Mit dem Entwickeln beginnen
Sind Sie bereit? Los geht‘s!

### <a name="create-a-project"></a>Erstellen eines Projekts
Erstellen wir zunächst ein Visual Basic-Anwendungsprojekt. Der Projekttyp enthält, schon bevor Sie mit der Bearbeitung beginnen, alle Vorlagendateien, die Sie benötigen.

1. Öffnen Sie Visual Studio 2017.

2. Klicken Sie in der Menüleiste im oberen Bereich auf **Datei** > **Neu** > **Projekt...**.

3. Erweitern Sie im Dialogfeld **Neues Projekt** links den Eintrag **Visual Basic**, und klicken Sie auf **.NET Core**. Wählen Sie im mittleren Bereich die Option **Konsolenanwendung (.NET Core)** aus. Nennen Sie die Datei *HelloWorld*.  

   ![Projektvorlage „Console App (.NET Core)“ im Dialogfeld „Neues Projekt“ in der Visual Studio-IDE](../ide/media/new-project-vb-dotnetcore-whatisyourname-console-app.png)

#### <a name="add-a-workgroup-optional"></a>Hinzufügen einer Workgroup (optional)
Wenn Ihnen die Projektvorlage **Console App (.NET Core)** (Konsolen-App (.NET Core)) fehlt, fügen Sie einfach die Workload **Plattformübergreifende .NET Core-Entwicklung** hinzu. Sie haben folgende Möglichkeiten für das Hinzufügen der Workload, je nachdem, welche Visual Studio 2017-Updates auf dem Computer installiert sind.

##### <a name="option-1-use-the-new-project-dialog-box"></a>Option 1: Über das Dialogfeld „Neues Projekt“
1. Klicken Sie im Dialogfeld **Neues Projekt** im linken Bereich auf den Link **Visual Studio-Installer öffnen**.

  ![Klicken Sie auf den Link „Visual Studio-Installer öffnen“ im Dialogfeld „Neues Projekt“](../ide/media/vs-open-visual-studio-installer-generic.png)

2. Der Visual Studio-Installer wird gestartet. Wählen Sie die Workload **Plattformübergreifende .NET Core-Entwicklung** aus, und klicken Sie dann auf **Anpassen**.

   ![Workload für die plattformübergreifende .NET Core-Entwicklung im Visual Studio-Installer](../ide/media/dot-net-core-xplat-dev-workload.png)

##### <a name="option-2-use-the-tools-menu-bar"></a>Option 2: Über die Menüleiste „Extras“
1. Schließen Sie das Dialogfeld **Neues Projekt**, und klicken Sie in der Menüleiste oben auf **Extras** > **Tools und Features abrufen…**.

2. Der Visual Studio-Installer wird gestartet. Wählen Sie die Workload **Plattformübergreifende .NET Core-Entwicklung** aus, und klicken Sie dann auf **Anpassen**.   

## <a name="create-a-what-is-your-name-application"></a>Erstellen einer „What is your name“-Anwendung
Erstellen wir eine App, die Sie nach Ihrem Namen fragt und ihn anschließend zusammen mit dem Datum und der Uhrzeit anzeigt. Gehen Sie dabei folgendermaßen vor:

1. Wenn es nicht bereits geöffnet ist, öffnen Sie das Projekt *WhatIsYourName*.

2. Geben Sie unmittelbar nach der öffnenden Klammer, die auf die Zeile `Sub Main(args As String())` folgt, und vor der Zeile `End Sub` den folgenden Visual Basic-Code ein:

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    Dieser Code ersetzt die bestehenden Anweisungen <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> und <xref:System.Console.ReadKey%2A>.

 ![Codefenster mit „What is your name“-Code](../ide/media/vb-codewindow-what-name.png)

3. Wenn sich das Konsolenfenster öffnet, geben Sie Ihren Namen ein. Das Konsolenfenster sollte so wie der folgende Screenshot aussehen:

   ![Konsolenfenster mit „What is your name“, der Uhrzeit und dem Datum sowie der Nachricht „Drücken Sie eine beliebige Taste, um fortzufahren“](../ide/media/vb-console-what-name.png)

5. Drücken Sie eine beliebige Taste, um das Konsolenfenster zu schließen.

## <a name="create-a-calculate-this-application"></a>Erstellen einer Rechenanwendung
1. Öffnen Sie Visual Studio 2017, und klicken Sie in der Menüleiste oben auf **Datei** > **Neu** > **Projekt…**.

2. Erweitern Sie im Dialogfeld **Neues Projekt** links den Eintrag **Visual Basic**, und klicken Sie auf **.NET Core**. Wählen Sie im mittleren Bereich die Option **Konsolenanwendung (.NET Core)** aus. Nennen Sie die Datei *CalculateThis*.  

3. Geben Sie zwischen den Zeilen `Module Program` und `End Module` den folgenden Code ein:

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

   ![Codefenster mit „Calulate This“-Code](../ide/media/vb-codewindow-calculate-this.png)

4. Klicken Sie auf **CalculateThis**, um das Programm auszuführen. Das Konsolenfenster sollte so wie der folgende Screenshot aussehen:       

    ![Konsolenfenster mit CalculateThis-App und Aufforderungen zu den erwarteten Benutzeraktionen](../ide/media/vb-console-calculate-this.png)

Damit haben Sie das Tutorial erfolgreich abgeschlossen.

## <a name="see-also"></a>Siehe auch
* [Leitfaden für Visual Basic](/dotnet/visual-basic/index)
* [Neues in Visual Basic](/dotnet/visual-basic/getting-started/whats-new)
* [IntelliSense für Visual Basic-Codedateien](visual-basic-specific-intellisense.md)
* [Sprachreferenz zu Visual Basic](/dotnet/visual-basic/language-reference/index)
* Videokurs: [Visual Basic Fundamentals for Absolute Beginners (Visual Basic-Grundlagen für Einsteiger)](https://mva.microsoft.com/en-us/training-courses/visual-basic-fundamentals-for-absolute-beginners-16507)
