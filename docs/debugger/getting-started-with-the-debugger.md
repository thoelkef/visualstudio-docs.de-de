---
title: Lernen Sie das Debuggen mit Visual Studio-debugger
ms.description: Learn how to start the Visual Studio debugger, step through code, and inspect data.
ms.custom: mvc
ms.date: 08/01/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- CSharp
- C++
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 235e9386070d316cd9a4f9751ac1d8f1e8fd92b4
ms.sourcegitcommit: db94ca7a621879f98d4c6aeefd5e27da1091a742
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2018
ms.locfileid: "42623796"
---
# <a name="tutorial-learn-to-debug-using-visual-studio"></a>Tutorial: Informationen Sie zum Debuggen mit Visual Studio

Dieser Artikel enthält die Funktionen von Visual Studio-Debugger in eine schrittweise exemplarische Vorgehensweise. Einen allgemeineren Überblick über die Funktionen des Debuggers, finden Sie unter [Debugger – Featuretour](../debugger/debugger-feature-tour.md). Wenn Sie *Debuggen Ihrer app*, er wird in der Regel bedeutet, dass Sie Ihre Anwendung mit dem angefügten Debugger ausgeführt werden. Wenn Sie dies tun, wird der Debugger bietet viele Möglichkeiten, um festzustellen, was den Status Ihres Codes während der Ausführung. Sie können den Code schrittweise durchlaufen und die Werte in Variablen gespeichert, können Sie Überwachungen für die Variablen angezeigt, wenn sich Werte ändern, können Sie den Ausführungspfad des Codes untersuchen, festzustellen, ob eine Verzweigung des Codes wird ausgeführt, und so weiter. Wenn dies das erste Mal, die Sie versucht haben ist, um Code zu debuggen, sollten Sie lesen [Debuggen für absolute Anfänger](../debugger/debugging-absolute-beginners.md) , bevor Sie diesen Artikel durchgehen.

|         |         |
|---------|---------|
|  ![Kamerasymbol für video](../install/media/video-icon.png "Video ansehen")  |    [Sehen Sie sich ein Video](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugger-Feature-tour-of-Visual-studio-2017-sqwiwLD6D_1111787171) zum Debuggen, die ähnliche Schritte zeigt. |

Auch die Demo-app mit c# und C++ ist, sind die Funktionen für Visual Basic, JavaScript und anderen Sprachen von Visual Studio (außer den) unterstützt. Die Screenshots sind in C# geschrieben. Um zwischen c# und C++-Beispielcode zu wechseln, verwenden Sie den Filter "Language" in der oberen rechten Ecke der Seite.

In diesem Tutorial werden Sie Folgendes durchführen:

> [!div class="checklist"]
> * Starten Sie den Debugger und Haltepunkte.
> * Erfahren Sie, Befehle aus, um Code im Debugger schrittweise durchlaufen
> * Überprüfen von Variablen in den Datentipps und Debugger-Fenster
> * Die Aufrufliste überprüfen

## <a name="prerequisites"></a>Erforderliche Komponenten

* Sie müssen Visual Studio 2017 installiert haben und die **.NET Desktopentwicklung** oder **Desktopentwicklung mit C++** arbeitsauslastung.

    Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) kostenlos herunterladen.

    Falls Sie bereits über Visual Studio verfügen, aber die Workload noch installieren müssen, klicken Sie im linken Bereich des Dialogfelds **Neues Projekt** (**Datei** > **Neu** > **Projekt**) auf den Link **Visual Studio-Installer**. Der Visual Studio-Installer wird gestartet. Wählen Sie die. **NET Desktopentwicklung** oder **Desktopentwicklung mit C++** Workload, wählen Sie dann **ändern**.

## <a name="create-a-project"></a>Erstellen eines Projekts

1. Klicken Sie in Visual Studio auf **Datei > Neues Projekt**.

2. Klicken Sie unter **Visual C#-** oder **Visual C++**, wählen Sie **Windows Desktop**, und wählen Sie dann im mittleren Bereich **Konsolen-App** ( **Windows-Konsolenanwendung** in C++).

    Wenn Sie nicht angezeigt wird der **Konsolenanwendung** -Projektvorlage aus, klicken Sie auf die **Visual Studio-Installer öffnen** Link im linken Bereich des der **neues Projekt** Dialogfeld. Der Visual Studio-Installer wird gestartet. Wählen Sie die *.NET Desktopentwicklung** oder **Desktopentwicklung mit C++** Workload, wählen Sie dann **ändern**.

3. Geben Sie einen Namen wie **Get-gestartet-debugging** , und klicken Sie auf **OK**.

    Visual Studio erstellt daraufhin das Projekt.

4. In *"Program.cs"* (c#) oder *Get-gestartet-debugging.cpp* (C++), ersetzen Sie den folgenden Code.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
    using System.Threading.Tasks;

    namespace get_started_debugging
    {
        class Program
        {
            static void Main(string[] args)
            {
            }
        }
    }
    ```

    ```c++
    int main()
    {
        return 0;
    }
    ```

    durch den folgenden:

    ```csharp
    using System;
    using System.Collections.Generic;

    public class Shape
    {
        // A few example members
        public int X { get; private set; }
        public int Y { get; private set; }
        public int Height { get; set; }
        public int Width { get; set; }
   
        // Virtual method
        public virtual void Draw()
        {
            Console.WriteLine("Performing base class drawing tasks");
        }
    }

    class Circle : Shape
    {
        public override void Draw()
        {
            // Code to draw a circle...
            Console.WriteLine("Drawing a circle");
            base.Draw();
        }
    }

    class Rectangle : Shape
    {
        public override void Draw()
        {
            // Code to draw a rectangle...
            Console.WriteLine("Drawing a rectangle");
            base.Draw();
        }
    }

    class Triangle : Shape
    {
        public override void Draw()
        {
            // Code to draw a triangle...
            Console.WriteLine("Drawing a trangle");
            base.Draw();
        }
    }

    class Program
    {
        static void Main(string[] args)
        {

            var shapes = new List<Shape>
            {
                new Rectangle(),
                new Triangle(),
                new Circle()
            };

            foreach (var shape in shapes)
            {
                shape.Draw();
            }

            // Keep the console open in debug mode.
            Console.WriteLine("Press any key to exit.");
            Console.ReadKey();
        }

    }

    /* Output:
        Drawing a rectangle
        Performing base class drawing tasks
        Drawing a triangle
        Performing base class drawing tasks
        Drawing a circle
        Performing base class drawing tasks
    */
    ```

    ```c++
    #include "pch.h"

    #include <string>
    #include <vector>
    #include <iostream>

    class Shape
    {
        int privateX = 0;
        int privateY = 0;
        int privateHeight = 0;
        int privateWidth = 0;

        int getX() const { return privateX; }
        void setX(int value) { privateX = value; }

        int getY() const { return privateY; }
        void setY(int value) { privateY = value; }

        int getHeight() const { return privateHeight; }
        void setHeight(int value) { privateHeight = value; }

        int getWidth() const { return privateWidth; }
        void setWidth(int value) { privateWidth = value; }

        public:
        // Virtual method
        virtual void Draw()
        {
            std::wcout << L"Performing base class drawing tasks" << std::endl;
        }
    };

    class Circle : public Shape
    {
        public:
        void Draw() override
        {
        // Code to draw a circle...
        std::wcout << L"Drawing a circle" << std::endl;
        Shape::Draw();
        }
    };

    class Rectangle : public Shape
    {
        public:
        void Draw() override
        {
        // Code to draw a rectangle...
        std::wcout << L"Drawing a rectangle" << std::endl;
        Shape::Draw();
        }
    };

    class Triangle : public Shape
    {
        public:
        void Draw() override
        {
        // Code to draw a triangle...
        std::wcout << L"Drawing a trangle" << std::endl;
        Shape::Draw();
        }
    };

    int main(std::vector<std::wstring> &args)
    {
        auto shapes = std::vector<Shape*>
        {
            new Rectangle(),
            new Triangle(),
            new Circle()
        };

        for (auto shape : shapes)
        {
            shape->Draw();
        }
    }

    /* Output:
    Drawing a rectangle
    Performing base class drawing tasks
    Drawing a triangle
    Performing base class drawing tasks
    Drawing a circle
    Performing base class drawing tasks
    */
    ```

## <a name="start-the-debugger"></a>Starten Sie den Debugger an!

1. Drücken Sie **F5** (**Debuggen > Debuggen starten**) oder die **Debuggen starten** Schaltfläche ![Debuggen starten](../debugger/media/dbg-tour-start-debugging.png "Debugging starten ") in der Debug-Symbolleiste.

     **F5** startet die app mit dem Debugger angefügt wird, um die app verarbeitet werden, aber derzeit wir ganz einfach den Code untersuchen dies nicht getan haben. Die app nur geladen, und die Ausgabe der Konsole angezeigt.

    ```
    Drawing a rectangle
    Performing base class drawing tasks
    Drawing a triangle
    Performing base class drawing tasks
    Drawing a circle
    Performing base class drawing tasks
    ```

     In diesem Tutorial haben wir werfen einen genaueren Blick auf dieser app, die mit dem Debugger und erhalten einen Blick auf die Debugger-Features.

2. Beenden Sie den Debugger durch Drücken der Beendigung des roten ![Debuggen beenden](../debugger/media/dbg-tour-stop-debugging.png "Debuggen beenden") Schaltfläche.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Festlegen eines Haltepunkts und starten Sie den debugger

1. In der `foreach` der Schleife die `Main` Funktion (`for` -Schleife in C++ `main` Funktion), legen Sie einen Haltepunkt durch Klicken auf den linken Rand der ersten Zeile des Codes.

    ![Festlegen eines Haltepunkts](../debugger/media/get-started-set-breakpoint.png "SetABreakPoint")

    Ein roter Kreis angezeigt, in dem Sie den Haltepunkt festgelegt.

    Haltepunkte sind eine einfache und wichtige Funktion zum zuverlässigen Debuggen. Ein Haltepunkt gibt an, wo Visual Studio im ausgeführten Code angehalten werden soll. So können Sie einen Blick auf die Werte von Variablen oder das Speicherverhalten werfen oder überprüfen, ob eine Verzweigung im Code ausgeführt wird. 

6. Drücken Sie **F5** oder **Debuggen starten** Schaltfläche, die app gestartet wird, und der Debugger ausgeführt wird, um die Codezeile, in dem Sie den Haltepunkt gesetzt haben.

    ![Erreichen eines Haltepunkts](../debugger/media/get-started-hit-breakpoint.png "HitABreakPoint")

    Der gelbe Pfeil stellt die Anweisung auf der der Debugger angehalten ist, die auch app-Ausführung an der gleichen Stelle unterbricht (diese Anweisung wurde noch nicht ausgeführt).

     Wenn die app noch nicht ausgeführt wird, **F5** wird der Debugger gestartet und wird am ersten Haltepunkt angehalten. Andernfalls **F5** wird fortgesetzt, die app bis zum nächsten Haltepunkt ausgeführt wird.

    Haltepunkte sind eine nützliche Funktion, wenn Sie wissen, die Zeile des Codes oder des Codeabschnitts, die Sie genauer untersuchen möchten.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Navigieren Sie im Code im Debugger verwenden diese Befehle

In der Regel verwenden wir die Tastenkombinationen, da es sich um eine gute Möglichkeit, ist schnell auf Ihre app im Debugger (entsprechende Befehle z. B. Menü Befehle in Klammern angezeigt werden) ausführen.

1. Drücken Sie **F11** (oder wählen Sie **Debuggen > Einzelschritt**) einmal (mehrere Male in c#), bis Sie anhalten, auf die `shape.Draw` -Methodenaufruf in der `Main` Methode (`shape->Draw` in C++).

1. Drücken Sie **F11** zu fahren Sie fort, in dem Code für die `Rectangle` Klasse.

     ![Verwenden Sie F11, um Einzelschritt Code](../debugger/media/get-started-f11.png "F11 Einzelschritt")

     F11 wird die **Einzelschritt** -Befehl aus, und setzt die app Ausführung einer Anweisung zu einem Zeitpunkt. F11 ist eine gute Möglichkeit, den Ausführungsablauf in die meisten Details zu überprüfen. (Um im Code schneller zu verschieben, zeigen wir Ihnen einige andere Optionen auch.) Standardmäßig überspringt der Debugger nicht benutzerseitiger Code (Sie weitere Informationen finden Sie unter [nur mein Code](../debugger/just-my-code.md)).

2. Drücken Sie die **F10** (oder wählen Sie **Debuggen > Prozedurschritt**) einige Male, bis auf der Debugger hält die `base.Draw` Methodenaufruf (`Shape::Draw` in C++), und drücken Sie dann **F10** Noch einmal.

     ![Verwenden Sie F10, um Prozedurschritt Code](../debugger/media/get-started-step-over.png "F10 Prozedurschritt")

     Beachten Sie, dass diesmal, die der Debugger nicht schrittweise die `Draw` Methode der Basisklasse (`Shape`). **F10** wechselt den Debugger ohne einen Einzelschritt in die Funktionen oder Methoden in Ihrem app-Code (der Code wird immer noch ausgeführt). Durch Drücken von F10 auf die `base.Draw` (oder `Shape::Draw`) Methodenaufruf (anstelle von **F11**), wir den Implementierungscode für übersprungen `base.Draw` (die vielleicht, es keine Sie jetzt möchten sind).

## <a name="navigate-code-using-run-to-click"></a>Navigieren Sie im Code mit Ausführung bis Klick

5. Der Code-Editor einen Bildlauf nach unten, und zeigen Sie auf die `Console.WriteLine` Methode (`std::cout` in C++) in der `Triangle` Klasse, bis die grüne **Ausführung bis Klick** Schaltfläche ![Ausführung bis Klick](../debugger/media/dbg-tour-run-to-click.png " RunToClick") auf der linken Seite angezeigt wird.

     ![Verwenden Sie die Ausführung bis Klick Feature](../debugger/media/get-started-run-to-click.png "Ausführung bis Klick")

    >  [!NOTE]
    > Die **Ausführung bis Klick** Schaltfläche ist neu in [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]. Wenn Sie nicht, dass die Schaltfläche mit dem grünen Pfeil sehen, verwenden Sie **F11** in diesem Beispiel stattdessen um den Debugger an die richtige Stelle zu gelangen.

6. Klicken Sie auf die **Ausführung bis Klick** Schaltfläche ![Ausführung bis Klick](../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    Mit dieser Schaltfläche ähnelt der als temporären Haltepunkt festlegen. **Ausführung bis Klick** ist praktisch für die Umgehung sich schnell innerhalb eines sichtbaren Bereichs des app-Codes (Sie können in einer geöffneten Datei klicken).

    Der Debugger setzt auf den `Console.WriteLine` für die Implementierung der `Triangle` Klasse (`std::cout` in C++).

    Bei angehaltener skriptausführung, beachten Sie, dass Sie einen Tippfehler! Die Ausgabe "Zeichnen eine Trangle" ist falsch geschrieben. Wir können hier das Problem beheben während der Ausführung der app im Debugger.

## <a name="edit-code-and-continue-debugging"></a>Bearbeiten von Code und Fortsetzen des Debuggens

1. Klicken Sie auf "Zeichnen eine Trangle", und geben Sie eine Korrektur, ändern "Trangle" in "Triangle".

1. Drücken Sie **F11** einmal, und Sie sehen, dass es sich bei der Debugger erneut verschiebt.

    > [!NOTE]
    > Je nachdem, welche Art von Code im Debugger bearbeiten möglicherweise eine Warnmeldung angezeigt. In einigen Szenarien müssen der Code neu kompilieren, bevor Sie fortfahren können.

## <a name="step-out"></a>Ausführen bis Rücksprung

Nehmen wir an, dass Sie fertig sind untersucht die `Draw` -Methode in der die `Triangle` -Klasse, und Sie möchten, nutzen Sie die Funktion, aber behalten Sie den Debugger. Hierzu können Sie mithilfe der **Ausführen bis Rücksprung** Befehl.

1. Drücken Sie **UMSCHALT** + **F11** (oder **Debuggen > Ausführen bis Rücksprung**).

     Mit diesem Befehl wird die app-Ausführung fortgesetzt (und den Debugger wechselt), bis die aktuelle Funktion zurückkehrt.

     Sie muss in der `foreach` wurde eine Schleife in der `Main` Methode (`for` -Schleife in C++).

## <a name="restart-your-app-quickly"></a>Starten Sie Ihre app schnell neu.

Klicken Sie auf die **Neustart** ![App neu starten](../debugger/media/dbg-tour-restart.png "RestartApp") der Debug-Symbolleiste (**STRG** + **UMSCHALT**   +  **F5**).

Beim Drücken **Neustart**, denn Sie spart Zeit und beenden die app und erneutes Starten des Debuggers. Der Debugger hält am ersten Haltepunkt, der erreicht wird, indem Sie Code ausführen.

Der Debugger hält wieder am Haltepunkt, in Festlegen der `foreach` Schleife (`for` -Schleife in C++).

## <a name="inspect-variables-with-data-tips"></a>Untersuchen Sie Variablen mit den Datentipps

Funktionen, die Ihnen ermöglichen, Variablen untersuchen sind eines der nützlichsten Features des Debuggers, und es gibt verschiedene Möglichkeiten dafür. Häufig, wenn Sie versuchen, ein Problem debuggen können, sind Sie versucht, finden Sie heraus, ob Variablen die Werte speichern, die Sie zu einem bestimmten Zeitpunkt über erwarten.

1. Bei angehaltener auf die `foreach` Schleife (`for` -Schleife in C++), drücken Sie die **F11** nach.

1. Zeigen Sie auf die `shapes` -Objekt, und Sie sehen, der Standardwert der Eigenschaft, die `Count` Eigenschaft.

1. Erweitern Sie die `shapes` Objekt, das alle zugehörigen Eigenschaften, z. B. der erste Index des Arrays finden Sie unter `[0]`, das hat den Wert `Rectangle` (c#) oder einer Speicheradresse (C++).

     ![Anzeigen ein Datentipps](../debugger/media/get-started-data-tip.png "einem Datentipp anzeigen")

    Häufig, wenn Debuggen, sollten Sie eine schnelle Möglichkeit zum Überprüfen der Eigenschaftswerte für Objekte, und der Datentipps sind eine gute Möglichkeit dafür.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Untersuchen Sie Variablen mit den Fenstern "Auto" und "lokal"

1. Sehen Sie sich die **"Auto"** Fenster am unteren Rand der Code-Editor.

     ![Untersuchen Sie Variablen im Fenster "Auto"](../debugger/media/get-started-autos-window.png "Fenster \"Auto\"")

    In der **"Auto"** Fenster Variablen und ihren aktuellen Wert angezeigt. Die **"Auto"** Fenster zeigt alle Variablen, die in der aktuellen Zeile oder die vorangehende Zeile verwendet wird (In C++ wird das Fenster zeigt Variablen in den vorherigen drei Zeilen des Codes. Dokumentation für die sprachspezifisches Verhalten).

    > [!NOTE]
    > In JavaScript die **"lokal"** Fenster wird nicht unterstützt die **"Auto"** Fenster.

2. Betrachten Sie als Nächstes die **"lokal"** Fenster auf einer Registerkarte neben der **"Auto"** Fenster.

    Die **"lokal"** Fenster zeigt die Variablen, die in der aktuellen [Bereich](https://www.wikipedia.org/wiki/Scope_(computer_science)).

## <a name="set-a-watch"></a>Set a Watch festlegen

1. In der main-Code-Editorfenster, mit der Maustaste der `shapes` Objekt aus, und wählen Sie **Überwachung hinzufügen**.

    Die **Watch** Fenster am unteren Rand der Code-Editor wird geöffnet. Können Sie eine **Watch** Fenster, geben auf eine Variable (oder eines Ausdrucks), die Sie im Auge zu behalten möchten.

    Nun müssen Sie eine Überwachung, legen Sie für die `shapes` -Objekt, und Sie sehen den Wert ändern, wie Sie den Debugger verschieben. Im Gegensatz zu anderen Variablenfenstern die **Watch** Fenster enthält stets den Variablen, die Sie überwachen (sie sind ausgegraut, wenn außerhalb des gültigen Bereichs).

## <a name="examine-the-call-stack"></a>Die Aufrufliste überprüfen

1. Bei angehaltener in die `foreach` Schleife (`for` -Schleife in C++), klicken Sie auf die **Aufrufliste** Fenster, in dem wird standardmäßig in der unteren rechten Bereich geöffnet.

1. Klicken Sie auf **F11** einige Male, bis Sie anhalten im Debugger finden Sie unter den `Circle.Draw` Methode im Code-Editor. Sehen Sie sich die **Aufrufliste** Fenster.

    ![Überprüfen Sie die Aufrufliste](../debugger/media/get-started-call-stack.png "ExamineCallStack")

    Die **Aufrufliste** Fenster zeigt die Reihenfolge, in dem Methoden und Funktionen werden aufgerufen. Der obersten Zeile wird die aktuelle Funktion (der `Circle.Draw` oder `Circle::Draw` -Methode in der diese app). Die zweite Zeile zeigt, dass `Circle.Draw` aufgerufen wurde, aus der `Main` Methode (`main` in C++) und so weiter.

    >  [!NOTE]
    > Die **Aufrufliste** Fenster ähnelt der Debug-Perspektive in einigen IDEs wie Eclipse.

    Die Aufrufliste ist eine gute Möglichkeit zum Untersuchen und verstehen, den Ausführungsablauf der app.

    Doppelklicken Sie auf eine einzige Zeile Code zu diesem Quellcode betrachten und ändert, die ebenfalls den aktuellen Bereich, der vom Debugger überprüft werden. Den Debugger weitergeführt diese Aktion nicht.

    Sie können auch die Kontextmenüs von der **Aufrufliste** Fenster aus, um andere Dinge tun. Sie können z. B. Legen Sie Haltepunkte in der angegebenen Funktionen, fahren Sie fort mit **Ausführen bis Cursor**, und Untersuchen von Quellcode. Weitere Informationen finden Sie unter [Vorgehensweise: Untersuchen der Aufrufliste](../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Ändern Sie den Ausführungsablauf

1. Mit dem Debugger angehalten werden soll, der `Circle.Draw` Methodenaufruf, drücken Sie **F11** einige Male, bis auf der Debugger hält die `base.Draw` Methodenaufruf (`Shape::Draw` in C++).

1. Verwenden Sie die Maus, und ziehen Sie den gelben Pfeil (der Ausführungszeiger) auf der linken Seite nach der gelbe Pfeil, um eine Zeile, die `Console.WriteLine` (`std::cout` in C++) Methodenaufruf.

1. Drücken Sie **F11** noch einmal.

    Der Debugger führt erneut die `Console.WriteLine` Methode (`std::cout` in C++).

    Ändern Sie den Ausführungsablauf, können Sie z. B. Ausführungspfade für anderen Code zu testen, oder führen Sie ohne Neustart des Debuggers den Code erneut ausführen.

    > [!WARNING]
    > Häufig müssen Sie diese Funktion vorsichtig sein, und Sie wird eine Warnung in der QuickInfo angezeigt. Sie können andere Warnungen, zu sehen. Verschieben den Zeiger kann nicht rückgängig gemacht, Ihre Anwendung in einem früheren app-Status.

1. Drücken Sie **F5** auf die app weiter auszuführen.

    Damit haben Sie das Tutorial erfolgreich abgeschlossen.

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie gelernt, starten Sie den Debugger, Code durchlaufen und untersuchen Sie Variablen. Sie sollten einen allgemeinen Überblick über die Debugger-Features sowie Links zu weiteren Informationen zu erhalten.

> [!div class="nextstepaction"]
> [Debugger – Featuretour](../debugger/debugger-feature-tour.md)
