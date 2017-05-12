---
title: "Spezielle Fehlereigenschaften asynchroner Windows-Runtime-Methoden | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 45155584-06d8-4e7f-93a6-8564a93f643d
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Spezielle Fehlereigenschaften asynchroner Windows-Runtime-Methoden
Es kann schwierig sein, asynchrone Windows\-Runtime\-Methoden in JavaScript zu debuggen, da der Fehler möglicherweise in der Aufrufliste ausgelöst wird.  Das `Error`\-JavaScript\-Objekt weist zusätzliche Eigenschaften auf, die nur dann angezeigt werden, wenn der Fehler beim Ausführen der App im Debugmodus von einer asynchronen Windows\-Runtime\-Methode ausgelöst wird.  
  
## Besondere Fehler\-Eigenschaften  
 Ein Fehlerobjekt, das durch einen Fehler bei einem asynchronen Windows\-Runtime\-Vorgang im Debugmodus entsteht, hat die folgenden speziellen Eigenschaften:  
  
-   `asyncOpSource` \(Objekt\) ruft Informationen zum ursprünglichen Speicherort ab, an dem der Aufruf, der einen Fehler erzeugt hat, ausgeführt wurde.  Die Eigenschaft `asyncOpSource.originatingCall` \(Zeichenfolge\) zeigt die Position im Benutzercode an, der den asynchronen Vorgang ausgelöst hat.  
  
-   asyncOpType \(Zeichenfolge\) ruft den Namen des Typs des asynchronen Vorgangs ab, der den Fehler verursacht hat.  
  
 Weitere Informationen zu Fehlern bei asynchronen Vorgängen finden Sie unter:  
  
-   [How to handle errors with promises](http://msdn.microsoft.com/de-de/01d5a901-c4ea-46f6-8005-6d39c32203eb)  
  
-   [Problembehandlung bei Windows\-Runtime\-Fehlern](http://msdn.microsoft.com/de-de/1ef7d7df-82ac-441d-8ad0-54ab1318de64)