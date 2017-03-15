---
title: "How to: Search for a Process in Processes View | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Processes view"
  - "processes, searching for"
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# How to: Search for a Process in Processes View
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können in der Prozessansicht einen bestimmten Prozess suchen, indem Sie die Prozess\-ID oder Modulzeichenfolge des Prozesses als Suchkriterium verwenden.  Sie können auch die anfängliche Suchrichtung angeben.  In den Feldern des Dialogfelds werden die Attribute des in der Prozessstruktur ausgewählten Prozesses angezeigt.  
  
### So suchen Sie einen Prozess in der Prozessansicht  
  
1.  Ordnen Sie die Fenster so an, dass Spy\+\+ und ein aktives [Prozessansichtsfenster](../debugger/processes-view.md) sichtbar sind.  
  
2.  Klicken Sie im Menü **Suchen** auf **Prozess suchen**  
  
     Das Dialogfeld [Prozesssuche](../debugger/process-search-dialog-box.md) wird geöffnet.  
  
3.  Geben Sie die Prozess\-ID oder eine Modulzeichenfolge als Suchkriterium ein.  
  
4.  Löschen Sie alle Felder, für die Sie keine Werte angeben möchten.  
  
    > [!TIP]
    >  Um alle Prozesse zu suchen, die sich im Besitz des Moduls befinden, löschen Sie das Feld **Prozess**, und geben Sie im Feld **Modul** den Modulnamen ein.  Setzen Sie dann mithilfe von **Weitersuchen** die Suche nach Prozessen fort.  
  
5.  Wählen Sie als anfängliche Richtung der Suche **Nach oben** oder **Nach unten** aus.  
  
6.  Klicken Sie auf **OK**.  
  
 Wenn ein entsprechender Prozess gefunden wird, wird er im **Prozessansichtsfenster** hervorgehoben.