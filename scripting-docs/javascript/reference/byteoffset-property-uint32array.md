---
title: "byteOffset-Eigenschaft (UInt32Array) | Microsoft Docs"
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
ms.assetid: 61b1b117-e197-4655-b487-97d08c098775
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# byteOffset-Eigenschaft (UInt32Array)
Schreibgeschützt.  Der Offset dieses Arrays vom Beginn seines ArrayBuffers in Bytes, wie zur Konstruktionszeit festgelegt.  
  
## Syntax  
  
```javascript  
var arrayOffset = uint32Array.byteOffset;  
```  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie der Offset des Arrays abgerufen wird.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Uint32Array(buffer.byteLength / 4);  
            alert(intArr.byteOffset);  
        }  
    }  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv10](../../includes/jsv10-md.md)]