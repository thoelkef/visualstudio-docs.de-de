---
title: setFloat32-Methode (DataView) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b3f68048-c817-48d2-bc17-945e3bcc94d7
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a72bf2781bfbae7c7cd301d02ad71ebfbeffa13
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639150"
---
# <a name="setfloat32-method-dataview"></a>setFloat32-Methode (DataView)
Legt den Float32-Wert am angegebenen Byteoffset vom Beginn der Ansicht fest. Es ist keine Einschränkung der Ausrichtung. Alle Offset können Multi-Byte-Werte festgelegt werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
dataView.setFloat32 (byteOffset, value, littleEndian);   
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
 Im folgende Beispiel wird gezeigt, wie die erste Float32 in der DataView festgelegt.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setFloat32(0, 9.1);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]