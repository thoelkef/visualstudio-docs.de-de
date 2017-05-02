---
title: "subarray-Methode (Uint8ClampedArray) | Microsoft Docs"
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
ms.assetid: 309ed9e8-5805-47ab-b3ed-501cae1323dd
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# subarray-Methode (Uint8ClampedArray)
Ruft eine neue [Uint8ClampedArray](../../javascript/reference/uint8array-object.md)\-Ansicht des [ArrayBuffer](../../javascript/reference/arraybuffer-object.md)\-Speichers für dieses Array ab und gibt die ersten und letzten Member des Unterarrays an.  
  
## Syntax  
  
```javascript  
var newUint8ClampedArray = uint8ClampedArray.subarray(begin, end);  
```  
  
## Parameter  
 `newUint8ClampedArray`  
 Erforderlich.  Das von dieser Methode zurückgegebene Unterarray.  
  
 `begin`  
 Dies ist optional.  Der Index des Anfangs des Arrays.  
  
 `end`  
 Dies ist optional.  Der Index des Endes des Arrays.  Dies ist nicht eindeutig.  
  
## Hinweise  
 Wenn entweder der `begin` oder das `end` negativ ist, wird auf einen Index am Ende statt am Beginn des Arrays verwiesen.  Wenn `end` nicht angegeben wird, enthält das Unterarray alle Elemente vom `begin` bis zum Ende des typisierten Arrays.  Der durch die `begin`s\- und `end`werte festgelegte Bereich wird für das aktuelle Array an den gültigen Indexbereich geklammert.  Wenn die berechnete Länge des neuen TypedArrays negativ ist, wird sie an Null geklammert.  Das zurückgegebene Array hat denselben Typ wie das Array, für das diese Methode aufgerufen wird.  
  
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
            var intArr = new Uint8ClampedArray(buffer.byteLength);  
            var subArr = intArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv11_winonly](../../includes/jsv11-winonly-md.md)]  
  
## Siehe auch  
 [Uint8Array\-Objekt](../../javascript/reference/uint8array-object.md)   
 [ArrayBuffer\-Objekt](../../javascript/reference/arraybuffer-object.md)   
 [Uint8ClampedArray\-Objekt](../../javascript/reference/uint8clampedarray-object-javascript.md)