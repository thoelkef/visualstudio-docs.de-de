---
title: "prototype-Eigenschaft (Zahl) | Microsoft Docs"
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
ms.assetid: d5fb87af-fc3a-4469-8dde-d31daf654f94
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# prototype-Eigenschaft (Zahl)
Gibt einen Verweis auf den Prototyp einer Zahlenklasse zurück.  
  
## Syntax  
  
```  
  
number.prototype  
```  
  
## Hinweise  
 Das `number`\-Argument ist der Name einer Zahl.  
  
 Mit der `prototype`\-Eigenschaft können Sie einer Objektklasse grundlegende Funktionen zur Verfügung stellen.  Neue Instanzen eines Objekts "erben" das Verhalten des Prototyps, der diesem Objekt zugewiesen ist.  
  
 Um beispielsweise dem `Number`\-Objekt eine Methode hinzuzufügen, welche die Anzahl von Integer\-Ziffern zurückgibt, deklarieren Sie die Funktion, fügen sie zu `Number.prototype` hinzu und verwenden sie dann.  
  
```javascript  
function number_digits() {  
    var digits = 0;  
    var num = this;  
    while (num) >= 1) {  
        digits++;  
        num /= 10;  
    }  
    return digits;  
}  
  
Number.prototype.digits = number_digits;  
var myNumber = new Number(3456.789);  
document.write(myNumber.digits());  
// Output:  
// 4  
```  
  
 Alle systeminternen [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]\-Objekte verfügen über eine `prototype`\-Eigenschaft, die schreibgeschützt ist.  Dem Prototyp können Eigenschaften und Methoden hinzugefügt werden, dem Objekt kann jedoch kein anderer Prototyp zugewiesen werden.  Benutzerdefinierten Objekten kann jedoch ein neuer Prototyp zugewiesen werden.  
  
 In den Methoden\- und Eigenschaftenlisten für jedes systeminterne Objekt in diesem Sprachverzeichnis wird angegeben, welche Bestandteil des Objektprototyps sind und welche nicht.  
  
## Anforderungen  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]