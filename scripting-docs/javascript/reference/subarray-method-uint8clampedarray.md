---
title: Subarray-Methode (Uint8ClampedArray) | Microsoft Docs
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
ms.assetid: 309ed9e8-5805-47ab-b3ed-501cae1323dd
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 76cda8b123b02b4c19a7fd162f3bfbce4540d149
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="subarray-method-uint8clampedarray"></a>subarray-Methode (Uint8ClampedArray)
Ruft eine neue [Uint8ClampedArray](../../javascript/reference/uint8array-object.md) -Ansicht der [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) -Speichers für dieses Array ab und gibt die erste und letzte Member des Unterarrays.  
  
## <a name="syntax"></a>Syntax  
  
```JavaScript  
var newUint8ClampedArray = uint8ClampedArray.subarray(begin, end);  
```  
  
## <a name="parameters"></a>Parameter  
 `newUint8ClampedArray`  
 Erforderlich. Das von dieser Methode zurückgegebene Unterarray.  
  
 `begin`  
 Optional. Der Index des Arrayanfangs.  
  
 `end`  
 Optional. Der Index des Endes des Arrays. Dies ist nicht eindeutig.  
  
## <a name="remarks"></a>Hinweise  
 Wenn entweder der `begin` oder das `end` negativ ist, wird auf einen Index am Ende statt am Beginn des Arrays verwiesen. Wenn `end` nicht angegeben wird, enthält das Unterarray alle Elemente vom `begin` bis zum Ende des typisierten Arrays. Der durch die `begin`s- und `end`werte festgelegte Bereich wird für das aktuelle Array an den gültigen Indexbereich geklammert. Wenn die berechnete Länge des neuen TypedArrays negativ ist, wird sie an Null geklammert. Das zurückgegebene Array hat denselben Typ wie das Array, für das diese Methode aufgerufen wird.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird gezeigt, wie ein Subarray mit der Länge von zwei Elementen abgerufen wird, beginnend mit dem ersten Element des Arrays.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var intArr = new Uint8ClampedArray(buffer.byteLength);  
            var subArr = intArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Uint8Array-Objekt](../../javascript/reference/uint8array-object.md)   
 [ArrayBuffer-Objekt](../../javascript/reference/arraybuffer-object.md)   
 [Uint8ClampedArray-Objekt](../../javascript/reference/uint8clampedarray-object-javascript.md)