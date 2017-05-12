---
title: "subarray-Methode (Int8Array) | Microsoft Docs"
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
ms.assetid: 46271ed6-a3c3-41fb-bd6f-81efa9e8dedc
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# subarray-Methode (Int8Array)
Ruft eine neue Int8Array\-Ansicht des ArrayBuffer\-Speichers für dieses Array ab und verweist hierbei auf die Elemente zu Beginn, eingeschlossene Elemente, Elemente bis zum Ende und ausgeschlossene Elemente.  
  
## Syntax  
  
```javascript  
var newInt8Array = int8Array.subset(begin, end);  
```  
  
## Parameter  
 `newInt8Array`  
 Das von dieser Methode zurückgegebene Unterarray.  
  
 `begin`  
 Der Index des Anfangs des Arrays.  
  
 `end`  
 Der Index des Endes des Arrays.  Dies ist nicht eindeutig.  
  
## Hinweise  
 Wenn entweder der Beginn oder das Ende negativ ist, wird am Ende statt am Beginn des Arrays auf einen Index verwiesen.  Wenn das Ende nicht angegeben ist, enthält das Unterarray alle Elemente vom Beginn bis zum Ende des TypedArray.  Der durch die Anfangs\- und Endwerte festgelegte Bereich wird für das aktuelle Array an den gültigen Indexbereich gebunden.  Wenn die berechnete Länge des neuen TypedArray negativ ist, wird sie an Null gebunden.  Das zurückgegebene TypedArray hat denselben Typ wie das Array, für das diese Methode aufgerufen wird.  
  
## Beispiel  
 Im folgenden Beispiel wird gezeigt, wie ein Subarray mit der Länge von zwei Elementen abgerufen wird, beginnend mit dem ersten Element des Arrays.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Int8Array(buffer.byteLength);  
            var subArr = intArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]