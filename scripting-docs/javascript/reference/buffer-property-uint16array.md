---
title: "buffer-Eigenschaft (Uint16Array) | Microsoft Docs"
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
ms.assetid: 357ae766-a2c1-4f7a-8b4c-e80c28340943
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# buffer-Eigenschaft (Uint16Array)
Schreibgeschützt.  Ruft den ArrayBuffer ab, auf den durch dieses Array verwiesen wird.  
  
## Syntax  
  
```javascript  
var arrayBuffer = uint16Array.buffer;  
```  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie der ArrayBuffer des Arrays abgerufen wird.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Uint16Array(buffer.byteLength / 2);  
            alert(intArr.buffer.byteLength);  
        }  
    }  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]