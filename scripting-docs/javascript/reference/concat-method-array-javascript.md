---
title: "concat-Methode (Array) (JavaScript) | Microsoft Docs"
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
  - "concat"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "concat-Methode (Array)"
  - "Concat-Methode"
ms.assetid: bc2b4a6a-209e-4d59-8c24-59db01d53b1e
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# concat-Methode (Array) (JavaScript)
Kombiniert zwei oder mehr Arrays.  
  
## Syntax  
  
```  
  
array1.concat([item1[, item2[, . . . [, itemN]]]])   
```  
  
## Parameter  
 `array1`  
 Erforderlich.  Das `Array`\-Objekt, mit dem die anderen Arrays verkettet werden.  
  
 `item1,. . ., itemN`  
 Optional.  Weitere Elemente, die am Ende von `array1` hinzugefügt werden sollen.  
  
## Hinweise  
 Die Methode `concat` gibt ein `Array`\-Objekt zurück, das die Verkettung von `array1` und allen anderen bereitgestellten Elementen enthält.  
  
 Die dem Array hinzuzufügenden Elemente \(*itemN Element1*\) werden geordnet hinzugefügt, beginnend mit dem ersten Element in der Liste.  Wenn eines der Elemente ein Array ist, wird dessen Inhalt am Ende von `array1` angefügt.  Wenn das Element kein Array ist, wird es am Ende des Arrays als einzelnes Arrayelement angefügt.  
  
 Elemente von Quellarrays werden wie folgt in das resultierende Array kopiert:  
  
-   Wenn ein Objekt aus einem beliebigen Array kopiert wurde, das mit dem neuen Array verkettet wird, zeigt der Objektverweis weiterhin auf dasselbe Objekt.  Eine im neuen oder im ursprünglichen Array vorgenommene Änderung bewirkt, dass eine entsprechende Änderung im jeweils anderen Array vorgenommen wird.  
  
-   Werden eine Zahl oder ein Zeichenfolgenwert dem neuen Array hinzugefügt, wird nur der Wert kopiert.  Änderungen eines Werts in einem Arrays haben keine Auswirkungen auf den Wert im anderen Array.  
  
## Beispiel  
 Im folgenden Codebeispiel wird die Anwendung der `concat`\-Methode auf ein Array veranschaulicht:  
  
```javascript  
var a, b, c, d;  
a = new Array(1,2,3);  
b = "dog";  
c = new Array(42, "cat");  
d = a.concat(b, c);  
document.write(d);  
  
//Output:   
1, 2, 3, "dog", 42, "cat"  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## Siehe auch  
 [concat\-Methode \(String\)](../../javascript/reference/concat-method-string-javascript.md)   
 [join\-Methode \(Array\)](../../javascript/reference/join-method-array-javascript.md)