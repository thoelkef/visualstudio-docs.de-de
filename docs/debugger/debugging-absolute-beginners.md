---
title: Debuggen von Code für absolute Anfänger
description: Wenn Sie erstmals Debuggen, erfahren Sie, einige Grundsätze, damit Sie Ihre app im Debugmodus in Visual Studio ausführen können
ms.custom: ''
ms.date: 07/06/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8cba770195ced84083e67ae42afbef53631e5ba1
ms.sourcegitcommit: 522ba712c0d625e51352506146b0556414681964
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2018
ms.locfileid: "37890213"
---
# <a name="how-to-debug-for-absolute-beginners"></a>Gewusst wie: Debuggen für absolute Anfänger

Ohne Fehler auftreten nicht der Code, den wir als Software-Entwickler schreiben immer es ihm angeforderten Aktionen ausgeführt wurde. Manchmal ist es etwas völlig anderes! In diesem Fall wird die nächste Aufgabe besteht, um herauszufinden, warum ein, und obwohl wir versucht, die nur den Code für die Stunden starren beibehalten werden kann, ist es viel einfacher und effizienter, verwenden ein Tool zum Debuggen oder im debugger.

Ein Debugger, nicht leider etwas, das automatisch alle Probleme oder "Fehler" in unserem Code anzeigen können. *Debuggen von* bedeutet, dass zum Ausführen des Codes schrittweise in ein Tool zum Debuggen wie Visual Studio, um den genauen Punkt zu finden, in dem Sie ein Fehler Programmierung unterlaufen. Sie sich vergegenwärtigen, welche Korrekturen, die Sie in Ihrem Code vornehmen müssen, und die Debugtools ermöglichen temporäre Änderungen vornehmen, um die programmausführung fortgesetzt werden kann.

Verwenden eines Debuggers effektiv ist auch eine Qualifikation, die Zeit- und Vorgehensweise erfahren Sie mehr akzeptiert, jedoch ist letztlich eine wesentliche Aufgabe für alle Softwareentwickler. In diesem Artikel dann wir führen die wichtigsten Aspekte von Debuggen und geben Sie Tipps, die Ihnen den Einstieg erleichtern.

## <a name="clarify-the-problem-by-asking-yourself-the-right-questions"></a>Klären Sie das Problem, Fragen Sie sich mit der richtigen Fragen

Es hilft, um das Problem zu ermitteln, dem Sie in ausgeführt haben, bevor Sie versuchen, das Problem zu beheben. Wir erwarten, dass Sie bereits auf ein Problem in Ihrem Code ausgeführt haben, wäre nicht andernfalls hier versuchen Sie, herauszufinden, wie Sie es Debuggen! Bevor Sie mit dem Debuggen beginnen, stellen Sie daher sicher, dass Sie das Problem identifiziert haben, die, das Sie lösen möchten:

* Was erwarten Sie deinen Code?

* Was ist stattdessen passiert?

    Wenn Sie einen Fehler (Ausnahme) während der Ausführung Ihrer app ausführen, kann die eine gute Sache sein! Eine Ausnahme ist ein unerwartetes Ereignis bei der Ausführung von Code, in der Regel eine Art Fehler auftreten. Ein Tool zum Debuggen sind Sie genau zu der Stelle in Ihrem Code, in dem die Ausnahme aufgetreten ist, und ermöglicht Ihnen, mögliche Lösungen zu untersuchen.

    Wenn etwas anderes aufgetreten ist, was das Symptom des Problems ist? Vermuten Sie bereits, in denen dieses Problem in Ihrem Code aufgetreten ist? Beispielsweise wissen, ob Ihr Code zeigt einen Text an, aber der Text falsch ist, Sie, dass Ihre Daten ungültig ist oder der Code, der den anzuzeigenden Text festlegen, eine Art von Fehler ist. Durch den Code in einem Debugger zu durchlaufen, können Sie jede einzelne Änderung überprüfen, auf Ihre Variablen ermittelt werden, genau, wann und wie falsche Werte zugewiesen werden.

## <a name="examine-your-assumptions"></a>Überprüfen Sie Ihre Annahmen

Bevor Sie einen Fehler oder einen Fehler untersuchen, stellen Sie die Annahmen, die Sie erwarten, dass eine bestimmte Ergebnis vorgenommen. Können zugreifbarkeitsmodifizierer machen es ausgeblendet oder unbekannte Annahmen Identifizieren eines Problems, selbst wenn Sie rechts auf die Ursache des Problems in einem Debugger suchen. Sie müssen möglicherweise eine lange Liste von möglichen Annahmen! Hier sind einige Fragen helfen Ihnen, Ihre Annahmen Herausforderung werden.

* Verwenden Sie die richtige-API (d. h. die Rechte Objekt, -Funktion, Methode oder Eigenschaft)? Eine API, die Sie verwenden möglicherweise nicht, was Sie denken, dass dies der Fall ist. (Nach dem Sie den API-Aufruf im Debugger untersuchen, kann deren Behebung eine Reise in der Dokumentation zur Identifizierung, dass die richtige API erfordern.)

* Verwenden eine API ordnungsgemäß Sie? Vielleicht wird rechts API verwendet, aber nicht in der richtigen Weise verwenden.

* Enthält der Code keine Tippfehler? Einige Tippfehler, wie eine einfache Namen eines Variablennamens, können schwierig sein, insbesondere beim Arbeiten mit Sprachen, die keine Variablen deklariert werden, damit sie verwendet werden erfordern angezeigt wird.

* Sie vornehmen eine Änderung am Code und wird davon ausgegangen, dass sie unabhängig von das Problem ist, die angezeigt werden?

* Sollte ein Objekt oder eine Variable, die einen bestimmten Wert (oder eines bestimmten Typs des Werts) enthalten, die unterscheidet sich von was tatsächlich passiert ist?

* Wissen Sie, dass die Absicht des Codes wird? Häufig ist es schwierig, eine andere Person Debuggen des Codes. Wenn es sich nicht um den Code ist, ist es möglich ist, müssen Sie möglicherweise einarbeiten Ausgaben genau Zweck des Codes ist, bevor Sie es effizient beheben können.

    > [!TIP]
    > Beim Schreiben von Code, anzufangen Sie klein und beginnen Sie mit Code, der funktioniert! (Guter Beispielcode ist hilfreich, hier.) Manchmal ist es einfacher, einen großen oder komplizierteren Satz von Code zu beheben, indem Sie ein kleines Stück des Codes, die der Kernaufgabe veranschaulicht, die Sie erreichen möchten ab. Anschließend können Sie ändern oder fügen Code hinzu, inkrementell an jedem Punkt auf Fehler testen.

Durch hinterfragen der Annahmen, können Sie die Zeit reduzieren, dauert es um ein Problem im Code zu suchen. Sie können auch die Zeit reduzieren, dauert es um ein Problem zu beheben.

## <a name="step-through-your-code-in-debugging-mode-to-find-where-the-problem-occurred"></a>Durchlaufen Sie Ihren Code im Debugmodus befindet, um zu suchen, in dem das Problem aufgetreten ist

Wenn Sie normalerweise eine app ausführen, sehen Sie Fehler und falsche Ergebnisse, nur, nachdem der Code ausgeführt wurde. Ein Programm kann auch unerwartet beendet werden, ohne den Gründen dafür.

Ausführen einer app in einen Debugger, so genannte *Debugmodus*, bedeutet, dass der Debugger alles, was überwacht aktiv, das geschieht, wenn die Anwendung ausgeführt wird. Außerdem können Sie zum Anhalten der app zu irgendeinem Zeitpunkt aus, um dessen Zustand zu untersuchen und durchlaufen Sie anschließend auf Ihren Code Zeile für Zeile jedes Detail überwachen, während es geschieht.

In Visual Studio debugging-Modus über den eingegebenen **F5** (oder die **Debuggen** > **Debuggen starten** Menübefehl oder die **Debugging starten**  Schaltfläche ![Debuggen starten](../debugger/media/dbg-tour-start-debugging.png "Debuggen starten")) in der Debug-Symbolleiste. Wenn Ausnahmen auftreten, öffnet Visual Studio Ausnahme-Hilfe den genauen Punkt, in dem die Ausnahme aufgetreten ist, und bietet weitere hilfreiche Informationen.

Wenn Sie eine Ausnahme nicht erhalten haben, verfügen Sie wahrscheinlich eine gute Idee, wo Sie für das Problem in Ihrem Code zu suchen. Diese benutzen Sie *Haltepunkte* mit dem Debugger, damit Sie eine Möglichkeit, Ihren Code gründlich untersuchen können. Haltepunkte sind eine einfache und wichtige Funktion zum zuverlässigen Debuggen. Ein Haltepunkt gibt an, in dem den ausgeführten Code in Visual Studio anhalten soll, sodass Sie können einen Blick auf die Werte von Variablen, oder das Verhalten von Arbeitsspeicher oder die Reihenfolge, in der Code ausgeführt wird.

In Visual Studio können Sie schnell einen Haltepunkt festlegen, indem Sie auf den linken Rand neben einer Codezeile. Oder setzen Sie den Cursor in einer Zeile, und drücken Sie **F9**.

Um diese Konzepte zu verdeutlichen, führen wir Sie durch den Beispielcode, die bereits mehrere Fehler enthält. Wir verwenden C#-, debugging-Funktionen gelten jedoch für Visual Basic, C++, JavaScript, Python und anderen unterstützten Sprachen.

### <a name="create-a-sample-app-with-some-bugs"></a>Erstellen Sie eine Beispiel-app (mit einigen Fehlern)

Als Nächstes erstellen wir eine Anwendung, die einige Fehler aufweist.

1. Sie benötigen Visual Studio installiert und entweder die. **NET Desktopentwicklung** arbeitsauslastung oder der. **NET Core plattformübergreifende Entwicklung** Workload installiert ist, je nachdem welche app Geben Sie für die erstellen möchten.

    Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) kostenlos herunterladen.

    Wenn Sie verwenden möchten, installieren Sie die Workload jedoch bereits über Visual Studio, klicken Sie auf **Tools** > **Tools und Features abrufen**. Der Visual Studio-Installer wird gestartet. Wählen Sie die. **NET Desktopentwicklung** (oder. **NET Core plattformübergreifende Entwicklung**) Workload, wählen Sie dann **ändern**.

1. Öffnen Sie Visual Studio, und wählen Sie dann **Datei** > **neu** > **Projekt**.

1. Wählen Sie eine Vorlage für Ihren Anwendungscode.

    Für .NET Framework in der **neues Projekt** Dialogfeld wählen **Visual C#-**, **Windows Desktop** aus dem Abschnitt der installierten Vorlagen, und klicken Sie dann im mittleren Bereich die Option  **Konsolen-App ((.NET Framework)**.

    Für .NET Core in der **neues Projekt** Dialogfeld wählen **Visual C#-**, **.NET Core** wählen Sie aus dem Abschnitt der installierten Vorlagen, und klicken Sie dann im mittleren Bereich  **Konsolen-App ((.NET Core)**.

    Wenn Sie diese Vorlage nicht angezeigt wird, müssen Sie die erforderliche Workload installieren (siehe vorherigen Schritten).

1. In der **Namen** Feld **ConsoleApp-FirstApp** , und klicken Sie auf **OK**.

    Visual Studio erstellt das Konsolenprojekt, die im Projektmappen-Explorer im rechten Bereich angezeigt wird.

1. In *"Program.cs"*, ersetzen Sie den Standardcode durch folgenden Code:

    ```csharp
    using System;
    using System.Collections.Generic;
    
    namespace ConsoleApp_FirstApp
    {
        class Program
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Welcome to Galaxy News!");
                IterateThroughList();
                Console.ReadKey();
            }
    
            private static void IterateThroughList()
            {
                var theGalaxies = new List<Galaxy>
            {
                new Galaxy() { Name="Tadpole", MegaLightYears=400, GalaxyType=new GType('S')},
                new Galaxy() { Name="Pinwheel", MegaLightYears=25, GalaxyType=new GType('S')},
                new Galaxy() { Name="Cartwheel", MegaLightYears=500, GalaxyType=new GType('L')},
                new Galaxy() { Name="Small Magellanic Cloud", MegaLightYears=.2, GalaxyType=new GType('I')},
                new Galaxy() { Name="Andromeda", MegaLightYears=3, GalaxyType=new GType('S')},
                new Galaxy() { Name="Maffei 1", MegaLightYears=11, GalaxyType=new GType('E')}
            };
    
                foreach (Galaxy theGalaxy in theGalaxies)
                {
                    Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
                }
    
                // Expected Output:  
                //  Tadpole  400,  Spiral 
                //  Pinwheel  25,  Spiral 
                //  Cartwheel, 500,  Lenticular
                //  Small Magellanic Cloud .2,  Irregular
                //  Andromeda  3,  Spiral
                //  Maffei 1,  11,  Elliptical
            }
        }
    
        public class Galaxy
        {
            public string Name { get; set; }
    
            public double MegaLightYears { get; set; }
            public object GalaxyType { get; set; }
    
        }
    
        public class GType
        { 
            public GType(char type)
            {
                switch(type)
                {
                    case 'S':
                        MyGType = Type.Spiral;
                        break;
                    case 'E':
                        MyGType = Type.Elliptical;
                        break;
                    case 'l':
                        MyGType = Type.Irregular;
                        break;
                    case 'L':
                        MyGType = Type.Lenticular;
                        break;
                    default:
                        break;
                }
            }
            public object MyGType { get; set; }
            private enum Type { Spiral, Elliptical, Irregular, Lenticular}
        }
    }
    ```

    Unsere Absicht, damit dieser Code ist der Galaxy-Name, den Abstand und die Galaxie und den Typ des Galaxy alle in einer Liste angezeigt. Um zu debuggen, ist es wichtig, die Absicht des Codes zu verstehen. So sieht das Format für eine Zeile aus der Liste, die wir in der Ausgabe angezeigt werden soll:

    *Name des Galaxy*, *Abstand*, *Galaxy Typ*.

### <a name="run-the-app"></a>Ausführen der App

1. Drücken Sie **F5** oder **Debuggen starten** Schaltfläche ![Debuggen starten](../debugger/media/dbg-tour-start-debugging.png "Debuggen starten") befindet Sie sich in der Debug-Symbolleiste über dem Codeeditor.

    Die app wird gestartet und es sind keine Ausnahmen, die uns vom Debugger angezeigt. Die Ausgabe im Konsolenfenster angezeigten ist jedoch nicht Ihren Erwartungen. Hier ist die erwartete Ausgabe:

    ```
    Tadpole  400,  Spiral 
    Pinwheel  25,  Spiral 
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,  Irregular
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

    Allerdings sehen Sie dies stattdessen:

    ```
    Tadpole  400,  ConsoleApp_FirstApp.GType 
    Pinwheel  25,  ConsoleApp_FirstApp.GType 
    Cartwheel, 500,  ConsoleApp_FirstApp.GType
    Small Magellanic Cloud .2,  ConsoleApp_FirstApp.GType
    Andromeda  3,  ConsoleApp_FirstApp.GType
    Maffei 1, 11,  ConsoleApp_FirstApp.GType
    ```

    Suchen die Ausgabe und den Code, wissen wir, die `GType` ist der Name der Klasse, die den Typ des Galaxy speichert. Es wird versucht, den tatsächlichen Galaxy-Typ (z. B. "Spirale"), zeigen nicht die Klassennamen.

### <a name="debug-the-app"></a>Debuggen der app

1. Legen Sie einen Haltepunkt mit der app, die noch ausgeführt wird, indem Sie auf den linken Rand neben der `Console.WriteLine` Methodenaufruf in dieser Codezeile.

    ```csharp
    foreach (Galaxy theGalaxy in theGalaxies)
    {
        Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
    }    
    ```

    Wenn Sie den Haltepunkt festlegen, wird ein roter Punkt am linken Rand angezeigt.

    Da wir ein Problem in der Ausgabe sehen, beginnen wir Debuggen anhand des vorangehenden Codes, der die Ausgabe im Debugger festlegt.

1. Klicken Sie auf die **Neustart** ![App neu starten](../debugger/media/dbg-tour-restart.png "RestartApp") der Debug-Symbolleiste (**STRG** + **UMSCHALT**   +  **F5**).

    Die app hält die Ausführung am Haltepunkt, den Sie festlegen. Die gelben mit gibt an, in denen der Debugger angehalten ist (die gelbe Zeile des Codes wurde noch nicht ausgeführt).

1. Zeigen Sie auf die `GalaxyType` Erweitern von Variablen, die auf der rechten Seite, und klicken Sie dann auf der linken Seite, der das Schraubenschlüsselsymbol `theGalaxy.GalaxyType`. Sie sehen, dass `GalaxyType` enthält eine Eigenschaft `MyGType`, und legen Sie den Wert der Eigenschaft ist auf `Spiral`.

    ![Überprüfen Sie eine variable](../debugger/media/beginners-inspect-variable.png)

    "Spirale" ist tatsächlich der richtige Wert an, den Sie erwartet, die auf der Konsole auszugeben. Es ist also ein guter Ausgangspunkt, dass Sie diesen Wert in diesem Code beim Ausführen der app zugreifen können. In diesem Szenario verwenden wir die falsche-API. Es wird angezeigt, wenn wir dieses Problem beim Ausführen von Code im Debugger beheben können.

1. In den gleichen Code, während des Debuggens weiterhin, positionieren Sie den Cursor am Ende der `theGalaxy.GalaxyType` ändern sie die `theGalaxy.GalaxyType.MyGType`. Obwohl Sie diese Änderung vornehmen können, zeigt der Code-Editor, eine Fehlermeldung, dass sie diesen Code kompilieren kann nicht.

    ![Syntaxfehler](../debugger/media/beginners-edit.png)

1. Klicken Sie auf **bearbeiten** in die **bearbeiten und Fortfahren** Meldungsfeld. Sie sehen eine Fehlermeldung in nun der **Fehlerliste** Fenster. Der Fehler gibt an, dass die `'object'` enthält keine Definition für `MyGType`.

    ![Syntaxfehler](../debugger/media/beginners-no-definition.png)

    Obwohl wir jede Galaxy mit einem Objekt des Typs festgelegt `GType` (IValidator.h der `MGType` Eigenschaft), der Debugger erkennt keine der `theGalaxy` -Objekt als ein Objekt vom Typ `GType`. Was ist los? Möchten Sie über Code zu suchen, die der Galaxy-Typ festgelegt. Wenn Sie dies tun, Sie sehen, dass die `GType` -Klasse verfügt sicherlich über eine Eigenschaft des `MyGType`, ist jedoch etwas nicht rechts. Die Fehlermeldung zum `object` erweist sich die Anhaltspunkt; der Language-Interpreter, der Typ erscheint wie ein Objekt des Typs `object` anstelle eines Objekts vom Typ `GType`.

1. Durch den Code im Zusammenhang mit dem Typ Galaxy suchen, finden Sie die `GalaxyType` Eigenschaft der `Galaxy` Klasse angegeben ist, als `object` anstelle von `GType`.

    ```csharp
    public object GalaxyType { get; set; }     
    ```

1. Ändern des vorangehenden Codes folgendermaßen:

    ```csharp
    public GType GalaxyType { get; set; }     
    ```

1. Klicken Sie auf die **Neustart** ![App neu starten](../debugger/media/dbg-tour-restart.png "RestartApp") der Debug-Symbolleiste (**STRG** + **UMSCHALT**   +  **F5**) Code neu kompilieren und neu starten.

    Nun, wenn der Debugger hält bei `Console.WriteLine`, können Sie den Mauszeiger `theGalaxy.GalaxyType.MyGType`, und sehen Sie sich, die der Wert ordnungsgemäß festgelegt ist.

1. Entfernen Sie den Haltepunkt durch Klicken auf den Haltepunkt Kreis am linken Rand (oder mit der rechten Maustaste, und wählen Sie **Haltepunkt** > **Breakpoint löschen**), und drücken Sie dann die **F5** um den Vorgang fortzusetzen.

    Die app ausgeführt wird und das Ergebnis angezeigt. Es sieht ziemlich gut, aber Sie dabei beachten Sie bitte; die Galaxie kleine Magellanic Cloud als eine unregelmäßige Galaxy in der Konsolenausgabe angezeigt wird, wird erwartet, aber es überhaupt kein Galaxy-Typ zeigt.

    ```
    Tadpole  400,  Spiral 
    Pinwheel  25,  Spiral 
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

1. Legen Sie einen Haltepunkt in dieser Zeile des Codes.

    ```csharp
    public GType(char type)
    ```

    Dieser Code ist, in dem der Galaxy-Typ festgelegt ist, möchten wir eine näher ansehen.

1. Klicken Sie auf die **Neustart** ![App neu starten](../debugger/media/dbg-tour-restart.png "RestartApp") der Debug-Symbolleiste (**STRG** + **UMSCHALT**   +  **F5**) neu starten.

    Der Debugger hält bei der Codezeile, in dem Sie den Haltepunkt festgelegt.  

1. Zeigen Sie auf die `type` Variable. Sehen Sie einen Wert von `S` (befolgen Sie den Zeichencode). Gesuchte Wert `I`, da Sie wissen, das ist eine unregelmäßige Galaxy-Typ.

1. Drücken Sie **F5** und zeigen Sie auf die `type` Variable erneut aus. Wiederholen Sie diesen Schritt, bis Sie sehen, dass der Wert `I` in die `type` Variable.

    ![Überprüfen Sie eine variable](../debugger/media/beginners-inspecting-data.png)

1. Drücken Sie nun **F11** (**Debuggen** > **Einzelschritt** oder **Einzelschritt** der Debug-Symbolleiste).

    **F11** wechselt den Debugger eine Anweisung zu einem Zeitpunkt (und Code ausführt). **F10** (**Prozedurschritt**) einen ähnlichen Befehl ein, und beide sind äußerst nützlich, wenn zum Verwenden des Debuggers kennen zu lernen.

1. Drücken Sie **F11** bis Sie auf die Codezeile in das Beenden der `switch` -Anweisung für einen Wert von "I". Hier sehen Sie eine klare Problem durch einen Tippfehler. Sie erwartet, dass den Code, fahren Sie fort, um, in dem er festlegt `MyGType` als ein irregulär Galaxy-Typ, aber der Debugger stattdessen überspringt diesen Code vollständig und hält bei der `default` Teil der `switch` Anweisung.

    ![Suchen Sie einen Tippfehler](../debugger/media/beginners-typo.png)

    Betrachten den Code, durch einen Tippfehler im werden daraufhin die `case 'l'` Anweisung. Es muss `case 'I'`.

1. Klicken Sie in den Code für `case 'l'`, und Ersetzen Sie ihn mit ' Case 'I'.

1. Entfernen Sie den Haltepunkt, und klicken Sie dann auf die **Neustart** Schaltfläche, um die app neu starten.

    Die Fehler nun behoben werden, und Sie sehen, dass die Ausgabe, die Sie erwarten, dass!

    Drücken Sie eine beliebige Taste, um die app fertig zu stellen.

## <a name="summary"></a>Zusammenfassung

Wenn Sie ein Problem angezeigt wird, verwenden Sie den Debugger und [Schritt Befehle](../debugger/navigating-through-code-with-the-debugger.md) wie z. B. **F10** und **F11** den Codebereich mit dem Problem zu finden.

> [!NOTE]
> Wenn es schwierig ist, den Codebereich identifizieren, in dem das Problem auftritt, legen einen Haltepunkt im Code, der ausgeführt wird, bevor das Problem tritt auf, und klicken Sie dann diese Befehle verwenden, bis Sie sehen, dass das Problem Manifest. Sie können auch [Ablaufverfolgungspunkte](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints) zum Protokollieren von Nachrichten an die **Ausgabe** Fenster. Von protokollierten Nachrichten suchen (und bemerken, welche Nachrichten noch nicht angemeldet wurden), können Sie häufig den Codebereich mit dem Problem isolieren. Sie müssen möglicherweise diesen Vorgang mehrmals wiederholen, um es einzugrenzen.

Wenn Sie den Codebereich mit dem Problem finden, verwenden Sie den Debugger untersuchen. Um die Ursache eines Problems zu finden, überprüfen Sie die problematische Code während der Ausführung Ihrer app im Debugger:

* [Untersuchen Sie Variablen](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) und überprüfen Sie, ob sie den Typ der Werte enthalten, die sie enthalten soll. Wenn Sie einen falschen Wert finden, herauszufinden, wo der ungültige Wert festgelegt wurde (um zu suchen, in denen der Wert festgelegt wurde, müssen möglicherweise entweder den Debugger starten, sehen Sie sich die [Aufrufliste](../debugger/how-to-use-the-call-stack-window.md), oder beides).

* Überprüfen Sie, ob Ihre Anwendung den Code ausführt, den Sie erwarten. (Z. B. in der beispielanwendung, erwartet wurde den Code für die Switch-Anweisung für den Typ des Galaxy festzulegen, irregulär, aber die app wurde übersprungen, den Code der Tippfehler.)

> [!TIP]
> Sie können einen Debugger verwenden, können Sie die Fehler zu finden. Ein Tool zum Debuggen finden Fehler *für Sie* nur dann, wenn die Absicht des Codes bekannt ist. Ein Tool kann nur die Absicht des Codes bekannt, wenn Sie als Entwickler können diese Absicht Ausdrücken. Schreiben von [Komponententests](../test/improve-code-quality.md) ist, wie Sie dies tun.

## <a name="next-steps"></a>Nächste Schritte

In diesem Artikel haben Sie gelernt, dass einige allgemeine Konzepte zum Debuggen. Als Nächstes können Sie beginnen, lernen, wie Sie mit Visual Studio debuggen.

> [!div class="nextstepaction"]
> [Debugger – Featuretour](../debugger/debugger-feature-tour.md)
