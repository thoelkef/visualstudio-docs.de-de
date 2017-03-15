---
title: "Ereignis &quot;Class_Terminate&quot; wird nicht mehr unterst&#252;tzt. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42002"
  - "bc42002"
helpviewer_keywords: 
  - "BC42002"
ms.assetid: 11eeac74-666d-4b23-81bc-b1691290ddd0
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ereignis &quot;Class_Terminate&quot; wird nicht mehr unterst&#252;tzt.
Das Ereignis "Class\_Terminate" wird nicht mehr unterstützt. Verwenden Sie "Sub Finalize", um Ressourcen freizugeben.  
  
 Das Ereignis `Class_Terminate` aus früheren Versionen von Visual Basic wurde durch Klassendestruktoren ersetzt.  
  
 Standardmäßig ist diese Meldung eine Warnung. Informationen zum Ausblenden von Warnungen oder zum Behandeln von Warnungen als Fehler finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Fehler\-ID:** BC42002  
  
### So beheben Sie diesen Fehler  
  
-   Deklarieren Sie eine `Sub`\-Prozedur namens `Finalize` um eine Klasse zu beenden.`Sub Finalize` wird aufgerufen, wenn der Garbage Collector feststellt, dass es keine weiteren aktiven Verweise auf die Instanz gibt.  
  
## Siehe auch  
 [Classes for Visual Basic 6.0 Users](http://msdn.microsoft.com/de-de/d625222c-cd32-4c8d-b25c-ea71729b88b7)   
 [NICHT IM BUILD: Verwenden von Konstruktoren und Destruktoren](http://msdn.microsoft.com/de-de/548eebe1-86c4-4377-b2f5-447cb8be3d90)   
 [NICHT im BUILD: Gewusst wie: Implementieren des Dispose\-Finalize\-Musters \(Visual Basic\)](http://msdn.microsoft.com/de-de/adf7a232-4ebb-485d-8626-8d64421eb0c4)