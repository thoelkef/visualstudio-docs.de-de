---
title: Set-Methode (Uint8ClampedArray) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1298443d-5c4c-4329-9ad2-35e213dca157
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed7635559e615746c577560f1a9266b26acd959d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="set-method-uint8clampedarray"></a>set-Methode (Uint8ClampedArray)
Legt einen Wert oder ein Wertearray fest.  
  
## <a name="syntax"></a>Syntax  
  
```JavaScript  
uint8ClampedArray.set(index, value);  
uint8ClampedArray.set(array, offset);  
  
```  
  
## <a name="parameters"></a>Parameter  
 `index`  
 Der Index des festzulegenden Speicherorts.  
  
 `value`  
 Der festzulegende Wert.  
  
 `array`  
 Ein typisiertes oder nicht typisiertes, festzulegendes Array von Werten.  
  
 `offset`  
 Der Index im aktuellen Array, an dem die Werte geschrieben werden sollen.  
  
## <a name="remarks"></a>Hinweise  
 Wenn das Eingabearray ein typisiertes Array ist, die beiden Arrays dürfen verwenden das gleiche zugrunde liegende [ArrayBuffer](../../javascript/reference/arraybuffer-object.md). In diesem Fall werden die Werte so festgelegt, als ob alle Daten zunächst in einen temporären Puffer kopiert wurden, der sich mit keinem der Arrays überschneidet, und anschließend die Daten aus dem temporären Puffer in das aktuelle Array kopiert werden.  
  
 Wenn der Offset plus die Länge des angegebenen Arrays außerhalb des gültigen Bereichs für das aktuelle typisierte Array liegt, wird eine Ausnahme ausgelöst.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird gezeigt, wie das erste Element des Arrays festgelegt wird.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [ArrayBuffer-Objekt](../../javascript/reference/arraybuffer-object.md)   
 [Uint8ClampedArray-Objekt](../../javascript/reference/uint8clampedarray-object-javascript.md)