---
title: getInt16-Methode (DataView) | Microsoft Docs
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
ms.assetid: d364cbe0-48a6-4350-a6ca-9f563d7ae571
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a30804ddaa4840bfbd8a791ac5a5d4d82d107879
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="getint16-method-dataview"></a>getInt16-Methode (DataView)
Ruft den Int16-Wert am angegebenen Byteoffset vom Beginn der Ansicht ab. Es ist keine Einschränkung der Ausrichtung. Multi-Byte-Werte können aus jeder Offset abgerufen werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
var testInt = dataView.getInt16(byteOffset, littleEndian);   
```  
  
## <a name="parameters"></a>Parameter  
 `testInt`  
 Erforderlich. Der Int16-Wert, der von der Methode zurückgegeben wird.  
  
 `byteOffset`  
 Die Position im Puffer, an dem der Wert abgerufen werden soll.  
  
 `littleEndian`  
 Dies ist optional. Wenn "false" oder nicht definiert ist, ein big-Endian-Wert gelesen werden soll, andernfalls ein little-Endian-Wert gelesen werden soll.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methoden auslösen eine Ausnahme, wenn sie hinter dem Ende der Sicht gelesen werden.  
  
## <a name="example"></a>Beispiel  
 Im folgende Beispiel wird das Abrufen von der ersten Int16 in der DataView veranschaulicht.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.getInt16(0));  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]