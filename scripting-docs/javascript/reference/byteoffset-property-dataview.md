---
title: ByteOffset-Eigenschaft (DataView) | Microsoft Docs
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
ms.assetid: 3b3e68bc-1476-4a32-a18d-6efa375bce0f
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7cfc829f9821dbf4eb440071b9c1971e8c4e882
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="byteoffset-property-dataview"></a>byteOffset-Eigenschaft (DataView)
Schreibgeschützt. Der Offset dieser Ansicht vom Beginn des ArrayBuffers in Bytes, so wie während der Konstruktionszeit festgelegt.  
  
## <a name="syntax"></a>Syntax  
  
```JavaScript  
var arrayOffset = dataView.byteOffset;  
```  
  
## <a name="example"></a>Beispiel  
 Im folgende Beispiel wird gezeigt, wie die Länge eines DataView-Objekts abgerufen werden.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.byteOffset)  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]