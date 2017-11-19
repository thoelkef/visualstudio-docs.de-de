---
title: setFloat64-Methode (DataView) | Microsoft Docs
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
ms.assetid: 63d2c631-876f-4d4b-b3b6-62b0aaffe6c5
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e22552e4190c74b520dfce853be6e9d1364764e3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="setfloat64-method-dataview"></a>setFloat64-Methode (DataView)
Legt den Float64-Wert am angegebenen Byteoffset vom Beginn der Ansicht fest. Es ist keine Einschränkung der Ausrichtung. Alle Offset können Multi-Byte-Werte festgelegt werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
dataView.setFloat64 (byteOffset, value, littleEndian);   
```  
  
## <a name="parameters"></a>Parameter  
 `byteOffset`  
 Die Position im Puffer, an dem der Wert abgerufen werden soll.  
  
 `value`  
 Der festzulegende Wert.  
  
 `littleEndian`  
 Dies ist optional. Wenn "false" oder nicht definiert ist, ein big-Endian-Wert geschrieben werden soll, andernfalls ein little-Endian-Wert geschrieben werden soll.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methoden auslösen eine Ausnahme, wenn sie hinter dem Ende der Ansicht schreiben würden.  
  
## <a name="example"></a>Beispiel  
 Im folgende Beispiel wird gezeigt, wie die erste Float64 in der DataView festgelegt.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setFloat64(0, 9.1);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]