---
title: "byteLength-Eigenschaft (Int8Array) | Microsoft Docs"
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
ms.assetid: 4e8457a8-2200-4d61-800e-f49fc1e916e5
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# byteLength-Eigenschaft (Int8Array)
Schreibgeschützt.  Die Länge dieses Arrays vom Beginn seines ArrayBuffers in Bytes, so wie während der Konstruktionszeit festgelegt.  
  
## Syntax  
  
```javascript  
var arrayByteLength = int8Array.byteLength;  
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
            var intArr = new Int8Array(buffer.byteLength);  
            alert(intArr.byteLength);  
        }  
    }  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv10](../../includes/jsv10-md.md)]