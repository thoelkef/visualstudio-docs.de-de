---
title: "byteLength-Eigenschaft (Uint8ClampedArray) | Microsoft Docs"
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
ms.assetid: 37ae1728-8e2c-496c-bb77-f5f85b1ecbba
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# byteLength-Eigenschaft (Uint8ClampedArray)
Schreibgeschützt.  Die Länge dieses Arrays vom Beginn des [ArrayBuffers](../../javascript/reference/arraybuffer-object.md) in Bytes, so wie bei der Konstruktion festgelegt.  
  
## Syntax  
  
```javascript  
var arrayByteLength = uint8ClampedArray.byteLength;  
```  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie die Länge des Arrays abgerufen wird.  
  
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
            alert(intArr.byteLength);  
        }  
    }  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv11_winonly](../../includes/jsv11-winonly-md.md)]  
  
## Siehe auch  
 [ArrayBuffer\-Objekt](../../javascript/reference/arraybuffer-object.md)   
 [Uint8ClampedArray\-Objekt](../../javascript/reference/uint8clampedarray-object-javascript.md)