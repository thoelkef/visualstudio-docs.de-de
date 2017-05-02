---
title: "Boolescher Wert erwartet | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5010"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 35d71b7f-53fd-44c4-a7c7-b1550c65cfd4
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Boolescher Wert erwartet
Sie haben versucht, die **Boolean.prototype.toString**\-Methode oder **Boolean.prototype.valueOf**\-Methode für ein Objekt aufzurufen, das nicht vom Typ `Boolean` ist.  Das Objekt dieser Art von Aufruf muss vom Typ `Boolean` sein.  Beispiel:  
  
```javascript  
var o = new Object;  
o.f = Boolean.prototype.toString;  
o.f();  
```  
  
### So beheben Sie diesen Fehler  
  
-   Rufen Sie nur die boolesche **.prototype.toString**\-Methode oder die **Boolean.prototype.valueOf** \-Methode für Objekte des Typs **Boolean** auf.  
  
## Siehe auch  
 [Boolean\-Objekt](../../javascript/reference/boolean-object-javascript.md)   
 [Datentypen](../../javascript/data-types-javascript.md)   
 [Steuerung des Programmablaufs](../../javascript/controlling-program-flow-javascript.md)   
 [Kopieren, Übergeben und Vergleichen von Daten](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)