---
title: "prototype-Eigenschaft (Datum) | Microsoft Docs"
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
ms.assetid: 44f9c637-7da7-4833-906d-358506f32ced
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# prototype-Eigenschaft (Datum)
Gibt einen Verweis auf den Prototyp eines Datums zurück.  
  
## Syntax  
  
```  
  
date.prototype  
```  
  
## Hinweise  
 Das `date`\-Argument ist der Name eines Objekts.  
  
 Mit der `prototype`\-Eigenschaft können Sie einem Datum grundlegende Funktionen zur Verfügung stellen.  Neue Instanzen eines Objekts "erben" das Verhalten des Prototyps, der diesem Objekt zugewiesen ist.  
  
 Um beispielsweise dem `Date`\-Objekt eine Methode hinzuzufügen, die den Wert des größten Elements des Arrays zurückgibt, deklarieren Sie die Funktion, fügen sie `Date.prototype` hinzu und verwenden sie dann.  
  
```javascript  
function max( ){  
    var max = new Date();  
    max.setFullYear(2200, 01, 01);  
    return max;  
}  
Date.prototype.maxDate = max;  
var myDate = new Date();  
  
if (myDate < myDate.maxDate())  
    document.write("today isn't the max");  
else if (myDate == myDate.maxDate())  
    document.write("today is the max");   
  
// Output:  
// today isn't the max  
  
```  
  
 Alle systeminternen [!INCLUDE[javascript](../../includes/javascript-md.md)]\-Objekte verfügen über eine `prototype`\-Eigenschaft, die schreibgeschützt ist.  Dem Prototyp können Eigenschaften und Methoden hinzugefügt werden, dem Objekt kann jedoch kein anderer Prototyp zugewiesen werden.  Benutzerdefinierten Objekten kann jedoch ein neuer Prototyp zugewiesen werden.  
  
## Anforderungen  
 [!INCLUDE[jsv2](../../includes/jsv2-md.md)]