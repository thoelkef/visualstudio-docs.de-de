---
title: "prototype-Eigenschaft (Boolesch) | Microsoft Docs"
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
ms.assetid: e4f07cb5-3462-488c-a418-76064ab10eae
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# prototype-Eigenschaft (Boolesch)
Gibt einen Verweis auf den Prototyp für einen booleschen Wert zurück.  
  
## Syntax  
  
```  
  
boolean.prototype  
```  
  
## Hinweise  
 Das `boolean`\-Argument ist der Name eines Objekts.  
  
 Die `prototype`\-Eigenschaft stellt einer Objektklasse grundlegende Funktionen zur Verfügung.  Neue Instanzen eines Objekts "erben" das Verhalten des Prototyps, der diesem Objekt zugewiesen ist.  Eigenschaften und Methoden können dem Prototyp hinzugefügt werde, aber integrierten Objekten kann kein anderer Prototyp zugewiesen werden.  
  
 Um beispielsweise dem `Boolean`\-Objekt eine Methode hinzuzufügen, die den Wert des größten Elements des Arrays zurückgibt, deklarieren Sie die Funktion, fügen Sie sie `Boolean.prototype` hinzu, und verwenden Sie sie dann.  
  
```javascript  
function isFalse( ){  
    if (this.toString() == "false")  
         return true;  
    else  
        return false;  
}  
Boolean.prototype.isFalse = isFalse;  
var bool = new Boolean(1);  
document.write(bool.isFalse());  
  
// Output:  
// false  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]