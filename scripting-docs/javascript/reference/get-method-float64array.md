---
title: "Get-Methode (Float64Array) | Microsoft Docs"
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
ms.assetid: debbe2f4-fe1e-4f9d-af7d-b24430bfa962
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Get-Methode (Float64Array)
Kann unterdrückt werden.  Ruft das Element am angegebenen Index ab.  
  
## Syntax  
  
```javascript  
var value = float64Array.get(index);  
```  
  
## Parameter  
 `value`  
 Der Wert, der von dieser Methode zurückgegeben wird.  
  
 `index`  
 Der Index, an dem das Element des Arrays abgerufen werden soll.  
  
## Beispiel  
 Im folgenden Beispiel wird gezeigt, wie das erste Element des Arrays abgerufen wird.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var floatArr = new Float64Array(buffer.byteLength / 4);  
            var element = floatArr.getFloat64(0);  
        }  
    }  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]