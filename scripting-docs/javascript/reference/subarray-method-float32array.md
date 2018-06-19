---
title: Subarray-Methode (Float32Array) | Microsoft Docs
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
ms.assetid: 97aa27c0-d650-411e-b929-dd9c4a2ae9a5
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 78d8c729298fe80d841d7c4750e4e6817120c9d3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639870"
---
# <a name="subarray-method-float32array"></a>subarray-Methode (Float32Array)
Ruft eine neue Float32Array-Ansicht des der [ArrayBuffer-Objekt](../../javascript/reference/arraybuffer-object.md) -Speichers für dieses Array ab und gibt die erste und letzte Member des Unterarrays.  
  
## <a name="syntax"></a>Syntax  
  
```JavaScript  
var newFloat32Array = float32Array.subarray(begin, end);  
```  
  
## <a name="parameters"></a>Parameter  
 `newFloat32Array`  
 Das von dieser Methode zurückgegebene Unterarray.  
  
 `begin`  
 Der Index des Anfangs des Arrays.  
  
 `end`  
 Der Index des Endes des Arrays.  
  
## <a name="remarks"></a>Hinweise  
 Wenn entweder der `begin` oder das `end` negativ ist, wird auf einen Index am Ende statt am Beginn des Arrays verwiesen. Wenn `end` nicht angegeben wird, enthält das Unterarray alle Elemente vom `begin` bis zum Ende des typisierten Arrays. Der durch die `begin`s- und `end`werte festgelegte Bereich wird für das aktuelle Array an den gültigen Indexbereich geklammert. Wenn die berechnete Länge des neuen TypedArrays negativ ist, wird sie an Null geklammert. Das zurückgegebene Array hat denselben Typ wie das Array, auf dem diese Methode aufgerufen wird.  
  
## <a name="example"></a>Beispiel  
 Im folgende Beispiel wird gezeigt, wie ein Unterarray mit drei Elementen, beginnend mit dem ersten Element des Arrays abgerufen wird.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var floatArr = new Float32Array(buffer.byteLength / 4);  
            var subArr = floatArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]