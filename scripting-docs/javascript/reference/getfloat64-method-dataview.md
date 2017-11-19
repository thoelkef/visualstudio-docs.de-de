---
title: getFloat64-Methode (DataView) | Microsoft Docs
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
ms.assetid: 347adeb6-b24c-4e7d-8b6b-8e36aacdcae1
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab6d52fcaa82cc957ba47b5ef2acdfbef90152d7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="getfloat64-method-dataview"></a>getFloat64-Methode (DataView)
Ruft den Float64-Wert am angegebenen Byteoffset vom Beginn der Ansicht ab. Es ist keine Einschränkung der Ausrichtung. Multi-Byte-Werte können aus jeder Offset abgerufen werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
var testFloat = dataView.getFloat64(byteOffset, littleEndian);   
```  
  
## <a name="parameters"></a>Parameter  
 `testFloat`  
 Erforderlich. Den Float64-Wert, der von der Methode zurückgegeben wird.  
  
 `byteOffset`  
 Die Position im Puffer, an dem der Wert abgerufen werden soll.  
  
 `littleEndian`  
 Dies ist optional. Wenn "false" oder nicht definiert ist, ein big-Endian-Wert gelesen werden soll, andernfalls ein little-Endian-Wert gelesen werden soll.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methoden auslösen eine Ausnahme, wenn sie hinter dem Ende der Sicht gelesen werden.  
  
## <a name="example"></a>Beispiel  
 Im folgende Beispiel wird das Abrufen von der ersten Float64 in der DataView veranschaulicht.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.getFloat64(0));  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]