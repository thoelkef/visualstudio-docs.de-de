---
title: "getInt16-Methode (DataView) | Microsoft Docs"
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
ms.assetid: d364cbe0-48a6-4350-a6ca-9f563d7ae571
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# getInt16-Methode (DataView)
Ruft den Int16\-Wert am angegebenen Byteoffset vom Beginn der Ansicht ab.  Es gibt keine Ausrichtungseinschränkung; Multi\-Byte\-Werte werden bei jedem Offset abgerufen.  
  
## Syntax  
  
```  
var testInt = dataView.getInt16(byteOffset, littleEndian);   
```  
  
## Parameter  
 `testInt`  
 Erforderlich.  Der Int16\-Wert, der von der Methode zurückgegeben wird.  
  
 `byteOffset`  
 Die Position im Puffer, an der der Wert abgerufen werden soll.  
  
 `littleEndian`  
 Optional.  Wenn "false" oder nicht definiert, wird ein Big\-Endian\-Wert gelesen; andernfalls sollte ein Little\-Endian\-Wert gelesen werden.  
  
## Hinweise  
 Diese Methoden lösen eine Ausnahme aus, wenn sie über das Ende der Ansicht hinaus lesen.  
  
## Beispiel  
 Im folgenden Beispiel wird dargestellt, wie der erste Int16\-Wert im DataView abgerufen wird.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.getInt16(0));  
        }  
    }  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv10](../../includes/jsv10-md.md)]