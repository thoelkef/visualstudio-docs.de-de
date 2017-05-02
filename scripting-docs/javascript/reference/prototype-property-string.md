---
title: "prototype-Eigenschaft (String) | Microsoft Docs"
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
ms.assetid: 437ce478-9c45-45f7-8952-bd71856cfcd8
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# prototype-Eigenschaft (String)
Gibt einen Verweis auf den Prototyp einer Zeichenfolgenklasse zurück.  
  
## Syntax  
  
```  
  
string.prototype  
```  
  
## Hinweise  
 Das `string`\-Argument ist der Name einer Zeichenfolge.  
  
 Mit der `prototype`\-Eigenschaft können Sie einer Objektklasse grundlegende Funktionen zur Verfügung stellen.  Neue Instanzen eines Objekts "erben" das Verhalten des Prototyps, der diesem Objekt zugewiesen ist.  
  
 Um beispielsweise dem `String`\-Objekt eine Methode hinzuzufügen, die den Wert des letzten Elements der Zeichenfolge zurückgibt, deklarieren Sie die Funktion, fügen sie zu `String.prototype` hinzu und verwenden sie dann.  
  
```javascript  
function string_last( ){  
    return this.charAt(this.length - 1);  
}  
String.prototype.last = string_last;  
var myString = new String("every good boy does fine");  
document.write(myString.last());  
  
// Output:  
// e  
```  
  
 Alle systeminternen [!INCLUDE[javascript](../../includes/javascript-md.md)]\-Objekte verfügen über eine `prototype`\-Eigenschaft, die schreibgeschützt ist.  Dem Prototyp können Eigenschaften und Methoden hinzugefügt werden, dem Objekt kann jedoch kein anderer Prototyp zugewiesen werden.  Benutzerdefinierten Objekten kann jedoch ein neuer Prototyp zugewiesen werden.  
  
 In den Methoden\- und Eigenschaftenlisten für jedes systeminterne Objekt in diesem Sprachverzeichnis wird angegeben, welche Bestandteil des Objektprototyps sind und welche nicht.  
  
## Anforderungen  
 [!INCLUDE[jsv2](../../includes/jsv2-md.md)]