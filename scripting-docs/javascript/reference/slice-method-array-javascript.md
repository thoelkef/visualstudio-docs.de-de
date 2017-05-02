---
title: "slice-Methode (Array) (JavaScript) | Microsoft Docs"
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
  - "slice"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Nullbasierter Index"
  - "Array-Objekt"
  - "slice-Methode"
ms.assetid: 3c122219-14de-4126-b091-809659c026d6
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# slice-Methode (Array) (JavaScript)
Gibt einen Abschnitt eines Arrays zurück.  
  
## Syntax  
  
```  
  
arrayObj.slice(start, [end])   
```  
  
## Parameter  
 `arrayObj`  
 Erforderlich.  Ein `Array`\-Objekt.  
  
 `start`  
 Erforderlich.  Der Anfang des angegebenen Abschnitts von `arrayObj`.  
  
 `end`  
 Optional.  Das Ende des angegebenen Abschnitts von `arrayObj`.  
  
## Hinweise  
 Die `slice`\-Methode gibt ein `Array`\-Objekt zurück, das den angegebenen Abschnitt von `arrayObj` enthält.  
  
 Die `slice`\-Methode kopiert bis zu dem Element, das durch `end` angegeben wird. Das Element ist jedoch nicht in der Kopie enthalten.  Wenn `start` negativ ist, wird der Parameter als `length` \+ `start` behandelt, wobei `length` die Länge des Arrays ist.  Wenn `end` negativ ist, wird der Parameter als `length` \+ `end` behandelt, wobei `length` die Länge des Arrays ist.  Wird `end` ausgelassen, wird die Extraktion bis zum Ende von `arrayObj` fortgesetzt.  Wenn `end` vor `start` steht, werden keine Elemente in das neue Array kopiert.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `slice`\-Methode veranschaulicht.  Im ersten Beispiel werden alle Elemente von `myArray` bis auf das letzte in `newArray` kopiert.  Im zweiten Beispiel werden nur die letzten beiden Elemente aus `myArray` in `newArray` kopiert.  
  
```javascript  
var origArray = [3, 5, 7, 9];  
var newArray = origArray. slice(0, -1);  
document.write(origArray);  
document.write("<br/>");  
newArray = origArray. slice(-2);  
document.write(newArray);  
  
// Output:  
// 3,5,7,9  
// 7,9  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../includes/jsv3-md.md)]  
  
## Siehe auch  
 [slice\-Methode \(String\)](../../javascript/reference/slice-method-string-javascript.md)   
 [String\-Objekt](../../javascript/reference/string-object-javascript.md)