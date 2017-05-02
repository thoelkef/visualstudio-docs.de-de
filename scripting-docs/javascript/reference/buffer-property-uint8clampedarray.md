---
title: "buffer-Eigenschaft (Uint8ClampedArray) | Microsoft Docs"
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
ms.assetid: 4b87d767-4246-4cf4-bb1d-241b3516397a
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# buffer-Eigenschaft (Uint8ClampedArray)
Schreibgeschützt.  Ruft den [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) ab, auf den durch dieses Array verwiesen wird.  
  
## Syntax  
  
```javascript  
var arrayBuffer = uint8ClampedArray.buffer;  
```  
  
## Beispiel  
 Das folgende Beispiel zeigt, wie der ArrayBuffer des Arrays abgerufen wird.  
  
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
            alert(intArr.buffer.byteLength);  
        }  
    }  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv11_winonly](../../includes/jsv11-winonly-md.md)]  
  
## Siehe auch  
 [ArrayBuffer\-Objekt](../../javascript/reference/arraybuffer-object.md)   
 [Uint8ClampedArray\-Objekt](../../javascript/reference/uint8clampedarray-object-javascript.md)