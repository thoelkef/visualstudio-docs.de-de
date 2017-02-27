---
title: "Exemplarische Vorgehensweise: Debuggen zur Entwurfszeit | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Haltepunkte, Entwurfszeitdebuggen"
  - "Debuggen [Visual Studio], Entwurfszeit"
  - "Entwurfszeitdebuggen"
  - "Direktfenster, Entwurfszeitdebuggen"
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# Exemplarische Vorgehensweise: Debuggen zur Entwurfszeit
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können über das **Direktfenster** in Visual Studio eine Funktion oder Unterroutine ausführen, während die Anwendung nicht ausgeführt wird.  Wenn die Funktion oder die Unterroutine einen Haltepunkt enthält, unterbricht Visual Studio die Ausführung an der entsprechenden Stelle.  Sie können dann die Debuggerfenster verwenden, um den Programmzustand zu überprüfen.  Dieses Feature wird "Debuggen zur Entwurfszeit" genannt.  
  
 Die folgende Prozedur veranschaulicht, wie Sie dieses Feature verwenden können.  
  
### So erreichen Sie Haltepunkte über das Direktfenster  
  
1.  Fügen Sie den folgenden Code in eine Visual Basic\-Konsolenanwendung ein:  
  
    ```  
    Module Module1  
  
        Sub Main()  
            MySub()  
        End Sub  
  
        Function MyFunction() As Decimal  
            Static i As Integer  
            i = i + 1  
            Dim s As String  
  
            s = "Add Breakpoint here"  
            Return 4  
        End Function  
  
        Sub MySub()  
            MyFunction()  
        End Sub  
    End Module  
    ```  
  
2.  Legen Sie einen Haltepunkt an der Zeile `s="Add BreakPoint Here"` fest.  
  
3.  Geben Sie im **Direktfenster** Folgendes ein: `?MyFunction<Eingabetaste>`  
  
4.  Stellen Sie sicher, dass der Haltepunkt erreicht wurde und dass die Aufrufliste korrekt ist.  
  
5.  Klicken Sie im Menü **Debuggen** auf **Weiter**, und überprüfen Sie, ob Sie sich immer noch im Entwurfsmodus befinden.  
  
6.  Geben Sie im **Direktfenster** Folgendes ein: `?MyFunction<Eingabetaste>`  
  
7.  Geben Sie im **Direktfenster** Folgendes ein: `?MySub<Eingabe>`  
  
8.  Stellen Sie sicher, dass Sie den Haltepunkt erreicht haben, und prüfen Sie den Wert der statischen Variablen `i` im Fenster **Lokal**.  Sie sollte den Wert 3 haben.  
  
9. Überprüfen Sie, dass die Aufrufliste korrekt ist.  
  
10. Klicken Sie im Menü **Debuggen** auf **Weiter**, und überprüfen Sie, ob Sie sich immer noch im Entwurfsmodus befinden.  
  
## Siehe auch  
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [Debugger – Grundlagen](../debugger/debugger-basics.md)