---
title: "byteOffset-Eigenschaft (DataView) | Microsoft Docs"
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
ms.assetid: 3b3e68bc-1476-4a32-a18d-6efa375bce0f
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# byteOffset-Eigenschaft (DataView)
Schreibgeschützt.  Das Offset dieser Ansicht vom Beginn seines ArrayBuffers in Bytes, so wie während der Konstruktionszeit festgelegt.  
  
## Syntax  
  
```javascript  
var arrayOffset = dataView.byteOffset;  
```  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie die Länge einer DataView abgerufen wird.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.byteOffset)  
        }  
    }  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv10](../../includes/jsv10-md.md)]