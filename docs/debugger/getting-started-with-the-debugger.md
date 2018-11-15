---
title: Informationen zum Debuggen mithilfe des Visual Studio-Debuggers
ms.description: Learn how to start the Visual Studio debugger, step through code, and inspect data.
ms.custom: debug-experiment
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
ms.openlocfilehash: d832753b798cc9e476b675f8791c1ab245b3adee
ms.sourcegitcommit: a34b7d4fdb3872865fcf98ba24a0fced58532adc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2018
ms.locfileid: "51561672"
---
# <a name="tutorial-learn-to-debug-using-visual-studio"></a>Tutorial: Informationen zum Debuggen mit Visual Studio

In diesem Artikel werden die Funktionen des Visual Studio-Debuggers in einer ausführlichen exemplarischen Vorgehensweise vorgestellt. Einen allgemeineren Überblick über die Funktionen des Debuggers finden Sie unter [Übersicht über die Funktionen des Debuggers](../debugger/debugger-feature-tour.md). Wenn Sie *Ihre App debuggen*, bedeutet dies in der Regel, dass Sie Ihre Anwendung mit dem angefügten Debugger ausführen. Wenn Sie dies machen, bietet der Debugger viele Möglichkeiten zum Ermitteln des Status Ihres Codes während der Ausführung. Sie können Ihren Code schrittweise durchlaufen und die Werte prüfen, die in Variablen gespeichert sind, Sie können die Überwachung von Variablen festlegen, um zu sehen, wenn sich Werte ändern, und Sie können den Ausführungspfad Ihres Codes prüfen und feststellen, ob ein Codezweig ausgeführt wird usw. Wenn Sie zum ersten Mal versuchen, Code zu debuggen, sollten Sie [Debuggen für Einsteiger](../debugger/debugging-absolute-beginners.md) lesen, bevor Sie diesen Artikel durchgehen.

| | |
|---------|---------|
| ![Kamerasymbol für Video](../install/media/video-icon.png "Video ansehen") | Zum Debuggen können Sie sich ein [Video ansehen](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugger-Feature-tour-of-Visual-studio-2017-sqwiwLD6D_1111787171), in dem ähnliche Schritte beschrieben werden. |

Auch wenn die Demo-App C# und C++ verwendet, beziehen sich die Funktionen auf Visual Basic, JavaScript und andere von Visual Studio unterstützten Programmiersprachen (sofern nicht anderweitig angegeben). Die Screenshots wurden in C# erstellt.

In diesem Tutorial werden Sie Folgendes durchführen:

> [!div class="checklist"]
> * Starten des Debuggers und Treffen der Breakpoints.
> * Erlernen von Befehlen zum Durchlaufen des Codes im Debugger
> * Überprüfen von Variablen im Fenster für Datentipps und im Debugger-Fenster
> * Überprüfen der Aufrufliste

## <a name="prerequisites"></a>Erforderliche Komponenten

* Sie müssen Visual Studio 2017 und die Workload **.NET-Desktopentwicklung** oder **Desktopentwicklung mit C++** installiert haben.

    Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite  [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)  kostenlos herunterladen.

    Falls Sie bereits über Visual Studio verfügen, aber die Workload noch installieren müssen, klicken Sie im linken Bereich des Dialogfelds **Neues Projekt** (**Datei** > **Neu** > **Projekt**) auf den Link **Visual Studio-Installer**. Der Visual Studio-Installer wird gestartet. Wählen Sie die Workload **.NET-Desktopentwicklung** oder **Desktopentwicklung mit C++** und anschließend **Ändern** aus.

## <a name="create-a-project"></a>Erstellen eines Projekts

1. Klicken Sie in Visual Studio auf **Datei > Neues Projekt**.

2. Wählen Sie unter **Visual C#** oder **Visual C++** den Eintrag **Windows Desktop** und anschließend im mittleren Bereich **Konsolenanwendung** (**Windows-Konsolenanwendung** in C++) aus.

    Wenn Ihnen die Projektvorlage **Konsolenanwendung** nicht angezeigt wird, klicken Sie im linken Bereich des Dialogfelds **Neues Projekt** auf den Link **Visual Studio-Installer öffnen**. Der Visual Studio-Installer wird gestartet. Wählen Sie die Workload *.NET-Desktopentwicklung** oder **Desktopentwicklung mit C++** und anschließend **Ändern** aus.

3. Geben Sie einen Namen ein, z.B. **get-gestartet-debugging**, und klicken Sie auf **OK**.

    Visual Studio erstellt daraufhin das Projekt.

    > [!NOTE]
    > Verwenden Sie zum Wechseln zwischen dem C#- und dem C++-Beispielcode in diesem Artikel den Sprachenfilter oben rechts auf dieser Seite.

4. Ersetzen Sie in *Program.cs* (C#) oder *get-started-debugging.cpp* (C++) folgenden Code

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

## <a name="start-the-debugger"></a>Starten Sie den Debugger.

1. Drücken Sie die Taste **F5** (**Debuggen > Debuggen starten**), oder klicken Sie in der Symbolleiste „Debuggen“ auf die Schaltfläche **Debuggen starten** ![Debuggen starten](../debugger/media/dbg-tour-start-debugging.png "Start Debugging").

     Durch Drücken der Taste **F5** wird die App mit dem an den App-Prozess angefügten Debugger gestartet. Bisher haben Sie jedoch nichts weiter gemacht, um den Code zu untersuchen. Die App wird lediglich geladen, und Ihnen wird die Konsolenausgabe angezeigt.

    ```
    Drawing a rectangle
    Performing base class drawing tasks
    Drawing a triangle
    Performing base class drawing tasks
    Drawing a circle
    Performing base class drawing tasks
    ```

     In diesem Tutorial werfen wir einen genaueren Blick auf diese App mit dem Debugger und schauen uns die Funktionen des Debuggers an.

2. Durch Drücken der roten Stopptaste ![Debuggen beenden](../debugger/media/dbg-tour-stop-debugging.png "Debuggen beenden") können Sie den Debugger beenden.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Festlegen eines Haltepunkts und Starten des Debuggers

1. Legen Sie in der `foreach`-Schleife der Funktion `Main` (in C++ die `for`-Schleife der Funktion `main`) einen Haltepunkt fest, indem Sie auf den linken Rand der folgenden Codezeile klicken:

    `shape.Draw()` (oder `shape->Draw()` in C++)

    An der Stelle des Haltepunkts wird ein roter Kreis angezeigt.

    Haltepunkte sind eine einfache und wichtige Funktion zum zuverlässigen Debuggen. Ein Haltepunkt gibt an, wo Visual Studio im ausgeführten Code angehalten werden soll. So können Sie einen Blick auf die Werte von Variablen oder das Speicherverhalten werfen oder überprüfen, ob eine Verzweigung im Code ausgeführt wird. 

6. Wenn Sie die Taste **F5** drücken oder auf die Schaltfläche **Debuggen starten** klicken, wird die App gestartet, und der Debugger geht zu der Codezeile, in der Sie den Haltepunkt festgelegt haben.

    ![Festlegen und Treffen eines Haltepunkts](../debugger/media/get-started-set-breakpoint.gif)

    Der gelbe Pfeil stellt die Anweisung dar, an der der Debugger angehalten hat. An der gleichen Stelle wird auch die Ausführung der App unterbrochen (diese Anweisung wurde noch nicht ausgeführt).

     Wenn die App noch nicht ausgeführt wird, kann der Debugger durch Drücken der Taste **F5** gestartet werden und hält am ersten Haltepunkt an. Andernfalls wird durch Drücken der Taste **F5** die Ausführung der App bis zum nächsten Haltepunkt fortgesetzt.

    Haltepunkte sind eine nützliche Funktion, wenn Ihnen die Codezeile oder der Codeabschnitt bekannt ist, die bzw. den Sie genauer untersuchen möchten.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Navigieren durch Code im Debugger mithilfe von Schrittbefehlen

In der Regel verwenden wir an dieser Stelle Tastenkombinationen, da auf diese Weise eine schnelle Ausführung Ihrer App im Debugger möglich ist (entsprechende Befehle, wie z.B. Menübefehle, werden in Klammern angezeigt).

1. Drücken Sie, während der `shape.Draw`-Methodenaufruf in der `Main`-Methode (`shape->Draw` in C++) angehalten wurde, die Taste **F11** (oder klicken Sie auf **Debuggen > Schrittweise ausführen**), um den Code für die `Rectangle`-Klasse anzuzeigen.

     ![Verwenden von F11 für schrittweise Codeausführung](../debugger/media/get-started-f11.png "F11: Schrittweise ausführen")

     Durch Drücken der Taste F11 wird der Befehl **Schrittweise ausführen** gesendet und die App Anweisung für Anweisung ausgeführt. Das Drücken der Taste F11 bietet eine gute Möglichkeit, den Ausführungsablauf am ausführlichsten zu überprüfen. (Wenn Sie den Code schneller durchlaufen möchten, zeigen wir Ihnen auch einige andere Optionen.) Standardmäßig überspringt der Debugger Nichtbenutzercode (weitere Einzelheiten hierzu finden Sie unter [Nur eigenen Code](../debugger/just-my-code.md)).

2. Drücken Sie so lange die Taste **F10** (oder klicken Sie auf **Debuggen > Step Over (Überspringen)**), bis der Debugger beim `base.Draw`-Methodenaufruf (`Shape::Draw` in C++) anhält. Drücken Sie anschließend erneut die Taste **F10**.

     ![Verwenden von F10 zum Überspringen von Code](../debugger/media/get-started-step-over.png "F10 – Überspringen")

     Beachten Sie, dass der Debugger die `Draw`-Methode der Basisklasse (`Shape`) dieses Mal nicht schrittweise ausführt. Durch Drücken der Taste **F10** fährt der Debugger in Ihrem App-Code fort, ohne dass Funktionen oder Methoden schrittweise ausgeführt werden (der Code wird immer noch ausgeführt). Durch Drücken der Taste F10 im `base.Draw`-Methodenaufruf (oder `Shape::Draw`) (anstelle der Taste **F11**) wurde der Implementierungscode für `base.Draw` übersprungen (der für uns gerade möglicherweise nicht von Interesse ist).

## <a name="navigate-code-using-run-to-click"></a>Navigieren durch Code mithilfe von „Ausführung bis Klick“

5. Scrollen Sie im Code-Editor nach unten und bewegen Sie den Cursor so lange über die `Console.WriteLine`-Methode (`std::cout` in C++) in der `Triangle`-Klasse, bis auf der linken Seite die grüne Schaltfläche **Ausführung bis Klick** ![Ausführung bis Klick](../debugger/media/dbg-tour-run-to-click.png "RunToClick") angezeigt wird.

     ![Verwenden der Funktion „Ausführung bis Klick“](../debugger/media/get-started-run-to-click.png "Ausführung bis Klick")

   > [!NOTE]
   > Die Schaltfläche **Ausführung bis Klick** ist neu in [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]. Wenn Ihnen die Schaltfläche mit dem grünen Pfeil nicht angezeigt wird, verwenden Sie in diesem Beispiel stattdessen die Taste **F11**, damit der Debugger an der richtigen Stelle fortfährt.

6. Klicken Sie auf die Schaltfläche **Ausführung bis Klick** ![Ausführung bis Klick](../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    Die Verwendung dieser Schaltfläche ist vergleichbar mit dem Festlegen eines temporären Haltepunkts. **Ausführung bis Klick** ist praktisch, um schnell durch einen sichtbaren Bereich mit App-Code zu navigieren (Sie können in eine beliebige geöffnete Datei klicken).

    Der Debugger fährt bis zur Implementierung der `Console.WriteLine`-Methode für die `Triangle`-Klasse (`std::cout` in C++) fort.

    Nach dem Anhalten des Debuggers fällt Ihnen ein Tippfehler auf. Die Ausgabe "Drawing a trangle" ist falsch geschrieben. Dieser Fehler kann direkt hier korrigiert werden, während die App im Debugger ausgeführt wird.

## <a name="edit-code-and-continue-debugging"></a>Bearbeiten von Code und Fortsetzen des Debuggens

1. Klicken Sie auf "Drawing a trangle", und ersetzen Sie „trangle“ durch „triangle“.

1. Drücken Sie **F11** einmal, und der Debugger wird weiter ausgeführt.

    > [!NOTE]
    > Abhängig vom Codetyp, den Sie im Debugger bearbeiten, wird Ihnen möglicherweise eine Warnmeldung angezeigt. In einigen Szenarios muss der Code erneut kompilieren, bevor Sie fortfahren können.

## <a name="step-out"></a>Ausführen bis Rücksprung

Angenommen Sie haben die `Draw`-Methode in der `Triangle`-Klasse fertig untersucht und möchten die Funktion, aber nicht den Debugger, beenden. Dies ist mit dem Befehl **Ausführen bis Rücksprung** möglich.

1. Drücken Sie **UMSCHALT** + **F11** (oder klicken Sie auf **Debuggen > Ausführen bis Rücksprung**).

     Mit diesem Befehl wird die Ausführung der App so lange fortgesetzt (und der Debugger weiter ausgeführt), bis die aktuelle Funktion wieder ausgeführt wird.

     Jetzt sollten Sie sich wieder in der `foreach`-Schleife in der `Main`-Methode (in C++ `for`-Schleife) befinden.

## <a name="restart-your-app-quickly"></a>Schnelles Neustarten Ihrer App

Klicken Sie in der Symbolleiste „Debuggen“ auf die Schaltfläche **Neu starten** ![App neu starten](../debugger/media/dbg-tour-restart.png "RestartApp") (**STRG** + **UMSCHALT** + **F5**).

Durch das Klicken auf **Neu starten** sparen Sie im Vergleich zum Beenden der App und dem erneuten Starten des Debuggers Zeit. Der Debugger hält am ersten Haltepunkt an, der bei der Codeausführung erreicht wird.

Der Debugger hält erneut an dem von Ihnen festgelegten Haltepunkt an, bei der `shape.Draw()`-Methode (`shape->Draw()` in C++).

## <a name="inspect-variables-with-data-tips"></a>Untersuchen von Variablen mithilfe von Datentipps

Funktionen, mit denen Sie Variablen untersuchen können, zählen zu den nützlichsten Funktionen des Debuggers. Es gibt verschiedene Möglichkeiten, Variablen zu untersuchen. Beim Debuggen eines Problems wird häufig versucht herauszufinden, ob Variablen die Werte speichern, die diese zu einem bestimmten Zeitpunkt erwartungsgemäß aufweisen.

1. Während der Debugger bei der `shape.Draw()`-Methode (`shape->Draw()` in C++) anhält und Sie den Cursor über das Objekt `shapes` bewegen, wird Ihnen der zugehörige Standardeigenschaftswert, die Eigenschaft `Count`, angezeigt.

1. Erweitern Sie das Objekt `shapes`, um sämtliche zugehörige Eigenschaften anzuzeigen, wie z.B. den ersten Index des Arrays `[0]` mit dem Wert `Rectangle` (C#) oder eine Speicheradresse (C++).

     ![Anzeigen eines Datentipps](../debugger/media/get-started-data-tip.gif "View a Data Tip")

    Sie können Objekte weiter erweitern, um die zugehörigen Eigenschaften anzuzeigen, wie z.B. die Eigenschaft `Height` des Rechtecks.

    Beim Debuggen möchten Sie häufig eine schnelle Möglichkeit zum Überprüfen der Eigenschaftswerte für Objekte. Die Datentipps stellen eine gute Methode hierfür dar.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Untersuchen von Variablen über die Fenster „Auto“ und „Lokal“

1. Schauen Sie sich das Fenster **Auto** unten im Code-Editor an.

     ![Untersuchen von Variablen im Fenster „Auto“](../debugger/media/get-started-autos-window.png "Fenster „Auto“")

    Im Fenster **Auto** werden Ihnen Variablen und der zugehörige aktuelle Wert angezeigt. Im Fenster **Auto** werden sämtliche Variablen angezeigt, die in der aktuellen Zeile oder der vorangehenden Zeile verwendet werden (in C++ werden in den vorangehenden drei Codezeilen Variablen angezeigt. In der Dokumentation finden Sie Informationen zum sprachspezifischen Verhalten).

    > [!NOTE]
    > In JavaScript wird das Fenster **Lokal** nicht unterstützt, das Fenster **Auto** jedoch schon.

2. Schauen Sie sich als Nächstes das Fenster **Lokal** auf einer Registerkarte neben dem Fenster **Auto** an.

    Im Fenster **Lokal** werden Ihnen die Variablen angezeigt, die sich im aktuellen [Bereich](https://www.wikipedia.org/wiki/Scope_(computer_science)) befinden.

## <a name="set-a-watch"></a>Festlegen von Überwachung

1. Klicken Sie im Hauptfenster des Code-Editors mit der rechten Maustaste auf das Objekt `shapes`, und wählen Sie **Überwachung hinzufügen** aus.

    Das Fenster **Überwachung** wird unten im Code-Editor geöffnet. Sie können über das Fenster **Überwachung** eine Variable (oder einen Ausdruck) angeben, die Sie im Auge behalten möchten.

    Nun haben Sie festgelegt, dass das Objekt `shapes` überwacht werden soll, und Sie können seine Wertänderung sehen, wenn Sie durch den Debugger navigieren. Im Gegensatz zu den anderen Variablenfenstern werden im Fenster **Überwachung** immer die Variablen angezeigt, die von Ihnen überwacht werden (wenn sie außerhalb des gültigen Bereichs liegen, sind sie ausgegraut).

## <a name="examine-the-call-stack"></a>Überprüfen der Aufrufliste

1. Klicken Sie, nachdem in der `foreach`-Schleife (in C++ die `for`-Schleife) angehalten wurde, auf das Fenster **Aufrufliste**. Dieses Fenster ist standardmäßig im unteren rechten Bereich geöffnet.

2. Drücken Sie einige Male die Taste **F11**, bis der Debugger bei der `Circle.Draw`-Methode im Code-Editor anhält. Schauen Sie sich das Fenster **Aufrufliste** an.

    ![Überprüfen der Aufrufliste](../debugger/media/get-started-call-stack.png "ExamineCallStack")

    Im Fenster **Aufrufliste** wird die Reihenfolge angezeigt, in der Methoden und Funktionen aufgerufen werden. In der obersten Zeile wird die aktuelle Funktion (in dieser App die `Circle.Draw`- oder `Circle::Draw`-Methode) angezeigt. In der zweiten Zeile wird angezeigt, dass `Circle.Draw` über die `Main`-Methode (`main` in C++) aufgerufen wurde usw.

   > [!NOTE]
   > Das Fenster **Aufrufliste** ist mit der Debugperspektive in einigen IDEs wie Eclipse vergleichbar.

    Die Aufrufliste bietet eine nützliche Möglichkeit zum Untersuchen und Verstehen des Ausführungsablaufs einer App.

    Sie können auf eine Codezeile doppelklicken, um diesen Quellcode anzuzeigen. Dadurch wird auch der aktuelle Bereich geändert, der vom Debugger untersucht wird. Durch diese Aktion wird der Debugger nicht weiter ausgeführt.

    Sie können auch über die Kontextmenüs im Fenster **Aufrufliste** weitere Aktionen ausführen. So können Sie beispielsweise Haltepunkte in bestimmte Funktionen einfügen, den Debugger über **Ausführen bis Cursor** weiter ausführen und Quellcode untersuchen. Weitere Informationen hierzu finden Sie unter [Vorgehensweise: Untersuchen der Aufrufliste](../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Ändern des Ausführungsablaufs

1. Drücken Sie, wenn der Debugger beim `Circle.Draw`-Methodenaufruf angehalten hat, einige Male die Taste **F11**, bis der Debugger beim `base.Draw`-Methodenaufruf (`Shape::Draw` in C++) anhält.

1. Ziehen Sie den gelben Pfeil (den Ausführungszeiger) mit der Maus nach links und um eine Zeile nach oben in den `Console.WriteLine`-Methodenaufruf (`std::cout` in C++).

1. Drücken Sie erneut die Taste **F11**.

    Der Debugger führt die `Console.WriteLine`-Methode (`std::cout` in C++) erneut aus.

    Durch Ändern des Ausführungsablaufs können Sie Aktionen ausführen wie das Testen verschiedener Pfade für die Codeausführung oder das erneute Ausführen von Code ohne Neustarten des Debuggers.

    > [!WARNING]
    > Bei dieser Funktion müssen Sie häufig vorsichtig vorgehen. Sie werden durch eine Warnung in der QuickInfo auf Probleme aufmerksam gemacht. Möglicherweise werden Ihnen auch andere Warnungen angezeigt. Durch das Verschieben des Zeigers können Sie Ihre Anwendung nicht auf einen früheren App-Status zurücksetzen.

1. Drücken Sie die Taste **F5**, um die Ausführung der App fortzusetzen.

    Damit haben Sie das Tutorial erfolgreich abgeschlossen.

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie gelernt, wie Sie den Debugger starten, Code schrittweise durchlaufen und Variablen untersuchen. Sie sollten sich einen allgemeinen Überblick über die Debugger-Funktionen verschaffen und die zugehörigen Links aufrufen, um weitere Informationen hierzu zu erhalten.

> [!div class="nextstepaction"]
> [Tipps und Tricks zum Debugger](../debugger/debugger-tips-and-tricks.md)
