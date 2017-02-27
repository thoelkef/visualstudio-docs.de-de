---
title: "How to: Search for a Thread in Threads View | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "threads, searching"
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# How to: Search for a Thread in Threads View
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können in der Threadansicht einen bestimmten Thread suchen, indem Sie seine Thread\-ID oder Modulzeichenfolge als Suchkriterium verwenden.  Sie können auch die anfängliche Suchrichtung angeben.  In den Feldern des Dialogfelds werden die Attribute des in der Threadstruktur ausgewählten Threads angezeigt.  
  
### So suchen Sie einen Thread in der Threadansicht  
  
1.  Ordnen Sie die Fenster so an, dass Spy\+\+ und ein aktives [Threadansichtsfenster](../debugger/threads-view.md) sichtbar sind.  
  
2.  Klicken Sie im Menü **Suchen** auf **Thread suchen**.  
  
     Das Dialogfeld [Threadsuche](../debugger/thread-search-dialog-box.md) wird geöffnet.  
  
3.  Geben Sie die Thread\-ID oder eine Modulzeichenfolge als Suchkriterium ein.  
  
4.  Löschen Sie alle Felder, für die Sie keine Werte angeben möchten.  
  
    > [!TIP]
    >  Um alle Threads im Besitz eines Moduls zu suchen, löschen Sie das Textfeld **Thread**, und geben Sie den Modulnamen im Feld **Modul** ein.  Setzen Sie dann mithilfe von **Weitersuchen** die Suche nach Threads fort.  
  
5.  Wählen Sie als anfängliche Richtung der Suche **Nach oben** oder **Nach unten** aus.  
  
6.  Klicken Sie auf **OK**.  
  
 Wenn ein entsprechender Thread gefunden wird, wird er im Threadansichtsfenster hervorgehoben.