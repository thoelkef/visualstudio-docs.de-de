---
title: "Wie wird festgestellt, woher der falsche Parameterwert stammt? | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.parameters"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "Debuggen [C++], Parameter"
  - "Funktionen [Debugger], Entdecken falscher Parameterwerte"
  - "Parameterwerte, Problembehandlung"
  - "Parameter [Debugger]"
  - "Übergeben von Parametern, Problembehandlung bei falschen Werten"
ms.assetid: 1f1ae455-0e25-4e9d-b33f-53908f5bd6ce
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Wie wird festgestellt, woher der falsche Parameterwert stammt?
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## Problembeschreibung  
 An eine Funktion wird der falsche Parameterwert übergeben.  Diese Funktion wird von mehreren Stellen aus aufgerufen.  Wie kann festgestellt werden, woher der falsche Wert stammt?  
  
## Lösung  
  
#### So beheben Sie dieses Problem  
  
1.  Legen Sie am Anfang der Funktion einen Positionshaltepunkt fest.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Haltepunkt, und wählen Sie **Bedingung** aus.  
  
3.  Klicken Sie im Dialogfeld **Bedingung für Haltepunkt** auf das Kontrollkästchen **Bedingung**.  Weitere Informationen erhalten Sie unter [Erweiterte Haltepunkte](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).  
  
4.  Geben Sie einen Ausdruck, z. B. `Var==3`, in das Textfeld ein, wobei `Var` der Name des Parameters ist, der den falschen Wert enthält, und `3` der übergebene falsche Wert.  
  
5.  Aktivieren Sie das Optionsfeld **ist True**, und klicken Sie auf die Schaltfläche **OK**.  
  
6.  Führen Sie nun das Programm erneut aus.  Der Haltepunkt bewirkt, dass das Programm am Funktionsanfang anhält, sobald `Var` den Wert `3` hat.  
  
7.  Im Fenster Aufrufliste sehen Sie die aufrufende Funktion und können zu ihrem Quellcode navigieren.  Weitere Informationen finden Sie unter [Gewusst wie: Verwenden des Fensters Aufrufliste](../debugger/how-to-use-the-call-stack-window.md).  
  
## Siehe auch  
 [FAQs zum Debuggen von systemeigenem Code](../debugger/debugging-native-code-faqs.md)   
 [Breakpoints](http://msdn.microsoft.com/de-de/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [Debuggen von systemeigenem Code](../debugger/debugging-native-code.md)