---
title: Subarray-Methode (Int8Array) | Microsoft Docs
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
ms.assetid: 46271ed6-a3c3-41fb-bd6f-81efa9e8dedc
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e32c3a0da7e3173273eb40bf52bb6583bd77df51
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640010"
---
# <a name="subarray-method-int8array"></a>subarray-Methode (Int8Array)
Ruft eine neue Int8Array-Ansicht des ArrayBuffer-Speichers für dieses Array ab und verweist hierbei auf die Elemente zu Beginn, eingeschlossene Elemente, Elemente bis zum Ende und ausgeschlossene Elemente.  
  
## <a name="syntax"></a>Syntax  
  
```JavaScript  
var newInt8Array = int8Array.subset(begin, end);  
```  
  
## <a name="parameters"></a>Parameter  
 `newInt8Array`  
 Das von dieser Methode zurückgegebene Unterarray.  
  
 `begin`  
 Der Index des Anfangs des Arrays.  
  
 `end`  
 Der Index des Endes des Arrays. Dies ist nicht eindeutig.  
  
## <a name="remarks"></a>Hinweise  
 Wenn entweder der Beginn oder das Ende negativ ist, wird am Ende statt am Beginn des Arrays auf einen Index verwiesen. Wenn das Ende nicht angegeben ist, enthält das Unterarray alle Elemente vom Beginn bis zum Ende des TypedArray. Der durch die Anfangs- und Endwerte festgelegte Bereich wird für das aktuelle Array an den gültigen Indexbereich gebunden. Wenn die berechnete Länge des neuen TypedArray negativ ist, wird sie an Null gebunden. Das zurückgegebene TypedArray hat denselben Typ wie das Array, für das diese Methode aufgerufen wird.  
  
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
            var dataView = new DataView(buffer);  
            var intArr = new Int8Array(buffer.byteLength);  
            var subArr = intArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]