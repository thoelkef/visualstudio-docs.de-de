---
title: "prototype-Eigenschaft (Fehler) | Microsoft Docs"
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
ms.assetid: 6c268a51-1a3d-4397-abf8-e54ca4e598fe
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# prototype-Eigenschaft (Fehler)
Gibt einen Verweis auf den Prototyp eines Fehlers zurück.  
  
## Syntax  
  
```  
  
error.prototype  
```  
  
## Hinweise  
 Das `error`\-Argument ist der Name eines Fehlers.  
  
 Mit der `prototype`\-Eigenschaft können Sie einem Fehler grundlegende Funktionen zur Verfügung stellen.  Neue Instanzen eines Objekts "erben" das Verhalten des Prototyps, der diesem Objekt zugewiesen ist.  
  
 Um beispielsweise dem `Error`\-Objekt eine Methode hinzuzufügen, die den Wert des größten Elements des Arrays zurückgibt, deklarieren Sie die Funktion, fügen sie `Error.prototype` hinzu und verwenden sie dann.  
  
```javascript  
function getSeverity(){  
    if (this.number > 1000)  
        return "high";  
    else  
        return "low";  
}  
Error.prototype.getSev = getSeverity;  
var myError = new Error();  
myError.number = 5000;  
  
document.write(myError.getSev());   
  
// Output: high  
  
```  
  
 Alle systeminternen [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]\-Objekte verfügen über eine `prototype`\-Eigenschaft, die schreibgeschützt ist.  Dem Prototyp können Eigenschaften und Methoden hinzugefügt werden, dem Objekt kann jedoch kein anderer Prototyp zugewiesen werden.  Benutzerdefinierten Objekten kann jedoch ein neuer Prototyp zugewiesen werden.  
  
## Anforderungen  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]