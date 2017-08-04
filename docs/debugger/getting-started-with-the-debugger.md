---
title: "Erste Schritte mit dem Debugger | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
caps.latest.revision: 6
caps.handback.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Erste Schritte mit dem Debugger
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Der Visual Studio\-Debugger ist in jeder Sprache einfach zu verwenden.  Wir zeigen Ihnen hier, wie Sie ein einfaches C\#\-Programm debuggen. Sie können die gleichen Schritte jedoch auch auf andere Sprachen wie z. B. C\+\+ und JavaScript anwenden.  
  
##  <a name="BKMK_Start_debugging_a_VS_project"></a> Debuggen eines einfachen C\#\-Projekts  
 Beginnen wir mit einer einfachen C\#\-Konsolenanwendung \(Klicken Sie auf **Datei \/ Neu \/ Projekt**, und wählen Sie **Visual C\#** und anschließend **Konsolenanwendung**\).  Wenn Sie bisher noch nicht mit Visual Studio gearbeitet haben, finden Sie grundlegende Informationen unter [Exemplarische Vorgehensweise: Erstellen einer einfachen Anwendung](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md).  Die Main\-Methode erhöht eine Integer\-Variablen 10\-mal um 1 und gibt das Ergebnis an die Konsole aus:  
  
```c#  
static void Main(string[] args)  
{  
    int testInt = 0;  
    for (int i = 1; i < 10; i++)  
    {  
        testInt += 1;  
    }  
    Console.WriteLine(testInt);  
}  
```  
  
 Erstellen Sie diesen Code in der **Debugkonfiguration**.  Diese Konfiguration ist standardmäßig festgelegt.  Weitere Informationen zu Konfigurationen finden Sie unter [Grundlagen der Buildkonfiguration](../ide/understanding-build-configurations.md).  
  
 Führen Sie diesen Code im Debugger aus, indem Sie auf **Debuggen \/ Debugging starten** klicken \(oder indem Sie auf der Symbolleiste auf **Starten** klicken oder die Taste F5 drücken\).  Die Anwendung wird nahezu sofort beendet, sodass Sie nicht genau erkennen können, ob etwas an das Konsolenfenster ausgegeben wurde.  
  
 Sie können die Ausführung anhalten, um das Konsolenfenster zu sehen, indem Sie einen Haltepunkt festlegen und die Ausführung schrittweise durchlaufen.  Um einen Haltepunkt festzulegen, platzieren Sie den Cursor in die Zeile `Console.WriteLine`, und klicken Sie auf **Debuggen \/ Neuer Haltepunkt \/ Funktionshaltepunkt**, oder klicken Sie einfach neben dieser Zeile in den linken Rand.  Der Haltepunkt sollte wie folgt aussehen:  
  
 ![Haltepunkt festlegen](~/debugger/media/getstartedbreakpoint.png "GetStartedBreakpoint")  
  
 Weitere Informationen zu Haltepunkten finden Sie unter [Verwenden von Haltepunkten](../debugger/using-breakpoints.md).  
  
 Starten Sie das Debuggen erneut.  Die Ausführung wird angehalten, bevor der `Console.WriteLine`\-Code ausgeführt wird.  Sie können diesen Code ausführen, indem Sie die Ausführung schrittweise durchlaufen \(klicken Sie auf **Debuggen \/ Prozedurschritt**, oder drücken Sie **F10**\).  In diesem Fall hätten Sie mit **Einzelschritt** \(**F11**\) das gleiche Ergebnis erzielt; der Unterschied wird weiter unten erläutert.  Die Zeile mit der letzten geschweiften Klammer der Methode sollte gelb hervorgehoben sein.  Betrachten Sie das Konsolenfenster.  Darin sollte **10** angezeigt werden.  Beenden Sie das Debugging \(**Debuggen \/ Debugging beenden** oder **Debugging beenden** auf der Symbolleiste oder **UMSCHALTTASTE\+F5**\).  
  
 Betrachten wir nun die Variablenwerte.  Direkt unterhalb des Codefensters befinden sich die Fenster **Auto**, **Lokal** und **Überwachen**.  Diese Fenster zeigen die aktuellen Werte der Variablen zum Zeitpunkt der Ausführung.  In den Fenstern **Auto** und **Lokal** wird „testInt“ mit dem Wert **10** angezeigt.  
  
 ![Auto&#45;Fenster beim Debuggen](~/debugger/media/getstartedwindows.png "GetStartedWindows")  
  
 Weitere Informationen zu den Fenstern **Auto** und **Lokal** finden Sie unter [Variablenfenster](../Topic/Variable%20Windows.md).  
  
 Sehen wir uns nun an, wie sich der Variablenwert beim Durchlaufen des Programms ändert.  Legen Sie in der Zeile `testInt += 1;` einen Haltepunkt fest, und starten Sie das Debuggen.  Wie Sie sehen, wird der Wert für **testInt** in den Fenstern **Lokal** und **Auto** mit **0** angezeigt, und der Wert für **i** ist **1**.  Wenn Sie das Debuggen fortsetzen \(**Debuggen \/ Fortfahren** oder **Fortfahren** auf der Symbolleiste oder **F5**\), können Sie sehen, dass sich der Wert für "testInt" erst zu **1**, dann zu **2** ändert usw.  Wenn Sie die Änderungen nicht weiter anzeigen möchten, entfernen Sie den Haltepunkt \(**Debuggen \/ Haltepunkt umschalten**, oder klicken Sie am Rand darauf\) und fahren mit dem Debuggen fort.  Wenn Sie alle Haltepunkte entfernen möchten, klicken Sie auf **Debuggen \/ Alle Haltepunkte löschen**, oder Sie drücken **STRG\+UMSCHALTTASTE\+F9** und klicken im angezeigten Dialogfeld **Möchten Sie alle Haltepunkte entfernen?** auf **Ja**.  
  
## Einzel\- und Prozedurschritte für Funktionsaufrufe  
 Zum Anzeigen des Unterschieds zwischen dem **Einzelschritt** und dem **Prozedurschritt** müssen wir eine Methode hinzufügen, die durch eine andere Methode aufgerufen wird.  Fügen Sie der C\#\-Anwendung eine Methode hinzu, und rufen Sie diese von der Main\-Methode auf.  Der Code sollte in etwa wie folgt aussehen:  
  
```c#  
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
  
 Setzen Sie einen Haltepunkt im `Method1();`\-Aufruf in der Main\-Methode, und starten Sie das Debuggen.  Wenn die Ausführung unterbrochen wird, klicken Sie auf **Debuggen \/ Einzelschritt** \(oder klicken Sie auf der Symbolleiste auf **Einzelschritt**, oder drücken Sie **F11**\).  Die Ausführung wird an der ersten geschweiften Klammer in "Method1\(\)" erneut unterbrochen:  
  
 ![Ausführen von Code in Einzelschritten](~/debugger/media/getstartedstepinto.png "GetStartedStepInto")  
  
 Beenden Sie das Debuggen, und starten Sie es erneut. Wenn die Ausführung am Haltepunkt unterbrochen wird, klicken Sie auf **Debuggen \/ Prozedurschritt** \(oder klicken Sie auf der Symbolleiste auf **Prozedurschritt**, oder drücken Sie **F10**\).  Die Ausführung wird bei `Console.WriteLine("end");` erneut unterbrochen.  
  
 Weitere Informationen zum Navigieren in Code finden Sie unter [Navigieren im Code mit dem Debugger](../debugger/navigating-through-code-with-the-debugger.md).