---
title: "Regul&#228;res Ausdrucksobjekt erwartet | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5016"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: e226096c-c58f-4bcb-a71e-fa32ce474b67
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Regul&#228;res Ausdrucksobjekt erwartet
Sie haben versucht, die **RegExp.prototype.toString**\-Methode oder die **RegExp.prototype.valueOf**\-Methode für ein Objekt aufzurufen, das nicht vom Typ `RegExp` ist.  Das Objekt, für das diese Art von Aufruf erfolgt, muss vom Typ `RegExp` sein.  
  
### So beheben Sie diesen Fehler  
  
-   Rufen Sie die **RegExp.prototype.toString**\-Methode oder die **RegExp.prototype.valueOf**\-Methode nur für Objekte des Typs `RegExp` auf.  
  
## Siehe auch  
 [Regular Expression\-Objekt](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/de-de/ab0766e1-7037-45ed-aa23-706f58358c0e)