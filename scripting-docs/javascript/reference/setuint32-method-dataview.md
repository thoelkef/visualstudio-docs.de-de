---
title: setUint32-Methode (DataView) | Microsoft Docs
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
ms.assetid: ab2894fe-4cdc-40c8-9503-951e42ca61e7
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4e4d2bf075c46f84c75a174b0ca5954b9cedf154
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="setuint32-method-dataview"></a>setUint32-Methode (DataView)
Legt den Uint32-Wert am angegebenen Byteoffset vom Beginn der Ansicht fest. Es ist keine Einschränkung der Ausrichtung. Alle Offset können Multi-Byte-Werte festgelegt werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
dataView.setUint32 (byteOffset, value, littleEndian);   
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
 Im folgende Beispiel wird gezeigt, wie die erste Uint32 in der DataView festgelegt.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]