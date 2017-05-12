---
title: "setUint32-Methode (DataView) | Microsoft Docs"
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
ms.assetid: ab2894fe-4cdc-40c8-9503-951e42ca61e7
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# setUint32-Methode (DataView)
Legt den Uint32\-Wert am angegebenen Byteoffset vom Beginn der Ansicht fest.  Es gibt keine Ausrichtungseinschränkung; Multi\-Byte\-Werte werden bei jedem Offset festgelegt.  
  
## Syntax  
  
```  
dataView.setUint32 (byteOffset, value, littleEndian);   
```  
  
## Parameter  
 `byteOffset`  
 Die Position im Puffer, an der der Wert abgerufen werden soll.  
  
 `value`  
 Der festzulegende Wert.  
  
 `littleEndian`  
 Optional.  Wenn "false" oder nicht definiert, wird ein Big\-Endian\-Wert geschrieben; andernfalls sollte ein Little\-Endian\-Wert geschrieben werden.  
  
## Hinweise  
 Diese Methoden lösen eine Ausnahme aus, wenn sie über das Ende der Ansicht hinaus schreiben.  
  
## Beispiel  
 Im folgenden Beispiel wird dargestellt, wie der erste Uint32\-Wert im DataView\-Objekt festgelegt wird.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setUint32(0, 9);  
        }  
    }  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]