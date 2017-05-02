---
title: "setUint8-Methode (DataView) | Microsoft Docs"
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
ms.assetid: b294262b-3f4b-4183-a292-5a6982cbdd27
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# setUint8-Methode (DataView)
Speichert einen Uint8\-Wert am angegebenen Byteoffset vom Beginn der Ansicht.  
  
## Syntax  
  
```  
dataView.setUint8(byteOffset, value);   
```  
  
## Parameter  
 `byteOffset`  
 Die Position im Puffer, an der der Wert festgelegt werden soll.  
  
 `value`  
 Der festzulegende Wert.  
  
## Hinweise  
 Diese Methoden lösen eine Ausnahme aus, wenn sie über das Ende der Ansicht hinaus schreiben.  
  
## Beispiel  
 Im folgenden Beispiel wird dargestellt, wie der erste Uint8\-Wert im DataView\-Objekt festgelegt wird.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setUint8(0, 9);  
        }  
    }  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv10](../../includes/jsv10-md.md)]