---
title: "Die Genauigkeit liegt au&#223;erhalb des definierten Bereichs | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5027"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: c16760ac-fc08-49d7-8878-9bc434b3c080
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Die Genauigkeit liegt au&#223;erhalb des definierten Bereichs
Sie haben versucht, ein ungültiges Argument an die **Number.prototype.toPrecision**\-Funktion zu übergeben.  Das Argument für **toPrecision** muss zwischen 1 und 21 \(einschließlich\) liegen.  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass das Argument für `toPrecision` nicht zu groß oder zu klein ist.  
  
## Siehe auch  
 [toPrecision\-Methode \(Zahl\)](../../javascript/reference/toprecision-method-number-javascript.md)