---
title: "Gewusst wie: Debuggen im gemischten Modus | Microsoft Docs"
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
  - "C++"
helpviewer_keywords: 
  - "Debuggen [Visual Studio], Gemischter Modus"
  - "Debuggen von DLLs"
  - "Debuggen im gemischten Modus"
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
caps.latest.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 29
---
# Gewusst wie: Debuggen im gemischten Modus
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In den folgenden Prozeduren wird beschrieben, wie sowohl verwalteter als auch systemeigener Code debuggt wird. Dieses Verfahren wird auch als Debuggen im gemischten Modus bezeichnet.  Je nachdem, ob die DLL oder die Anwendung in systemeigenem Code geschrieben sind, gibt es hierfür zwei Szenarios:  
  
-   Die Anwendung, die die DLL aufruft, ist in systemeigenem Code geschrieben.  In diesem Fall handelt es sich um eine verwaltete DLL, und sowohl der verwaltete als auch der systemeigene Debugger müssen für das Debuggen aktiviert werden.  Sie können diese Einstellungen im Dialogfeld **\<Projekt\>\-Eigenschaftenseiten** überprüfen.  Wie Sie dabei vorgehen, hängt davon ab, ob Sie den Debugvorgang über das DLL\-Projekt oder über das Projekt für die aufrufende Anwendung starten.  
  
-   Die aufrufende Anwendung, die die DLL aufruft, ist in verwaltetem Code, die DLL in systemeigenem Code geschrieben.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen.  Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren**, um die Einstellungen zu ändern.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### So aktivieren Sie Debuggen im gemischten Modus  
  
1.  Wählen Sie das Projekt im **Projektmappen\-Explorer** aus.  
  
2.  Klicken Sie im Menü **Ansicht** auf die Option **Eigenschaftenseiten**.  
  
3.  Erweitern Sie im Dialogfeld **\<Projekt\>\-Eigenschaftenseiten** den Knoten **Konfigurationseigenschaften**, und wählen Sie **Debuggen**.  
  
4.  Legen Sie **Debuggertyp** auf **Gemischt** oder **Automatisch** fest.  
  
## Siehe auch  
 [Gewusst wie: Debuggen über ein DLL\-Projekt](../debugger/how-to-debug-from-a-dll-project.md)