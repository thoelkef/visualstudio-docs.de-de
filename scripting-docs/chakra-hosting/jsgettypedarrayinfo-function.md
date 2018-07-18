---
title: JsGetTypedArrayInfo-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 992bc4e9-3d06-4ad2-8b6b-88a437360f81
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 44897f3960b09a110c1f1dd288f08bd5b9edc7ed
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568170"
---
# <a name="jsgettypedarrayinfo-function"></a>JsGetTypedArrayInfo-Funktion
Ruft häufig verwendete Eigenschaften eines typisierten Arrays ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
STDAPI_(JsErrorCode) JsGetTypedArrayInfo(  
  _In_ JsValueRef typedArray,  
  _Out_opt_ JsTypedArrayType *arrayType,  
  _Out_opt_ JsValueRef *arrayBuffer,  
  _Out_opt_ unsigned int *byteOffset,  
  _Out_opt_ unsigned int *byteLength  
);  
  
```  
  
#### <a name="parameters"></a>Parameter  
 `typedArray`  
 Die Instanz des typisierten Arrays.  
  
 `arrayType`  
 Der Typ des Arrays.  
  
 `arrayBuffer`  
 Der `ArrayBuffer` -Speicherbereich des Arrays.  
  
 `byteOffset`  
 Der Offset in Bytes ab dem Anfang des Arraypuffers (arrayBuffer), auf den das Array verweist.  
  
 `byteLength`  
 Die Anzahl der Bytes im Array.  
  
## <a name="return-value"></a>Rückgabewert  
 Der Code `JsNoError` , wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## <a name="remarks"></a>Hinweise  
 Erfordert einen Active Script-Kontext.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** jsrt.h  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz (JavaScript-Laufzeit)](../chakra-hosting/reference-javascript-runtime.md)