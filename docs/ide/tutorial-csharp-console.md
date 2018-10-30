---
title: Erste Schritte mit C#-Konsolen-Apps in Visual Studio
description: Erfahren Sie anhand einer exemplarischen Vorgehensweise, wie Sie eine C#-Konsolen-App in Visual Studio erstellen.
ms.custom: ''
ms.date: 09/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: tutorial
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: ad1ee95cb9cc754261502e7377cde6c91e5befce
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47859509"
---
# <a name="tutorial-get-started-with-a-c-console-app-in-visual-studio"></a>Tutorial: Erste Schritte mit einer C#-Konsolen-App in Visual Studio

In diesem Tutorial für C# verwenden Sie Visual Studio, um eine Konsolen-App zu erstellen und auszuführen und einige Funktionen der [integrierten Visual Studio-Entwicklungsumgebung (IDE)](visual-studio-ide.md) zu untersuchen, während Sie diese Aufgaben ausführen.

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) kostenlos herunterladen.

## <a name="create-a-project"></a>Erstellen eines Projekts

Zunächst müssen Sie ein Projekt für die C#-Anwendung erstellen. Der Projekttyp enthält, schon bevor Sie mit der Bearbeitung beginnen, alle Vorlagendateien, die Sie benötigen.

1. Öffnen Sie Visual Studio 2017.

2. Klicken Sie in der Menüleiste im oberen Bereich auf **Datei** > **Neu** > **Projekt**.

3. Erweitern Sie im linken Dialogfeld **Neues Projekt** den Eintrag **C#**, und klicken Sie auf **.NET Core**. Wählen Sie im mittleren Bereich die Option **Konsolenanwendung (.NET Core)** aus. Nennen Sie die Datei *Calculator*.

   ![Projektvorlage „Console App (.NET Core)“ im Dialogfeld „Neues Projekt“ in der Visual Studio-IDE](../ide/media/new-project-csharp-calculator-console-app.png)

### <a name="add-a-workgroup-optional"></a>Hinzufügen einer Workgroup (optional)

Wenn Ihnen die Projektvorlage **Console App (.NET Core)** (Konsolen-App (.NET Core)) fehlt, fügen Sie einfach die Workload **Plattformübergreifende .NET Core-Entwicklung** hinzu. Sie haben folgende Möglichkeiten für das Hinzufügen der Workload, je nachdem, welche Visual Studio 2017-Updates auf dem Computer installiert sind.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Option 1: Über das Dialogfeld „Neues Projekt“

1. Wählen Sie im Dialogfeld **Neues Projekt** im linken Bereich den Link **Visual Studio-Installer öffnen** aus.

   ![Auswählen des Links „Visual Studio-Installer öffnen“ im Dialogfeld „Neues Projekt“](../ide/media/csharp-open-visual-studio-installer-generic-dark.png)

1. Der Visual Studio-Installer wird gestartet. Wählen Sie die Workload **Plattformübergreifende .NET Core-Entwicklung** aus, und klicken Sie dann auf **Anpassen**.

   ![Workload für die plattformübergreifende .NET Core-Entwicklung im Visual Studio-Installer](../ide/media/dot-net-core-xplat-dev-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>Option 2: Über die Menüleiste „Extras“

1. Schließen Sie das Dialogfeld **Neues Projekt**, und klicken Sie in der Menüleiste oben auf **Extras** > **Tools und Features abrufen…**.

1. Der Visual Studio-Installer wird gestartet. Wählen Sie die Workload **Plattformübergreifende .NET Core-Entwicklung** aus, und klicken Sie dann auf **Anpassen**.

## <a name="create-a-c-console-calculator-app"></a>Erstellen einer C#-Konsolen-App namens „Calculator“

1. Öffnen Sie Visual Studio 2017, und klicken Sie in der Menüleiste oben auf **Datei** > **Neu** > **Projekt**.

1. Erweitern Sie im linken Dialogfeld **Neues Projekt** den Eintrag **C#**, und klicken Sie auf **.NET Core**. Wählen Sie im mittleren Bereich die Option **Konsolenanwendung (.NET Core)** aus. Nennen Sie die Datei *Calculator*.

1. Geben Sie den folgenden Code in den Code-Editor ein, oder fügen Sie ihn ein:

    ```csharp
    using System;

    namespace Calculator
    {
        class Program
        {
            static void Main(string[] args)
            {
                // Declare variables and then instantiate to zero
                double num1 = 0; double num2 = 0;

                // Display title as the C# console calculator app
                Console.WriteLine("Console Calculator in C#\r");
                Console.WriteLine("------------------------\n");

                // Ask the user to type the first number
                Console.WriteLine("Type a number, and then press Enter");
                num1 = Convert.ToDouble(Console.ReadLine());

                // Ask the user to type the second number
                Console.WriteLine("Type another number, and then press Enter");
                num2 = Convert.ToDouble(Console.ReadLine());

                // Ask the user to choose an option
                Console.WriteLine("Choose an option from the following list:");
                Console.WriteLine("\ta - Add");
                Console.WriteLine("\ts - Subtract");
                Console.WriteLine("\tm - Multiply");
                Console.WriteLine("\td - Divide");
                Console.Write("Your option? ");

                // Use a switch statement to do the math
                switch (Console.ReadLine())
                {
                    case "a":
                        Console.WriteLine($"Your result: {num1} + {num2} = " + (num1 + num2));
                        break;
                    case "s":
                        Console.WriteLine($"Your result: {num1} - {num2} = " + (num1 - num2));
                        break;
                    case "m":
                        Console.WriteLine($"Your result: {num1} * {num2} = " + (num1 * num2));
                        break;
                    case "d":
                        // Ask the user to enter a non-zero divisor until they do so
                        while (num2 == 0)
                        {
                            Console.WriteLine("Enter a non-zero divisor: ");
                            num2 = Convert.ToDouble(Console.ReadLine());
                        }
                        Console.WriteLine($"Your result: {num1} / {num2} = " + (num1 / num2));
                        break;
                    // Return text for an incorrect option entry
                    default:
                        Console.WriteLine("That is an incorrect option entry, please try again.");
                        break;
                }
                // Wait for the user to respond before closing
                Console.Write("Press any key to close the Calculator console app...");
                Console.ReadKey();
            }
        }
    }
    ```

   Der Code, der nach `static void Main(string[] args)` angezeigt wird, sollte wie im folgenden Screenshot aussehen:

   ![Code-Editor mit der C#-Konsolen-App „Calculator“](../ide/media/csharp-console-calculator-code.png)

1. Wählen Sie **Calculator** aus, um das Programm auszuführen, oder drücken Sie **F5**.

   ![Auswählen der Schaltfläche „Calculator“ zum Ausführen der App aus der Symbolleiste](../ide/media/csharp-console-calculator-button.png)

1. Zeigen Sie Ihre App im Konsolenfenster an. Wenn Sie den Eingabeaufforderungen folgen, sollte Ihre App ähnlich wie der folgende Screenshot aussehen:

    ![Konsolenfenster mit der Calculator-App, die Eingabeaufforderungen zu den auszuführenden Aktionen bereitstellt](../ide/media/csharp-console-calculator.png)

### <a name="close-the-app"></a>Schließen der App

1. Drücken Sie eine beliebige Taste, um die Calculator-App zu schließen.

1. Schließen Sie den Bereich **Output** (Ausgabe) in Visual Studio.

   ![Schließen des Ausgabebereichs in Visual Studio](../ide/media/csharp-calculator-close-output-pane.png)

1. Schließen Sie Visual Studio.

## <a name="quick-answers-faq"></a>Schnelle Antworten zu häufig gestellten Fragen

Im folgenden kurzen Abschnitt zu häufig gestellten Fragen werden einige wichtige Konzepte besprochen.

### <a name="what-is-c"></a>Was ist C#?

C# ist eine typsichere Programmiersprache, die unter .NET Framework und .NET Core ausgeführt wird. Mit C# können Sie Windows-Anwendungen, Client-/Serveranwendungen, Datenbankanwendungen, XML-Webdienste, verteilte Komponenten und vieles mehr erstellen.

### <a name="what-is-visual-studio"></a>Was ist Visual Studio?

Visual Studio ist eine integrierte Zusammenstellung von Entwicklertools, die die Produktivität fördern. Es ist also ein Programm zum Erstellen von Programmen und Anwendungen.

### <a name="what-is-a-console-app"></a>Was ist eine Konsolen-App?

Eine Konsolen-App nimmt eine Eingabe und zeigt die Ausgabe in einem Befehlszeilenfenster (Konsole) an.

### <a name="what-is-net-core"></a>Was ist .NET Core?

.NET Core ist die Weiterentwicklung von .NET Framework. In .NET Framework war es nur möglich, Code programmiersprachenübergreifend zu verwenden. Mit .NET Core kann er auch plattformübergreifend genutzt werden. Und die Technologie ist sogar Open Source.

(.NET Framework und .NET Core enthalten Bibliotheken mit vordefinierter Funktionalität. Sie umfassen auch eine CLR (Common Language Runtime), die als ein virtueller Computer fungiert, auf dem Ihr Code ausgeführt wird.)

## <a name="next-steps"></a>Nächste Schritte

Damit haben Sie das Tutorial erfolgreich abgeschlossen. Wenn Sie weitere Informationen erhalten möchten, fahren Sie mit den folgenden Tutorials fort.

> [!div class="nextstepaction"]
> [C#-Tutorials](/dotnet/csharp/tutorials/)

## <a name="see-also"></a>Siehe auch

* Videokurs: [C# Fundamentals for Absolute Beginners (C#-Grundlagen für Neueinsteiger)](https://mva.microsoft.com/en-us/training-courses/c-fundamentals-for-absolute-beginners-16169)
