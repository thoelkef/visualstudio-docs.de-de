---
title: "subarray-Methode (Int16Array) | Microsoft Docs"
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
ms.assetid: 8a7437c2-8c4e-41eb-a3d5-ec4f7399b81d
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# subarray-Methode (Int16Array)
Ruft eine neue Int16Array\-Ansicht [ArrayBuffer\-Objekt](../../javascript/reference/arraybuffer-object.md) des Speichers für dieses Array ab und gibt die ersten und letzten Member des Unterarrays an.  
  
## Syntax  
  
```javascript  
var newInt16Array = int16Array.subarray(begin, end);  
```  
  
## Parameter  
 `newInt16Array`  
 Das von dieser Methode zurückgegebene Unterarray.  
  
 `begin`  
 Der Index des Anfangs des Arrays.  
  
 `end`  
 Der Index des Endes des Arrays.  Dies ist nicht eindeutig.  
  
## Hinweise  
 Wenn entweder der `begin` oder das `end` negativ ist, wird auf einen Index am Ende statt am Beginn des Arrays verwiesen.  Wenn `end` nicht angegeben wird, enthält das Unterarray alle Elemente vom Anfang bis zum Ende des typisierten Arrays.  Der durch die `begin`s\- und `end`werte festgelegte Bereich wird für das aktuelle Array an den gültigen Indexbereich geklammert.  Wenn die berechnete Länge des neuen TypedArrays negativ ist, wird sie an Null geklammert.  Das zurückgegebene Array hat denselben Typ wie das Array, auf dem diese Methode aufgerufen wird.  
  
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
            var intArr = new Int16Array(buffer.byteLength / 2);  
            var subArr = intArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv10](../../includes/jsv10-md.md)]