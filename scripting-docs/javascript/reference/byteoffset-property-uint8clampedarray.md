---
title: "byteOffset-Eigenschaft (Uint8ClampedArray) | Microsoft Docs"
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
ms.assetid: bfc22cf4-00e3-4e2c-8419-032b179aa8da
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# byteOffset-Eigenschaft (Uint8ClampedArray)
Schreibgeschützt.  Der Offset dieses Arrays vom Beginn des [ArrayBuffers](../../javascript/reference/arraybuffer-object.md) in Bytes, so wie bei der Konstruktion festgelegt.  
  
## Syntax  
  
```javascript  
var arrayOffset = uint8ClampedArray.byteOffset;  
```  
  
## Beispiel  
 Das folgende Beispiel zeigt, wie der Offset des Arrays abgerufen wird.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Uint8ClampedArray(buffer.byteLength);  
            alert(intArr.byteOffset);  
        }  
    }  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## Siehe auch  
 [ArrayBuffer\-Objekt](../../javascript/reference/arraybuffer-object.md)   
 [Uint8ClampedArray\-Objekt](../../javascript/reference/uint8clampedarray-object-javascript.md)