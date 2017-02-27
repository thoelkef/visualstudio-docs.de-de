---
title: "Gewusst wie: Zur&#252;ckkehren zur Funktion, die MFC aufgerufen hat, wenn die Ausf&#252;hrung angehalten wurde | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.mfc"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "Unterbrechen (Befehl)"
  - "Debuggen [MFC], Funktionen"
  - "Debuggen [MFC], Zurück zur aufrufenden Funktion"
  - "Funktionsaufrufe, Zurück zur aufrufenden Funktion"
  - "Funktionen [C++], Debuggen"
  - "Funktionen [Debugger]"
  - "Programme, Anhalten"
ms.assetid: d254a5a9-afbd-4923-9d7a-7422d824cabf
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Gewusst wie: Zur&#252;ckkehren zur Funktion, die MFC aufgerufen hat, wenn die Ausf&#252;hrung angehalten wurde
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen.  Klicken Sie im Menü Extras auf Einstellungen importieren und exportieren, um die Einstellungen zu ändern.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Wenn Sie zum Abbrechen des Programms im Menü **Debuggen** den Befehl **Unterbrechen** verwendet haben, sich jetzt in MFC befinden und sicher sind, dass das Problem in Ihrem Code liegt, können sie mithilfe des Fensters "Aufrufliste" zu Ihrer Funktion zurück navigieren.  Weitere Informationen finden Sie unter [Gewusst wie: Verwenden des Fensters Aufrufliste](../debugger/how-to-use-the-call-stack-window.md).  
  
 Manchmal wird der Code in der Meldungsverteilschleife unterbrochen.  In diesem Fall ist kein Benutzercode in der Aufrufliste vorhanden.  Um diesen Fehler zu vermeiden, können Haltepunkte \(möglicherweise mit Bedingungen und Trefferanzahl\) anstelle des Befehls **Unterbrechen** verwendet werden.  Weitere Informationen finden Sie unter [Breakpoints and Tracepoints](http://msdn.microsoft.com/de-de/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
### So navigieren Sie zu der Funktion, von der MFC aufgerufen wurde  
  
-   Verwenden Sie das Fenster **Aufrufliste**.  
  
## Siehe auch  
 [FAQs zum Debuggen von systemeigenem Code](../debugger/debugging-native-code-faqs.md)   
 [Debuggen von systemeigenem Code](../debugger/debugging-native-code.md)