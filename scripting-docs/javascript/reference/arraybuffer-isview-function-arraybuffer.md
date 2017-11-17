---
title: ArrayBuffer.isView-Funktion (ArrayBuffer) | Microsoft Docs
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
ms.assetid: 1887324f-892b-4fcd-ad33-748ba9517a06
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5aaae2acb38aa2f8c4b5e49ea203e86665315700
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="arraybufferisview-function-arraybuffer"></a>ArrayBuffer.isView-Funktion (ArrayBuffer)
Bestimmt, ob ob ein Objekt eine Ansicht des Puffers bereitstellt.  
  
## <a name="syntax"></a>Syntax  
  
```JavaScript  
ArrayBuffer.isView(object)  
```  
  
#### <a name="parameters"></a>Parameter  
 `object`  
 Erforderlich. Das zu überprüfende Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 `true`, wenn eine der folgenden Bedingungen zutrifft:  
  
-   `object` ist ein `DataView`-Objekt.  
  
-   `object` ist ein typisiertes Array.  
  
 Andernfalls gibt diese Methode `false` zurück.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `isView`-Funktion zum Testen eines typisierten Arrays und eines `DataView`-Objekts.  
  
```JavaScript  
var uint = new UInt8ClampedArray(10);  
  
if(console && console.log) {  
    console.log( ArrayBuffer.isView(uint) ); // Outputs true  
{  
var dataView = new DataView(uint.buffer);  
  
if(console && console.log) {  
    console.log( ArrayBuffer.isView(dataView) ); // Outputs true.  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Uint8ClampedArray-Objekt](../../javascript/reference/uint8clampedarray-object-javascript.md)