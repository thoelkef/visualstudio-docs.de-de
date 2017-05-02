---
title: "Array.from-Funktion (Array) (JavaScript) | Microsoft Docs"
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
ms.assetid: 1bf59a99-f860-4c4d-b4c6-d5f1f946a490
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Array.from-Funktion (Array) (JavaScript)
Gibt ein Array aus einem arrayähnlichen oder iterierbaren Objekt zurück.  
  
## Syntax  
  
```  
Array.from (arrayLike [ , mapfn [ , thisArg ] ] );  
```  
  
#### Parameter  
 `arrayLike`  
 Erforderlich.  Ein arrayähnliches oder iterierbares Objekt.  
  
 `mapfn`  
 Optional.  Eine Zuordnungsfunktion zum Aufrufen der einzelnen Elemente in `arrayLike`.  
  
 `thisArg`  
 Optional.  Gibt das `this`\-Objekt in der Zuordnungsfunktion an.  
  
## Hinweise  
 Der `arrayLike`\-Parameter muss entweder ein Objekt mit indizierten Elementen und einer `length`\-Eigenschaft oder ein iterierbares Objekt sein, z. B. ein `Set`\-Objekt.  
  
 Die optionale Zuordnungsfunktion wird für jedes Element im Array aufgerufen.  
  
## Beispiel  
 Im folgenden Beispiel wird ein Array aus einer Auflistung von DOM\-Elementknoten zurückgegeben.  
  
```javascript  
var elemArr = Array.from(document.querySelectorAll('*'));  
var elem = elemArr[0]; // elem contains a reference to the first DOM element  
  
```  
  
## Beispiel  
 Im folgenden Beispiel wird ein Array von Zeichen zurückgegeben.  
  
```javascript  
var charArr = Array.from("abc");  
// charArr[0] == "a";  
```  
  
## Beispiel  
 Im folgenden Beispiel wird ein Array von Objekten zurückgegeben, die in der Auflistung enthalten sind.  
  
```javascript  
var setObj = new Set("a", "b", "c");  
var objArr = Array.from(setObj);  
// objArr[1] == "b";  
  
```  
  
## Beispiel  
 Das folgende Beispiel zeigt die Verwendung der Pfeilsyntax und eine Zuordnungsfunktion, um den Wert von Elementen zu ändern.  
  
```javascript  
var arr = Array.from([1, 2, 3], x => x * 10);  
// arr[0] == 10;  
// arr[1] == 20;  
// arr[2] == 30;  
```  
  
## Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]