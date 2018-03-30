---
title: Erste Schritte mit dem Debugger in Visual Studio | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 02/07/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: get-started-article
ms.assetid: 0b3138c4-b840-446a-a15c-10ed8e2dd050
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 171b07d453c81883354848f70458bab39daa313e
ms.sourcegitcommit: 29ef88fc7d1511f05e32e9c6e7433e184514330d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2018
---
# <a name="get-started-with-the-visual-studio-debugger"></a>Erste Schritte mit Visual Studio-Debugger
Der Visual Studio-Debugger ist in jeder Sprache einfach zu verwenden. Hier zeigen wir, wie ein einfaches C#-Programm debuggen, aber Sie können die gleichen Schritte für Code in anderen Sprachen wie C++ und JavaScript anwenden.

Um ein Video mit ähnlichen Funktionen beobachten zu können, finden Sie unter [erste Schritte mit dem Debugger](https://www.youtube.com/watch?v=FtGCi5j30YU&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=6).
  
##  <a name="BKMK_Start_debugging_a_VS_project"></a> Debuggen eines einfachen C#-Projekts  
 Beginnen wir mit einer einfachen C#-Konsolenanwendung (**Datei > Neu > Projekt**, und wählen Sie dann **Visual C#-** und dann **Konsolenanwendung**). Wenn Sie mit Visual Studio noch nie gearbeitet haben, finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer einfachen Anwendung](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md). Die **Main** Methode nur 1 10 Mal an eine IntegerVariable hinzugefügt und das Ergebnis in der Konsole ausgegeben:  
  
```csharp  
static void Main(string[] args)  
{  
    int testInt = 0;  
    for (int i = 1; i <= 10; i++)  
    {  
        testInt += 1;  
    }  
    Console.WriteLine(testInt);  
}  
```  
  
 Erstellen Sie diesen Code in die **Debuggen** Konfiguration. Diese Konfiguration ist standardmäßig festgelegt. Weitere Informationen zu Konfigurationen finden Sie unter [Grundlagen zu Buildkonfigurationen](../ide/understanding-build-configurations.md).  
  
 Führen Sie diesen Code im Debugger, indem Sie auf **Debuggen > Debuggen starten** (oder **starten** auf der Symbolleiste oder **F5**). Die Anwendung sollte nahezu sofort beendet, sodass Sie genau erkennen können, ob etwas an das Konsolenfenster ausgegeben wurde.  
  
 Sie können die Ausführung anhalten, um das Konsolenfenster zu sehen, indem Sie einen Haltepunkt festlegen und die Ausführung schrittweise durchlaufen. Um einen Haltepunkt festzulegen, platzieren Sie den Cursor in die `Console.WriteLine` Zeile, und klicken Sie auf **Debuggen > Neuer Haltepunkt > Funktionshaltepunkt**, oder klicken Sie einfach auf den linken Rand der gleichen Zeile. Der Haltepunkt sollte wie folgt aussehen:  
  
 ![Festlegen eines Haltepunkts](../debugger/media/getstartedbreakpoint.png "GetStartedBreakpoint")  
  
 Weitere Informationen über Breakpoints finden Sie unter [mithilfe von Haltepunkten](../debugger/using-breakpoints.md).  
  
##  <a name="BKMK_Inspect_Variables"></a> Überprüfung von Variablen  
 Debuggen von häufig gehört das Auffinden von Variablen, die keine Werte enthalten, die Sie zu einem bestimmten Zeitpunkt zu erwarten. Wir zeigen einige Möglichkeiten, um Variablen überprüfen.  
  
 Starten Sie das Debuggen erneut. Die Ausführung wird angehalten, bevor der `Console.WriteLine`-Code ausgeführt wird. Sie können dazu führen, dass es ausführen, indem Sie die Ausführung schrittweise durchlaufen (klicken Sie auf **Debuggen > Prozedurschritt** oder **F10**). In diesem Fall hätten Sie **Einzelschritt** (**F11**) und erhalten dasselbe Ergebnis; den Unterschied wird weiter unten erläutert. Die Zeile mit der letzten geschweiften Klammer der Methode sollte gelb hervorgehoben sein. Betrachten Sie das Konsolenfenster. Daraufhin sollte **10**.  
  
 Können Sie den Mauszeiger die **"TestInt"** Variable, die den aktuellen Wert in einem Datentipp anzeigen.  
  
 ![DBG&#95;Basics&#95;Data&#95;Tips](../debugger/media/dbg_basics_data_tips.png "DBG_Basics_Data_Tips")  
  
 Direkt unterhalb der Codefenster sollte die **"Auto"**, **"lokal"**, und **Überwachen** Windows. Diese Fenster zeigen die aktuellen Werte der Variablen zum Zeitpunkt der Ausführung. Sowohl die **"Auto"** und **"lokal"** Windows anzeigen **"TestInt"** mit einem Wert von **10**.  
  
 ![Fenster "Auto" beim Debuggen](../debugger/media/getstartedwindows.png "GetStartedWindows")  
  
 Weitere Informationen zu diesen Fenstern finden Sie unter ["Auto" und das Fenster "lokal"](../debugger/autos-and-locals-windows.md).  
  
 Sehen wir uns an, wie sich der Wert der Variable ändert, wie wir des Programms durchlaufen. Festlegen eines Haltepunkts auf die `testInt += 1;` Zeile und den Debugvorgang neu starten. Sollte angezeigt werden, **"TestInt"** in der **"lokal"** und **"Auto"** Windows **0**, und **ich** ist **1**. Wenn Sie das Debuggen fortsetzen (**Debuggen > Fortfahren**, oder **Fortfahren** auf der Symbolleiste oder **F5**), Sie sehen, dass der Wert der **"TestInt"** Änderungen an **1**, klicken Sie dann **2**und so weiter. Wenn Sie die Änderungen nicht weiter anzeigen möchten, entfernen Sie den Haltepunkt (**Debuggen > Haltepunkt ein/aus**, oder klicken Sie am Rand darauf), und mit dem Debuggen fortfahren. Wenn Sie alle Haltepunkte entfernen möchten, klicken Sie auf **Debuggen > alle Breakpoints löschen**, oder **STRG + UMSCHALT + F9**, und klicken Sie auf **Ja** im Dialogfeld mit der Frage **führen Möchten Sie alle Haltepunkte entfernen?** .  
  
## <a name="stepping-into-and-over-function-calls"></a>Einzel- und Prozedurschritte für Funktionsaufrufe  
 Sie können Code in der Debugger-Anweisung für Anweisung ausführen (**Einzelschritt**) oder Sie können Code ausführen, während der Debugger überspringt die Funktionen (**Prozedurschritt**), schnell auf Code zugreifen können, dass Sie mehr (interessiert sind Funktionscode wird immer noch ausgeführt). Sie können zwischen beiden Methoden in einer Debugsitzung wechseln.  
  
 Um den Unterschied zwischen **Einzelschritt** und **Prozedurschritt**, müssen wir eine Methode hinzufügen, die durch eine andere Methode aufgerufen wird. Fügen Sie der C#-Anwendung eine Methode hinzu, und rufen Sie diese von der Main-Methode auf. Der Code sollte in etwa wie folgt aussehen:  
  
```csharp  
static void Main(string[] args)  
{  
    Method1();  
    Console.WriteLine("end");  
}  
  
private static void Method1()  
{  
    Console.WriteLine("in Method1");  
}  
```  
  
 Setzen Sie einen Haltepunkt im `Method1();`-Aufruf in der Main-Methode, und starten Sie das Debuggen. Wenn die Ausführung unterbrochen wird, klicken Sie auf **Debuggen > Einzelschritt** (oder **Einzelschritt** auf der Symbolleiste oder **F11**). Die Ausführung wird an der ersten geschweiften Klammer in "Method1()" erneut unterbrochen:  
  
 ![Schrittweise Ausführung von Code](../debugger/media/getstartedstepinto.png "GetStartedStepInto")  
  
 Debuggen beenden und erneut starten und wenn die Ausführung am Haltepunkt unterbrochen wird, klicken Sie auf **Debuggen > Prozedurschritt** (oder **Prozedurschritt** auf der Symbolleiste oder **F10**). Die Ausführung wird bei `Console.WriteLine("end");` erneut unterbrochen.  
  
 Wenn Sie möchten wissen, Weitere Informationen zum Navigieren in Code mit dem Debugger, finden Sie unter [Navigieren im Code mit dem Debugger](../debugger/navigating-through-code-with-the-debugger.md).