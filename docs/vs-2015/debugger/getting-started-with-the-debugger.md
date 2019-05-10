---
title: Erste Schritte mit dem Debugger | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e093abd5e836bcb7ee236979c00d574a07ecfd3d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60109518"
---
# <a name="getting-started-with-the-debugger"></a>Erste Schritte mit dem Debugger
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der Visual Studio-Debugger ist in jeder Sprache einfach zu verwenden. Wir zeigen Ihnen hier, wie Sie ein einfaches C#-Programm debuggen. Sie können die gleichen Schritte jedoch auch auf andere Sprachen wie z. B. C++ und JavaScript anwenden.  
  
## <a name="BKMK_Start_debugging_a_VS_project"></a> Debuggen eines einfachen C#-Projekts  
 Beginnen wir mit einer einfachen C#-Konsolenanwendung (**Datei / neu / Projekt**, und wählen Sie dann **Visual C#-** und wählen Sie dann **Konsolenanwendung**). Wenn Sie mit Visual Studio noch nie gearbeitet haben, finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer einfachen Anwendung](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md). Die **Main** Methode nur 1 10 Mal auf eine ganzzahlige Variable hinzugefügt und gibt das Ergebnis an die Konsole:  
  
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
  
 Erstellen Sie diesen Code in die **Debuggen** Konfiguration. Diese Konfiguration ist standardmäßig festgelegt. Weitere Informationen zu Konfigurationen finden Sie unter [Grundlagen der Buildkonfiguration](../ide/understanding-build-configurations.md).  
  
 Führen Sie diesen Code im Debugger, indem Sie auf **Debuggen / Debugging starten** (oder **starten** auf der Symbolleiste oder **F5**). Die Anwendung wird nahezu sofort beendet, sodass Sie nicht genau erkennen können, ob etwas an das Konsolenfenster ausgegeben wurde.  
  
 Sie können die Ausführung anhalten, um das Konsolenfenster zu sehen, indem Sie einen Haltepunkt festlegen und die Ausführung schrittweise durchlaufen. Um einen Haltepunkt festzulegen, platzieren Sie den Cursor in die `Console.WriteLine` Zeile, und klicken Sie auf **Debuggen / Neuer Haltepunkt / Funktionshaltepunkt**, oder klicken Sie einfach auf den linken Rand dieser Zeile. Der Haltepunkt sollte wie folgt aussehen:  
  
 ![Festlegen eines Haltepunkts](../debugger/media/getstartedbreakpoint.png "GetStartedBreakpoint")  
  
 Weitere Informationen über Breakpoints finden Sie unter [Verwenden von Haltepunkten](../debugger/using-breakpoints.md).  
  
## <a name="BKMK_Inspect_Variables"></a> Untersuchen Sie Variablen  
 Debuggen von häufig umfasst das Suchen von Variablen, die keine Werte enthalten, die Sie zu einem bestimmten Zeitpunkt zu erwarten. Einige der Möglichkeiten zeigen wir, dass Sie die Variablen überprüfen können.  
  
 Starten Sie das Debuggen erneut. Die Ausführung wird angehalten, bevor der `Console.WriteLine`-Code ausgeführt wird. Sie können dazu führen, dass er ausgeführt wird, indem Sie Ausführung schrittweise durchlaufen (klicken Sie auf **Debuggen / Prozedurschritt über** oder **F10**). In diesem Fall hätten Sie **Einzelschritt** (**F11**) erzielt dasselbe Ergebnis; den Unterschied wird später erläutert. Die Zeile mit der letzten geschweiften Klammer der Methode sollte gelb hervorgehoben sein. Betrachten Sie das Konsolenfenster. Daraufhin sollte **10**.  
  
 Sie können auf zeigen die **"TestInt" erst** Variable, die den aktuellen Wert in einem Datentipp anzeigen.  
  
 ![DBG&#95;Basics&#95;Data&#95;Tips](../debugger/media/dbg-basics-data-tips.png "DBG_Basics_Data_Tips")  
  
 Nur unter dem Codefenster sollte die **"Auto"**, **"lokal"**, und **Watch** Windows. Diese Fenster zeigen die aktuellen Werte der Variablen zum Zeitpunkt der Ausführung. Sowohl die **"Auto"** und **"lokal"** Windows anzeigen **"TestInt" erst** mit einem Wert von **10**.  
  
 ![Auto-Fenster beim Debuggen](../debugger/media/getstartedwindows.png "GetStartedWindows")  
  
 Weitere Informationen über diese Fenster finden Sie unter ["Auto" und "lokal" Windows](../debugger/autos-and-locals-windows.md).  
  
 Sehen wir uns nun an, wie sich der Variablenwert beim Durchlaufen des Programms ändert. Legen Sie einen Haltepunkt auf der `testInt += 1;` Zeile, und das Debuggen neu starten. Sollte angezeigt werden, **"TestInt" erst** in die **"lokal"** und **"Auto"** Windows **0**, und **ich** ist **1**. Wenn Sie fortfahren, Debuggen (**Debuggen / fortfahren**, oder **Weiter** auf der Symbolleiste oder **F5**), sehen Sie, dass der Wert des **"TestInt" erst** Änderungen an **1**, klicken Sie dann **2**und so weiter. Wenn Sie die Änderungen anzeigen möchten, entfernen Sie den Haltepunkt (**Debuggen / umschalten Haltepunkt**, oder klicken Sie auf den Rand), und Debuggen fortsetzen. Wenn Sie alle Haltepunkte entfernen möchten, klicken Sie auf **Debuggen / alle Haltepunkte löschen**, oder **STRG + UMSCHALT + F9**, und klicken Sie auf **Ja** im Dialogfeld mit der Frage **möchten Sie Möchten Sie alle Haltepunkte entfernen?** .  
  
## <a name="stepping-into-and-over-function-calls"></a>Einzel- und Prozedurschritte für Funktionsaufrufe  
 Sie können Code in die Debugger-Anweisung für Anweisung ausführen (**Einzelschritt**) oder Sie können Code ausführen, während der Debugger überspringt die Funktionen (**Prozedurschritt**), schnell an Code, dass weitere Informationen über (du Funktionscode wird noch ausgeführt). Sie können zwischen den beiden Methoden in einer Debugsitzung wechseln.  
  
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
  
 Setzen Sie einen Haltepunkt im `Method1();`-Aufruf in der Main-Methode, und starten Sie das Debuggen. Wenn die Ausführung unterbrochen wird, klicken Sie auf **Debuggen / Einzelschritt** (oder **Einzelschritt** auf der Symbolleiste oder **F11**). Die Ausführung wird an der ersten geschweiften Klammer in "Method1()" erneut unterbrochen:  
  
 ![Code schrittweise](../debugger/media/getstartedstepinto.png "GetStartedStepInto")  
  
 Debuggen beenden und erneut starten und wenn die Ausführung am Haltepunkt unterbrochen wird, klicken Sie auf **Debuggen / Prozedurschritt über** (oder **Prozedurschritt** auf der Symbolleiste oder **F10**). Die Ausführung wird bei `Console.WriteLine("end");` erneut unterbrochen.  
  
 Wenn Sie möchten mehr über das Navigieren im Code mit dem Debugger zu erfahren, finden Sie unter [Navigieren im Code mit dem Debugger](../debugger/navigating-through-code-with-the-debugger.md).
