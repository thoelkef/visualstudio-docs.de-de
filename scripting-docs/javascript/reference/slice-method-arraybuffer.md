---
title: Slice-Methode (ArrayBuffer) | Microsoft Docs
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
ms.assetid: 2dcc51ff-f444-4d51-80ba-3bcd845ba0ae
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25fc10a02b4a3422a6720ad91c8bba29906da0e5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640490"
---
# <a name="slice-method-arraybuffer"></a>slice-Methode (ArrayBuffer)
Gibt einen Abschnitt einer [ArrayBuffer](../../javascript/reference/arraybuffer-object.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
arrayBufferObj.slice(start, [end])   
```  
  
## <a name="parameters"></a>Parameter  
 `arrayBufferObj`  
 Erforderlich. Die [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) Objekt aus der Abschnitt kopiert werden.  
  
 `start`  
 Erforderlich. Der Byteindex am Anfang des zu kopierenden Abschnitts.  
  
 `end`  
 Dies ist optional. Der Byteindex am Ende des zu kopierenden Abschnitts.  
  
## <a name="remarks"></a>Hinweise  
 Die `slice` Methode gibt ein [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) Objekt, das den angegebenen Teil enthält `arrayBufferObj`.  
  
 Die `slice`-Methode kopiert bis zu dem von `end` angebenen Byte, schließt dieses jedoch nicht ein. Wenn `start` oder `end` ist negativ ist, wird der angegebene Index behandelt, als `length`  +  `start` oder `end`nahezu, in denen `length` ist die Länge des der [ArrayBuffer](../../javascript/reference/arraybuffer-object.md). Wenn `end` ausgelassen wird, wird die Extraktion bis zum Ende von `arrayBufferObj` fortgesetzt. Wenn `end` tritt ein, bevor `start`, keine Bytes kopiert werden, mit dem neuen [ArrayBuffer](../../javascript/reference/arraybuffer-object.md).  
  
## <a name="example"></a>Beispiel  
 In den folgenden Beispielen wird die Verwendung der `slice`-Methode gezeigt.  
  
```JavaScript  
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
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [ArrayBuffer-Objekt](../../javascript/reference/arraybuffer-object.md)