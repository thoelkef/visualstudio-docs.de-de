---
title: "Gewusst wie: Ausf&#252;hren von verwaltetem Code bis zum R&#252;cksprung, wenn systemeigene Rahmen im Aufruflistenfenster fehlen | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
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
  - "SQL"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Fenster „Aufrufliste“, fehlende native Rahmen"
  - "Code, verwalteter Code"
  - "Systemeigene Rahmen"
  - "Ausführen in Einzelschritten, aus verwaltetem Code heraus"
  - "Verwalteter Code, Ausführen in Einzelschritten aus"
ms.assetid: 97cdd2a8-02a9-4a06-a5b1-c92b1e431979
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Ausf&#252;hren von verwaltetem Code bis zum R&#252;cksprung, wenn systemeigene Rahmen im Aufruflistenfenster fehlen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn der Code systemeigene Rahmen enthält, die im Fenster **Anrufliste** nicht angezeigt werden, kann das Ausführen von verwaltetem Code bis zum Rücksprung zu unerwarteten Ergebnissen führen.  Sie können dieses Problem umgehen, indem Sie anstelle von **Ausführung bis Rücksprung** einen Haltepunkt verwenden.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen.  Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren**, um die Einstellungen zu ändern.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### So führen Sie verwalteten Code bis zum Rücksprung aus, wenn systemeigene Rahmen in der Aufrufliste fehlen  
  
1.  Legen Sie im systemeigenen Code nach dem Aufruf an den verwalteten Code einen Positionshaltepunkt fest.  
  
2.  Wählen Sie im Menü **Debuggen** die Option **Weiter**.  
  
     Sobald der verwaltete Aufruf fertig gestellt wurde, wird die Ausführung am Haltepunkt im systemeigenen Code beendet.  
  
## Siehe auch  
 [Gewusst wie: Verwenden des Fensters Aufrufliste](../debugger/how-to-use-the-call-stack-window.md)