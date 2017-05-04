---
title: "instanceof-Operator (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "instanceof_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "instanceOf-Operator"
ms.assetid: 92467bdc-56b5-42dc-adbd-a219776454d2
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# instanceof-Operator (JavaScript)
Gibt einen booleschen Wert zurück, der angibt, ob ein Objekt eine Instanz einer bestimmten Klasse ist.  
  
## Syntax  
  
```  
  
result = object instanceof class  
```  
  
## Parameter  
 `result`  
 Erforderlich.  Beliebige Variable.  
  
 `object`  
 Erforderlich.  Beliebiger Objektausdruck.  
  
 `class`  
 Erforderlich.  Eine beliebige definierte Objektklasse.  
  
## Hinweise  
 Der `instanceof`\-Operator gibt `true` zurück, wenn `object` eine Instanz von `class` ist.  Er gibt `true` zurück, wenn `true`, wenn `class` in der Prototypenkette des Objekts vorhanden ist.  Er gibt `false` zurück, wenn `object` keine Instanz von `class` ist oder wenn `object` `null` ist.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung des `instanceof`\-Operators gezeigt.  
  
```javascript  
function objTest(obj){  
    var i, t, s = "";  
    t = new Array();  
    t["Date"] = Date;  
    t["Object"] = Object;  
    t["Array"] = Array;  
        for (i in t){  
            if (obj instanceof t[i]) {   
                s += "obj is an instance of " + i + "<br/>";  
            }  
            else {  
                s += "obj is not an instance of " + i + "<br/>";  
        }  
    }  
    return(s);  
}  
  
var obj = new Date();  
document.write(objTest(obj));  
  
// Output:   
// obj is an instance of Date  
// obj is an instance of Object  
// obj is not an instance of Array  
```  
  
## Anforderungen  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## Siehe auch  
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)