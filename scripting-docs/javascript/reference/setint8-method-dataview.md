---
title: setInt8-Methode (DataView) | Microsoft Docs
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
ms.assetid: 0a0e1450-e0c4-4778-8706-4d332442d882
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6f9bd9c4b3bea25686036d199d1a987927172d1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639490"
---
# <a name="setint8-method-dataview"></a>setInt8-Methode (DataView)
Speichert einen Int8-Wert am angegebenen Byteoffset vom Beginn der Ansicht an.  
  
## <a name="syntax"></a>Syntax  
  
```  
dataView.setInt8(byteOffset, value);   
```  
  
## <a name="parameters"></a>Parameter  
 `byteOffset`  
 Die Position im Puffer, an dem der Wert festgelegt werden soll.  
  
 `value`  
 Der festzulegende Wert.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methoden auslösen eine Ausnahme, wenn sie hinter dem Ende der Ansicht schreiben würden.  
  
## <a name="example"></a>Beispiel  
 Im folgende Beispiel wird gezeigt, wie der ersten Int8 in der DataView festgelegt wird.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setInt8(0, 9);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]