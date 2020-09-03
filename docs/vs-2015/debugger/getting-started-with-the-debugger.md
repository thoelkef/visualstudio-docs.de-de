---
title: Einstieg in den Debugger | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202306"
---
# <a name="getting-started-with-the-debugger"></a>Erste Schritte mit dem Debugger
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der Visual Studio-Debugger ist in jeder Sprache einfach zu verwenden. Wir zeigen Ihnen hier, wie Sie ein einfaches C#-Programm debuggen. Sie können die gleichen Schritte jedoch auch auf andere Sprachen wie z. B. C++ und JavaScript anwenden.  
  
## <a name="debug-a-basic-c-project"></a><a name="BKMK_Start_debugging_a_VS_project"></a> Debuggen eines grundlegenden c#-Projekts  
 Beginnen wir mit einer einfachen c#-Konsolenanwendung (**Datei/neu/Projekt**, wählen Sie **Visual c#** aus, und wählen Sie dann **Konsolenanwendung**aus). Wenn Sie noch nie mit Visual Studio gearbeitet haben, finden Sie weitere Informationen unter Exemplarische Vorgehensweise [: Erstellen einer einfachen Anwendung](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md). Die **Main** -Methode fügt eine ganzzahlige Variable 10 Mal nur 1 hinzu und druckt das Ergebnis in der Konsole:  
  
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
  
 Erstellen Sie diesen Code in der **Debugkonfiguration** . Diese Konfiguration ist standardmäßig festgelegt. Weitere Informationen zu Konfigurationen finden Sie Untergrund Legendes zu [Buildkonfigurationen](../ide/understanding-build-configurations.md).  
  
 Führen Sie diesen Code im Debugger aus, indem Sie auf **Debuggen > Debuggen starten** klicken (oder auf der Symbolleiste auf **starten** oder **F5** Die Anwendung wird nahezu sofort beendet, sodass Sie nicht genau erkennen können, ob etwas an das Konsolenfenster ausgegeben wurde.  
  
 Sie können die Ausführung anhalten, um das Konsolenfenster zu sehen, indem Sie einen Haltepunkt festlegen und die Ausführung schrittweise durchlaufen. Um einen Haltepunkt festzulegen, platzieren Sie den Cursor in der `Console.WriteLine` Zeile, und klicken Sie auf **Debuggen/neuer Haltepunkt/Funktions Haltepunkt**, oder klicken Sie einfach auf den linken Rand in derselben Zeile. Der Haltepunkt sollte wie folgt aussehen:  
  
 ![Festlegen eines Breakpoints](../debugger/media/getstartedbreakpoint.png "Getstartedbreakpoint")  
  
 Weitere Informationen zu Breakpoints finden Sie unter [Verwenden von Breakpoints](../debugger/using-breakpoints.md).  
  
## <a name="inspect-variables"></a><a name="BKMK_Inspect_Variables"></a> Variablen überprüfen  
 Das Debuggen umfasst häufig das Suchen von Variablen, die nicht die von Ihnen erwarteten Werte an einem bestimmten Punkt enthalten. Wir zeigen Ihnen einige Möglichkeiten, Variablen zu überprüfen.  
  
 Starten Sie das Debuggen erneut. Die Ausführung wird angehalten, bevor der `Console.WriteLine`-Code ausgeführt wird. Sie können dies ausführen, indem Sie Schritt für Schritt ausführen (Klicken Sie auf **Debuggen/Prozedur Schritt** oder **F10**). In diesem Fall können Sie "Einzel **Schritt** " (**F11**) auswählen und das gleiche Ergebnis erhalten. Wir erläutern den Unterschied zu einem späteren Zeitpunkt. Die Zeile mit der letzten geschweiften Klammer der Methode sollte gelb hervorgehoben sein. Betrachten Sie das Konsolenfenster. Es sollte **10**angezeigt werden.  
  
 Sie können mit dem Mauszeiger auf die **TestInt** -Variable zeigen, um den aktuellen Wert in einem Datentipp anzuzeigen.  
  
 ![Dbg&#95;Grundlagen&#95;Daten&#95;Tipps](../debugger/media/dbg-basics-data-tips.png "DBG_Basics_Data_Tips")  
  
 Direkt unterhalb des Code Fensters sollten die Fenster Auto, lokal **und über** **Wachen** **angezeigt werden.** Diese Fenster zeigen die aktuellen Werte der Variablen zum Zeitpunkt der Ausführung. Sowohl das **Auto-als auch das** **lokale** Fenster zeigen **TestInt** mit dem Wert **10**an.  
  
 ![Auto-Fenster beim Debuggen](../debugger/media/getstartedwindows.png "Getstartedwindows")  
  
 Weitere Informationen zu diesen Fenstern finden Sie unter Auto [-und lokal Fenster](../debugger/autos-and-locals-windows.md).  
  
 Sehen wir uns nun an, wie sich der Variablenwert beim Durchlaufen des Programms ändert. Legen Sie einen Haltepunkt in der `testInt += 1;` Zeile fest, und starten Sie das Debugging erneut. Sie sollten sehen, dass **TestInt** in **den Fenstern** "lokal **" und "** Auto" den Wert " **0**" hat und **1** **ist.** Wenn Sie das Debuggen fortsetzen (**Debuggen/fortfahren**oder **fortfahren** auf der Symbolleiste oder **F5**), können Sie sehen, dass der Wert von **TestInt** in **1**, dann **2**usw. geändert wird. Wenn Sie sich diese Änderungen nicht ansehen möchten, entfernen Sie den Haltepunkt (**Debuggen/Haltepunkt ein/** aus, oder klicken Sie am Rand darauf), und fahren Sie mit dem Debuggen fort. Wenn Sie alle Haltepunkte entfernen möchten, klicken Sie auf **Debuggen/alle Haltepunkte löschen**oder **STRG + UMSCHALT + F9**, und klicken Sie im Dialogfeld, in dem Sie gefragt werden möchten **Sie alle Breakpoints entfernen?** auf **Ja** .  
  
## <a name="stepping-into-and-over-function-calls"></a>Einzel- und Prozedurschritte für Funktionsaufrufe  
 Sie können Code in der Anweisung-by-Anweisung des Debuggers (Einzel**Schritt**) ausführen, oder Sie können Code ausführen, während der Debugger Funktionen überspringt (Prozedur**Schritt**), um schnell zu Code zu gelangen, an dem Sie interessiert sind (Funktionscode wird noch ausgeführt). Sie können in derselben Debugsitzung zwischen beiden Methoden wechseln.  
  
 Um den Unterschied zwischen Einzel **Schritt** und Prozedur **Schritt**anzuzeigen, müssen wir eine Methode hinzufügen, die von einer anderen Methode aufgerufen wird. Fügen Sie der C#-Anwendung eine Methode hinzu, und rufen Sie diese von der Main-Methode auf. Der Code sollte in etwa wie folgt aussehen:  
  
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
  
 Setzen Sie einen Haltepunkt im `Method1();`-Aufruf in der Main-Methode, und starten Sie das Debuggen. Wenn die Ausführung unterbrochen wird, klicken Sie auf **Debuggen/Einzelschritt** (oder Einzel **Schritt** auf der Symbolleiste oder **F11**). Die Ausführung wird an der ersten geschweiften Klammer in "Method1()" erneut unterbrochen:  
  
 ![Schritt-in-Code](../debugger/media/getstartedstepinto.png "Getstartedstepinto")  
  
 Beenden Sie das Debuggen, und starten Sie es erneut. wenn die Ausführung am Haltepunkt unterbrochen wird, klicken Sie auf **Debuggen/Prozedur Schritt** (oder über **springen auf der** Symbolleiste oder **F10**). Die Ausführung wird bei `Console.WriteLine("end");` erneut unterbrochen.  
  
 Weitere Informationen zum Navigieren im Code mit dem Debugger finden Sie unter [Navigieren im Code mit dem Debugger](../debugger/navigating-through-code-with-the-debugger.md).
