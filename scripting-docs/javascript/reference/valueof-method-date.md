---
title: "valueOf-Methode (Datum) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 39a1f96e-14b0-4db2-b53d-cdfd67cbb208
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# valueOf-Methode (Datum)
Gibt den gespeicherten Zeitwert seit dem 1. Januar 1970 UTC in Millisekunden zurück.  
  
## Syntax  
  
```  
  
date.valueOf()  
```  
  
#### Parameter  
 Das `date`\-Objekt ist eine beliebige Instanz eines Datums.  
  
## Rückgabewert  
 Der gespeicherte Zeitwert seit dem 1. Januar 1970 UTC um 0:00 Uhr in Millisekunden.  Dieser Wert entspricht `getTime`.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `valueOf`\-Methode mit einem Datum.  
  
```javascript  
var myDate = new Date();  
myDate.setFullYear(2100, 5, 5);  
if (myDate.getTime() == myDate.valueOf())  
    document.write("values are the same");  
else  
    document.write("values are different");  
  
// Output: values are the same  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]