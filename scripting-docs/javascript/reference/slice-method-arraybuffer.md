---
title: "slice-Methode (ArrayBuffer) | Microsoft Docs"
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
ms.assetid: 2dcc51ff-f444-4d51-80ba-3bcd845ba0ae
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# slice-Methode (ArrayBuffer)
Gibt einen Abschnitt eines [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) zurück.  
  
## Syntax  
  
```  
arrayBufferObj.slice(start, [end])   
```  
  
## Parameter  
 `arrayBufferObj`  
 Erforderlich.  Das [ArrayBuffer](../../javascript/reference/arraybuffer-object.md)\-Objekt, aus dem der Abschnitt kopiert wird.  
  
 `start`  
 Erforderlich.  Der Byteindex am Anfang des zu kopierenden Abschnitts.  
  
 `end`  
 Dies ist optional.  Der Byteindex am Ende des zu kopierenden Abschnitts.  
  
## Hinweise  
 Die `slice`\-Methode gibt ein [ArrayBuffer](../../javascript/reference/arraybuffer-object.md)\-Objekt zurück, das den angegebenen Teil von `arrayBufferObj` enthält.  
  
 Die `slice`\-Methode kopiert bis zu dem von `end` angebenen Byte, schließt dieses jedoch nicht ein.  Wenn `start` oder `end` negativ ist, wird der angegebene Index als `length` \+ `start` bzw. `end` behandelt, wobei `length` die Länge des [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) ist.  Wenn `end` ausgelassen wird, wird die Extraktion bis zum Ende von `arrayBufferObj` fortgesetzt.  Wenn `end` vor `start` eintritt, werden keine Bytes in den neuen [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) kopiert.  
  
## Beispiel  
 In den folgenden Beispielen wird die Verwendung der `slice`\-Methode gezeigt.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer1 = req.response;  
            var buffer2 = buffer1.slice(40, 48);  
            var dataview = new DataView(buffer2);  
            var ints = new Int32Array(buffer2.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[1]);  
        }  
    }  
```  
  
## Anforderungen  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## Siehe auch  
 [ArrayBuffer\-Objekt](../../javascript/reference/arraybuffer-object.md)