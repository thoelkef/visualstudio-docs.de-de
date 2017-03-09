---
title: "Das Projekt enth&#228;lt bereits einen Verweis auf die Assembly &lt;Assemblyidentit&#228;t&gt;. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32208"
  - "vbc32208"
helpviewer_keywords: 
  - "BC32208"
ms.assetid: a9f73a2c-5135-4315-bf2c-710ef216095d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Das Projekt enth&#228;lt bereits einen Verweis auf die Assembly &lt;Assemblyidentit&#228;t&gt;.
Das Projekt enthält bereits einen Verweis auf die Assembly \<Assemblyidentität\>. Es kann kein zweiter Verweis auf \<Dateipfad\> hinzugefügt werden.  
  
 Ein Projekt enthält mehrere Verweise auf dieselbe Assembly.  
  
 Die Identität der Assembly enthält den Namen, die Version, ggf. den öffentlichen Schlüssel sowie die Kultur der Assembly.  
  
 Eine mögliche Ursache dieses Fehlers ist ein Verweis auf eine andere Kopie der Assembly über einen anderen Dateipfad als den des ursprünglichen Verweises.  
  
 **Fehler\-ID:** BC32208  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie den zweiten Verweis. Er ist überflüssig, weil er auf dieselbe Assembly verweist.  
  
## Siehe auch  
 [Verwalten von Verweisen in einem Projekt](../ide/managing-references-in-a-project.md)   
 [NIB: Gewusst wie: Hinzufügen oder Entfernen von Verweisen mithilfe des Dialogfelds „Verweis hinzufügen“](http://msdn.microsoft.com/de-de/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Problembehandlung bei fehlerhaften Verweisen](../ide/troubleshooting-broken-references.md)