---
title: "subarray-Methode (Uint32Array) | Microsoft Docs"
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
ms.assetid: 4c183208-12ec-4051-bf0f-a4f7c112cea1
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# subarray-Methode (Uint32Array)
Ruft eine neue Uint32Array\-Ansicht des [ArrayBuffer\-Objekt](../../javascript/reference/arraybuffer-object.md)\-Speichers für dieses Array ab, in dem die ersten und letzten Elemente des Unterarrays ab.  
  
## Syntax  
  
```javascript  
var newUint32Array = uint32Array.subarray(begin, end);  
```  
  
## Parameter  
 `newUint32Array`  
 Das von dieser Methode zurückgegebene Unterarray.  
  
 `begin`  
 Der Index des Anfangs des Arrays.  
  
 `end`  
 Der Index des Endes des Arrays.  Dies ist nicht eindeutig.  
  
## Hinweise  
 Wenn entweder der `begin` oder das `end` negativ ist, wird auf einen Index am Ende statt am Beginn des Arrays verwiesen.  Wenn `end` nicht angegeben wird, enthält das Unterarray alle Elemente vom `begin` bis zum Ende des typisierten Arrays.  Der durch die `begin`s\- und `end`werte festgelegte Bereich wird für das aktuelle Array an den gültigen Indexbereich geklammert.  Wenn die berechnete Länge des neuen TypedArrays negativ ist, wird sie an Null geklammert.  Das zurückgegebene Array hat denselben Typ wie das Array, auf dem diese Methode aufgerufen wird.  
  
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
            var intArr = new Uint32Array(buffer.byteLength / 4);  
            var subArr = intArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]