---
title: "Datenobjekt erwartet | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5006"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: d6ab82e6-ca64-46b4-a06c-5c6b0aa057cb
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Datenobjekt erwartet
Sie haben versucht, die **Date.prototype.toString**\-Methode oder die **Date.prototype.valueOf**\-Methode für ein Objekt aufzurufen, das nicht vom Typ `Date` ist.  Das Objekt, für das diese Art von Aufruf erfolgt, muss vom Typ `Date` sein.  Beispiel:  
  
```javascript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### So beheben Sie diesen Fehler  
  
-   Rufen die **Date.prototype.toString**\-Methode oder die **Date.prototype.valueOf**\-Methode nur für Objekte des Typs `Date` auf.  
  
## Siehe auch  
 [Date\-Objekt](../../javascript/reference/date-object-javascript.md)   
 [getDate\-Methode \(Datum\)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Systeminterne Objekte](../../javascript/intrinsic-objects-javascript.md)