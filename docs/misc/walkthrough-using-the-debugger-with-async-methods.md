---
title: "Exemplarische Vorgehensweise: Verwenden des Debuggers mit Async-Methoden | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Async-Funktion, Verwenden des Debuggers"
  - "Await-Operator, Verwenden des Debuggers"
  - "Einzelschritt (Befehl), Bei Await-Operator"
  - "Ausführen bis Rücksprung (Befehl), In Async-Methode"
  - "Prozedurschritt (Befehl), Bei Await-Operator"
ms.assetid: 5adb2531-3f09-4b7e-8baa-29de80abee6e
caps.latest.revision: 23
caps.handback.revision: 23
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
---
# Exemplarische Vorgehensweise: Verwenden des Debuggers mit Async-Methoden
Mithilfe der Async\-Funktion können Sie asynchrone Methoden aufrufen, ohne Rückrufe verwenden oder den Code über mehrere Methoden oder Lambda\-Ausdrücke teilen zu müssen.  Um synchronen Code asynchron auszuführen, rufen Sie eine asynchrone Methode anstelle einer synchronen Methode auf und fügen dem Code einige Schlüsselwörter hinzu.  Weitere Informationen finden Sie unter [Asynchrone Programmierung mit Async und Await](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md).  
  
 Im Visual Studio\-Debugger können Sie die Befehle **Einzelschritt**, **Prozedurschritt** und **Ausführen bis Rücksprung** mit der `Async`\-Funktion verwenden.  Sie können auch weiterhin Haltepunkte verwenden, besonders um die Ablaufsteuerung bei einer Anweisung anzuzeigen, die einen await\-Operator enthält.  In dieser exemplarischen Vorgehensweise führen Sie folgende Aufgaben aus, die in einer beliebigen Reihenfolge ausgeführt werden können.  
  
-   Veranschaulichen Sie die Ablaufsteuerung an einer await\-Anweisung mithilfe von Haltepunkten.  
  
-   Erklären Sie sich das Verhalten der Befehle **Einzelschritt** und **Prozedurschritt** bei den Anweisungen, die einen await\-Operator enthalten.  
  
-   Erklären Sie sich das Verhalten des Befehls **Ausführen bis Rücksprung**, wenn Sie ihn in einer asynchronen Methode verwenden.  
  
## Haltepunkte zum Anzeigen der Ablaufsteuerung  
 Wenn Sie eine Methode mit dem [Asynch](/dotnet/visual-basic/language-reference/modifiers/async)\-Modifizierer \(Visual Basic\) oder [asynch](/dotnet/csharp/language-reference/keywords/async)\-Modifizierer \(C\#\) kennzeichnen, können Sie den [Await](/dotnet/visual-basic/language-reference/modifiers/async)\-Operator \(Visual Basic\) oder [await](/dotnet/csharp/language-reference/keywords/await)\-Operator \(C\#\) in der Methode verwenden.  Um einen await\-Ausdruck zu erstellen, weisen Sie dem await\-Operator eine Aufgabe zu.  Wenn ein await\-Ausdruck für die Aufgabe aufgerufen wird, wird die aktuelle Methode sofort beendet, und es wird eine andere Aufgabe zurückgegeben.  Wenn die dem await\-Operator zugeordnete Aufgabe beendet wird, wird die Ausführung in derselben Methode fortgesetzt.  Weitere Informationen finden Sie unter [Ablaufsteuerung in asynchronen Programmen](../Topic/Control%20Flow%20in%20Async%20Programs%20\(C%23%20and%20Visual%20Basic\).md).  
  
> [!NOTE]
>  Eine asynchrone Methode wird an den Aufrufer zurückgegeben, wenn sie entweder auf das erste await\-Objekt trifft, das noch nicht abgeschlossen wurde, oder das Ende der asynchronen Methode erreicht.  
  
> [!NOTE]
>  Die Konsolenanwendungen in diesen Beispielen verwenden die <xref:System.Threading.Tasks.Task.Wait%2A>\-Methode, um zu verhindern, dass die Anwendung in der `Main`\-Methode beendet wird.  Sie sollten die <xref:System.Threading.Tasks.Task.Wait%2A>\-Methode außerhalb der Konsolenanwendungen nicht verwenden, da eine Deadlocksituation auftreten kann.  
  
 Mit dem folgenden Verfahren werden Haltepunkte festgelegt, um den Ablauf zu veranschaulichen, wenn die Anwendung eine await\-Anweisung erreicht.  Sie können die Ablaufsteuerung auch darstellen, indem Sie `Debug.WriteLine`\-Anweisungen hinzufügen.  
  
1.  Erstellen Sie eine Konsolenanwendung, und fügen Sie den folgenden Code ein:  
  
     [!code-cs[csAsyncDebugging#1](../misc/codesnippet/CSharp/walkthrough-using-the-debugger-with-async-methods_1.cs)]
     [!code-vb[csAsyncDebugging#1](../misc/codesnippet/VisualBasic/walkthrough-using-the-debugger-with-async-methods_1.vb)]  
  
2.  Legen Sie Debughaltepunkte auf den drei Zeilen fest, die mit dem Kommentar "Haltepunkt festlegen" enden.  
  
3.  Drücken Sie die F5\-TASTE, oder klicken Sie auf der Menüleiste auf **Debuggen**, **Debuggen starten**, um die Anwendung auszuführen.  
  
     Die Anwendung wechselt in die `ProcessAsync`\-Methode und hält in der Zeile mit dem await\-Operator an.  
  
4.  Drücken Sie die F5\-TASTE erneut.  
  
     Da die Anwendung an einer Anweisung mit einem await\-Operator angehalten wurde, wird die Asynch\-Methode sofort beendet und eine Aufgabe zurückgegeben.  Daher beendet die Anwendung die `ProcessAsync`\-Methode und hält in der aufrufenden Methode \(`Main`\) am Haltepunkt an.  
  
5.  Drücken Sie die F5\-TASTE erneut.  
  
     Wenn die `DoSomethingAsync`\-Methode abgeschlossen wurde, wird der Code nach der await\-Anweisung in der aufrufenden Methode fortgesetzt.  Folglich wird die Anwendung in der `ProcessAsync`\-Methode am Haltepunkt unterbrochen.  
  
     Während zunächst auf die `DoSomethingAsync`\-Methode gewartet wurde, wurde die `ProcessAsync`\-Methode beendet, die dann eine Aufgabe zurückgegeben hat.  Als die erwartete `DoSomethingAsync`\-Methode abgeschlossen war, wurde durch die Auswertung der await\-Anweisung der Rückgabewert von `DoSomethingAsync` generiert.  Die `DoSomethingAsync`\-Methode ist so definiert, dass sie in Visual Basic einen `Task (Of Integer)`\-Code oder in C\# einen `Task<int>`\-Code zurückgibt, sodass der Wert in der return\-Anweisung eine ganze Zahl ist.  Weitere Informationen finden Sie unter [Asynchrone Rückgabetypen](../Topic/Async%20Return%20Types%20\(C%23%20and%20Visual%20Basic\).md).  
  
### Abrufen und Abwarten einer Aufgabe  
 In der `ProcessAsync`\-Methode ist die `Dim result = Await DoSomethingAsync()`\-Anweisung \(Visual Basic\) bzw. die `var result = await DoSomethingAsync();`\-Anweisung \(C\#\) ein Zusammenschluss der folgenden zwei Anweisungen:  
  
 [!code-cs[csAsyncDebugging#2](../misc/codesnippet/CSharp/walkthrough-using-the-debugger-with-async-methods_2.cs)]
 [!code-vb[csAsyncDebugging#2](../misc/codesnippet/VisualBasic/walkthrough-using-the-debugger-with-async-methods_2.vb)]  
  
 Die erste Codezeile ruft die Asynch\-Methode auf und gibt eine Aufgabe zurück.  Diese Aufgabe wird in der nächsten Codezeile dem await\-Operator zugewiesen.  Die await\-Anweisung beendet die Methode \(`ProcessAsync`\) und gibt eine andere Aufgabe zurück.  Wenn die mit dem await\-Operator verknüpfte Aufgabe abgeschlossen ist, wird der Code in der Methode \(`ProcessAsync`\) nach der await\-Anweisung fortgesetzt.  
  
 Wenn die await\-Anweisung sofort eine andere Aufgabe zurückgibt, ist diese Aufgabe das zurückgegebene Argument der Asynch\-Methode mit dem await\-Operator \(`ProcessAsync`\).  Die Aufgabe, die von der await\-Anweisung zurückgegeben wurde, enthält die Codeausführung, die nach der await\-Anweisung in derselben Methode erfolgt. Aus diesem Grund unterscheidet sich diese Aufgabe von der, die mit dem await\-Operator verknüpft ist.  
  
## Einzel\- und Prozedurschritt  
 Mit dem Befehl **Einzelschritt** wird ein Einzelschritt in eine Methode ausgeführt, dagegen wird mit dem Befehl **Prozedurschritt** der Methodenaufruf ausgeführt und die Ausführung dann an der nächsten Zeile der aufrufenden Methode unterbrochen.  Weitere Informationen finden Sie unter [Code schrittweise ausführen, überspringen oder bis zum Rücksprung ausführen](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Step_into__over__or_out_of_the_code).  
  
 Die folgende Prozedur veranschaulicht, was geschieht, wenn der Befehl **Einzelschritt** oder **Prozedurschritt** bei einer await\-Anweisung ausgewählt wird.  
  
1.  Ersetzen Sie den Code in der Konsolenanwendung durch den folgenden Code:  
  
     [!code-cs[csAsyncDebugging#3](../misc/codesnippet/CSharp/walkthrough-using-the-debugger-with-async-methods_3.cs)]
     [!code-vb[csAsyncDebugging#3](../misc/codesnippet/VisualBasic/walkthrough-using-the-debugger-with-async-methods_3.vb)]  
  
2.  Drücken Sie die F11\-TASTE, oder wählen Sie in der Menüleiste **Debuggen**, **Einzelschritt** aus, um eine Demonstration des `Step Into`\-Befehls bei einer Anweisung mit einem await\-Operator zu starten.  
  
     Die Anwendung wird gestartet und an der ersten Zeile unterbrochen, wobei es sich in Visual Basic um die `Sub Main()`\- Methode oder in C\# um die öffnende geschweifte Klammer der `Main`\-Methode handelt.  
  
3.  Drücken Sie die F11\-TASTE drei Mal.  
  
     Die Anwendung sollte sich nun an der await\-Anweisung in der `ProcessAsync`\-Methode befinden.  
  
4.  Drücken Sie die Taste F11.  
  
     Die Anwendung wechselt in die `DoSomethingAsync`\-Methode und wird an der ersten Zeile unterbrochen.  Dieses Verhalten tritt auch dann bei der `await`\-Anweisung auf, wenn die Anwendung sofort zur aufrufenden Methode \(`Main`\) zurückkehrt.  
  
5.  Halten Sie die F11\-TASTE so lange gedrückt, bis die Anwendung zur await\-Anweisung in der `ProcessAsync`\-Methode zurückkehrt.  
  
6.  Drücken Sie die Taste F11.  
  
     Die Anwendung wird in der Zeile unterbrochen, die der await\-Anweisung folgt.  
  
7.  Wählen Sie in der Menüleiste **Debuggen**, **Debuggen beenden** aus, um die Ausführung der Anwendung zu beenden.  
  
     In den nächsten Schritten wird der Befehl **Prozedurschritt** bei einer await\-Anweisung veranschaulicht.  
  
8.  Drücken Sie die F11\-TASTE vier Mal, oder wählen Sie auf der Menüleiste **Debuggen**, **Einzelschritt** aus.  
  
     Die Anwendung sollte sich nun an der await\-Anweisung in der `ProcessAsync`\-Methode befinden.  
  
9. Drücken Sie die F10\-TASTE, oder wählen Sie in der Menüleiste **Debuggen**, **Prozedurschritt** aus.  
  
     Die Ausführung wird in der Zeile unterbrochen, die der await\-Anweisung folgt.  Dieses Verhalten tritt auch dann bei der await\-Anweisung auf, wenn die Anwendung sofort zur aufrufenden Methode \(`Main`\) zurückkehrt.  Der `Step Over`\-Befehl überspringt auch erwartungsgemäß die Ausführung der `DoSomethingAsync`\-Methode.  
  
10. Wählen Sie in der Menüleiste **Debuggen**, **Debuggen beenden** aus, um die Ausführung der Anwendung zu beenden.  
  
     Wie die folgenden Schritte verdeutlichen, unterscheidet sich das Verhalten der Befehle **Einzelschritt** und **Prozedurschritt** geringfügig, wenn sich der await\-Operator in einer anderen Zeile als der Aufruf der Asynch\-Methode befindet.  
  
11. Ersetzen Sie die await\-Anweisung in der `ProcessAsync`\-Methode durch den folgenden Code.  Die ursprüngliche await\-Anweisung ist eine Zusammenfassung der folgenden zwei Anweisungen.  
  
     [!code-cs[csAsyncDebugging#2](../misc/codesnippet/CSharp/walkthrough-using-the-debugger-with-async-methods_2.cs)]
     [!code-vb[csAsyncDebugging#2](../misc/codesnippet/VisualBasic/walkthrough-using-the-debugger-with-async-methods_2.vb)]  
  
12. Drücken Sie die F11\-TASTE, oder wählen Sie in der Menüleiste **Debuggen**, **Einzelschritt** mehrmals aus, um die Ausführung zu starten und den Code zu durchlaufen.  
  
     Beim Aufruf der `DoSomethingAsync`\-Methode wird der Befehl **Einzelschritt** in der `DoSomethingAsync`\-Methode unterbrochen, während der Befehl **Prozedurschritt** erwartungsgemäß zur nächsten Anweisung wechselt.  Bei der await\-Anweisung werden beide Befehle an der Anweisung unterbrochen, die der await\-Anweisung folgt.  
  
## Ausführen bis Rücksprung  
 Bei nicht asynchronen Methoden wird in der aufrufenden Methode durch den Befehl **Ausführen bis Rücksprung** der Code unterbrochen, der dem Methodenaufruf folgt.  Bei asynchronen Methoden ist die Logik für die Stelle, an der die Ausführung in der aufrufenden Methode unterbrochen wird, komplexer. Diese Logik hängt davon ab, ob sich der Befehl **Ausführen bis Rücksprung** in der ersten Zeile der Asynch\-Methode befindet.  
  
1.  Ersetzen Sie den Code in der Konsolenanwendung durch den folgenden Code:  
  
     [!code-cs[csAsyncDebugging#4](../misc/codesnippet/CSharp/walkthrough-using-the-debugger-with-async-methods_4.cs)]
     [!code-vb[csAsyncDebugging#4](../misc/codesnippet/VisualBasic/walkthrough-using-the-debugger-with-async-methods_4.vb)]  
  
2.  Legen Sie in der `Debug.WriteLine("before")`\-Zeile in der `DoSomethingAsync`\-Methode einen Haltepunkt fest.  
  
     Hiermit wird das Verhalten des Befehls **Ausführen bis Rücksprung** von einer Zeile in einer Asynch\-Methode veranschaulicht, bei der es sich nicht um die erste Zeile handelt.  
  
3.  Drücken Sie die F5\-TASTE, oder klicken Sie auf der Menüleiste auf **Debuggen**, **Debuggen starten**, um die Anwendung zu starten.  
  
     Der Code wird in der `Debug.WriteLine("before")`\-Zeile in der `DoSomethingAsync`\-Methode unterbrochen.  
  
4.  Drücken Sie UMSCHALT\+F11, oder wählen Sie in der Menüleiste **Debuggen**, **Ausführen bis Rücksprung** aus.  
  
     Die Anwendung wird in der aufrufenden Methode an der await\-Anweisung für die Aufgabe unterbrochen, die mit der aktuellen Methode verknüpft ist.  Daher wird die Anwendung in der `ProcessAsync`\-Methode an der await\-Anweisung unterbrochen.  Die Anwendung wird in Visual Basic nicht am `Dim z = 0`\-Code bzw. in C\# nicht am `int z = 0;`\-Code unterbrochen. Hierbei handelt es sich um den Code, der dem Aufruf der `DoSomethingAsync`\-Methode folgt.  
  
5.  Wählen Sie in der Menüleiste **Debuggen**, **Debuggen beenden** aus, um die Ausführung der Anwendung zu beenden.  
  
     Die nächsten Schritte zeigen, was geschieht, wenn Sie in der ersten Zeile einer Asynch\-Methode den Befehl **Ausführen bis Rücksprung** durchführen.  
  
6.  Entfernen Sie den vorhandenen Haltepunkt, und fügen Sie in der erste Zeile der `DoSomethingAsync`\-Methode einen Haltepunkt hinzu.  
  
     Fügen Sie in C\# den Haltepunkt zur öffnenden geschweiften Klammer der `DoSomethingAsync`\-Methode hinzu.  Fügen Sie in Visual Basic den Haltepunkt in der Zeile mit `Async Function DoSomethingAsync() As Task(Of Integer)` hinzu.  
  
7.  Drücken Sie die F5\-TASTE, um die Anwendung zu starten.  
  
     Der Code wird in der ersten Zeile der `DoSomethingAsync`\-Methode unterbrochen.  
  
8.  Klicken Sie in der Menüleiste auf **Debuggen**, **Fenster** und **Ausgabe**.  
  
     Das **Ausgabefenster** wird geöffnet.  
  
9. Drücken Sie UMSCHALT\+F11, oder wählen Sie in der Menüleiste **Debuggen**, **Ausführen bis Rücksprung** aus.  
  
     Die Anwendung wird fortgesetzt, bis die Asynch\-Methode die erste await\-Anweisung erreicht. Die Anwendung wird dann an der aufrufenden Anweisung unterbrochen.  Daher wird die Anwendung bei der `Dim the Task = DoSomethingAsync()`\-Methode \(Visual Basic\) bzw. bei der `var theTask = DoSomethingAsync();`\-Methode \(C\#\) unterbrochen.  Die "Vorher"\-Meldung wird im Ausgabefenster angezeigt, die "Nachher"\-Meldung jedoch noch nicht.  
  
10. Drücken Sie die F5\-TASTE, um die Ausführung der Anwendung fortzusetzen.  
  
     Die Anwendung wird mit der Anweisung fortgesetzt, die der await\-Anweisung in der aufgerufenen Asynch\-Funktion \(`DoSomethingAsync`\) folgt.  Im Ausgabefenster wird die "Nachher"\-Meldung angezeigt.  
  
## Siehe auch  
 [Navigieren im Code mit dem Debugger](../debugger/navigating-through-code-with-the-debugger.md)