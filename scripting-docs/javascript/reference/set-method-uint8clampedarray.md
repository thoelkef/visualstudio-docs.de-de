---
title: "set-Methode (Uint8ClampedArray) | Microsoft Docs"
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
ms.assetid: 1298443d-5c4c-4329-9ad2-35e213dca157
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# set-Methode (Uint8ClampedArray)
Legt einen Wert oder ein Wertearray fest.  
  
## Syntax  
  
```javascript  
uint8ClampedArray.set(index, value); uint8ClampedArray.set(array, offset);   
```  
  
## Parameter  
 `index`  
 Der Index des festzulegenden Speicherorts.  
  
 `value`  
 Der festzulegende Wert.  
  
 `array`  
 Ein typisiertes oder nicht typisiertes, festzulegendes Array von Werten.  
  
 `offset`  
 Der Index im aktuellen Array, an dem die Werte geschrieben werden sollen.  
  
## Hinweise  
 Wenn das Eingabearray ein typisiertes Array ist, können die beiden Arrays den gleichen zugrunde liegende [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) verwenden.  In diesem Fall werden die Werte so festgelegt, als ob alle Daten zunächst in einen temporären Puffer kopiert wurden, der sich mit keinem der Arrays überschneidet, und anschließend die Daten aus dem temporären Puffer in das aktuelle Array kopiert werden.  
  
 Wenn der Offset plus die Länge des angegebenen Arrays außerhalb des gültigen Bereichs für das aktuelle typisierte Array liegt, wird eine Ausnahme ausgelöst.  
  
## Beispiel  
 Im folgenden Beispiel wird gezeigt, wie das erste Element des Arrays festgelegt wird.  
  
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
            intArr.set(0, 9);  
        }  
    }  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## Siehe auch  
 [ArrayBuffer\-Objekt](../../javascript/reference/arraybuffer-object.md)   
 [Uint8ClampedArray\-Objekt](../../javascript/reference/uint8clampedarray-object-javascript.md)