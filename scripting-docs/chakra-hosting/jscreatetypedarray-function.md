---
title: JsCreateTypedArray-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 937a2a91-6f5f-4aaa-a018-d3089702bf36
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1df33d0e1aadec9d7ed5aebf743e2c2f840e51fd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568360"
---
# <a name="jscreatetypedarray-function"></a>JsCreateTypedArray-Funktion
Erstellt ein typisiertes JavaScript-Arrayobjekt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
STDAPI_(JsErrorCode) JsCreateTypedArray(  
   _In_ JsTypedArrayType arrayType,  
   _In_ JsValueRef baseArray,  
   _In_ unsigned int byteOffset,  
   _In_ unsigned int elementLength,  
   _Out_ JsValueRef *result  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `arrayType`  
 Der Typ des zu erstellenden Arrays.  
  
 `baseArray`  
 Das Basisarray des neuen Arrays. Verwenden Sie `JS_INVALID_REFERENCE`, falls kein Basisarray.  
  
 `byteOffset`  
 Der Offset in Bytes vom Anfang des `baseArray` (`ArrayBuffer`) für das typisierte Ergebnisarray, auf das verwiesen wird. Gilt nur, wenn `baseArray` ein `ArrayBuffer`-Objekt ist. Muss andernfalls 0 sein.  
  
 `elementLength`  
 Die Anzahl der Elemente im Array. Gilt nur beim Erstellen eines neuen typisierten Arrays ohne `baseArray` (`baseArray` ist `JS_INVALID_REFERENCE`) oder wenn `baseArray` ein `ArrayBuffer`-Objekt ist. Muss andernfalls 0 sein.  
  
 `result`  
 Das neue typisierte Arrayobjekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Der Code `JsNoError` , wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## <a name="remarks"></a>Hinweise  
 Das `baseArray` kann ein `ArrayBuffer`, ein anderes typisiertes Array oder ein JavaScript-`Array` sein. Das zurückgegebene typisierte Array verwendet das `baseArray`, wenn es sich um ein `ArrayBuffer` handelt, oder erstellt und verwendet andernfalls eine Kopie des zugrunde liegenden Quellarrays.  
  
 Erfordert einen Active Script-Kontext.  
  
 Diese API wird nur im Edge-Modus unterstützt.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** jsrt.h  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz (JavaScript-Laufzeit)](../chakra-hosting/reference-javascript-runtime.md)