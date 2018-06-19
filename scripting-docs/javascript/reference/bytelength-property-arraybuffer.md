---
title: ByteLength-Eigenschaft (ArrayBuffer) | Microsoft Docs
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
ms.assetid: c158fa59-d006-4842-9d06-0fd8e630ea31
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5f576eb85652a7c250e0f446f4082dd6207e8fb2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633500"
---
# <a name="bytelength-property-arraybuffer"></a>byteLength-Eigenschaft (ArrayBuffer)
Schreibgeschützt. Die Länge des ArrayBuffer-Objekts in Bytes.  
  
## <a name="syntax"></a>Syntax  
  
```JavaScript  
var arrayLength = arrayBuffer.byteLength;  
```  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="example"></a>Beispiel  
 Im folgende Beispiel wird gezeigt, wie die Bytelänge der das arraybuffer-Objekt abgerufen wird.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
  
        alert(buffer.byteLength);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]