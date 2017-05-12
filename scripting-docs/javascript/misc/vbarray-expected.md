---
title: "VBArray erwartet | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5013"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: f2998d7d-13a4-4bbe-b872-3ff3316551e4
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# VBArray erwartet
Sie haben ein Objekt angegeben, das kein safeArray von Visual Basic war, obwohl ein solches Array erwartet wurde.  
  
```  
new VBArray(safeArray);  
```  
  
 VBArrays sind schreibgeschützt und können nicht direkt erstellt werden.  Das safeArray\-Argument ist ein VBArray\-Wert und muss einen VBArray\-Wert erhalten haben, bevor es an den `VBArray`\-Konstruktor übergeben wird.  Die ist nur möglich, indem der Wert aus einem vorhandenen ActiveX\-Objekt oder einem anderen Objekt abgerufen wird.  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass nur **VBArray**\-Objekte an den **VBArray**\-Konstruktor übergeben werden.  
  
## Siehe auch  
 [VBArray\-Objekt](../../javascript/reference/vbarray-object-javascript.md)   
 [Verwenden von Arrays](../../javascript/advanced/using-arrays-javascript.md)