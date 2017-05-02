---
title: "Enumeratorobjekt erwartet | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5015"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: dc6e32c1-a6e6-4e12-ac99-e3f65f91c8d7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Enumeratorobjekt erwartet
Sie haben versucht, die Methoden **Enumerator.prototype.atEnd, Enumerator.prototype.item, Enumerator.prototype.moveFirst** oder **Enumerator.prototype.moveNext** für ein Objekt eines anderen Typs als `Enumerator` aufzurufen.  Das Objekt, für das diese Art von Aufruf erfolgt, muss vom Typ `Enumerator` sein.  Hier folgt ein Beispiel für den Code, der diese Regel verletzt:  
  
```javascript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### So beheben Sie diesen Fehler  
  
-   Rufen Sie die Methoden **Enumerator.prototype.atEnd**, **Enumerator.prototype.item**, **Enumerator.prototype.moveFirst** oder **Enumerator.prototype.moveNext** nur für Objekte des Typs `Enumerator` auf.  Um herauszufinden, ob das Objekt ein `Enumerator`\-Objekt ist, verwenden Sie folgenden Code:  
  
    ```  
    if(x instanceof Enumerator)  
    ```  
  
## Siehe auch  
 [Enumeratorobjekt](../../javascript/reference/enumerator-object-javascript.md)