---
title: "prototype-Eigenschaft (Array) | Microsoft Docs"
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
ms.assetid: 5fedf632-8316-4e5d-ab20-10e41aa4d9f8
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# prototype-Eigenschaft (Array)
Gibt einen Verweis auf den Prototyp einer Arrayklasse zurück.  
  
## Syntax  
  
```  
  
array.prototype  
```  
  
## Hinweise  
 Das `array`\-Argument ist der Name eines Arrays.  
  
 Mit der `prototype`\-Eigenschaft können Sie einer Objektklasse grundlegende Funktionen zur Verfügung stellen.  Neue Instanzen eines Objekts "erben" das Verhalten des Prototyps, der diesem Objekt zugewiesen ist.  
  
 Um beispielsweise dem `Array`\-Objekt eine Methode hinzuzufügen, die den Wert des größten Elements des Arrays zurückgibt, deklarieren Sie die Funktion, fügen sie `Array.prototype` hinzu und verwenden sie dann.  
  
```javascript  
function array_max( ){  
    var i, max = this[0];  
    for (i = 1; i < this.length; i++)  
    {  
    if (max < this[i])  
    max = this[i];  
    }  
    return max;  
}  
Array.prototype.max = array_max;  
var myArray = new Array(7, 1, 3, 11, 25, 9  
);  
document.write(myArray.max());  
  
// Output: 25  
```  
  
 Alle systeminternen [!INCLUDE[javascript](../../includes/javascript-md.md)]\-Objekte verfügen über eine `prototype`\-Eigenschaft, die schreibgeschützt ist.  Dem Prototyp können Eigenschaften und Methoden hinzugefügt werden, dem Objekt kann jedoch kein anderer Prototyp zugewiesen werden.  Benutzerdefinierten Objekten kann jedoch ein neuer Prototyp zugewiesen werden.  
  
 In den Methoden\- und Eigenschaftenlisten für jedes systeminterne Objekt in diesem Sprachverzeichnis wird angegeben, welche Bestandteil des Objektprototyps sind und welche nicht.  
  
## Anforderungen  
 [!INCLUDE[jsv2](../../includes/jsv2-md.md)]