---
title: JsEquals-Funktion | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsEquals
helpviewer_keywords:
- JsEquals function
ms.assetid: 8377a7b6-12ff-43e4-8cc8-5a5a198a168b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4bb0a40cf74021fbad081745ef27c79a6a4b2b78
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="jsequals-function"></a>JsEquals-Funktion
Vergleicht zwei JavaScript-Werte hinsichtlich ihrer Gleichheit.  
  
## <a name="syntax"></a>Syntax  
  
```  
STDAPI_(JsErrorCode) JsEquals(  
   _In_ JsValueRef object1,  
   _In_ JsValueRef object2,  
   _Out_ bool *result  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `object1`  
 Das erste zu vergleichende Objekt.  
  
 `object2`  
 Das zweite zu vergleichende Objekt.  
  
 `result`  
 Gibt an, ob die Werte gleich sind.  
  
## <a name="return-value"></a>Rückgabewert  
 Der Code `JsNoError` , wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion entspricht dem Operator `==` in JavaScript.  
  
 Erfordert einen Active Script-Kontext.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** jsrt.h  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz (JavaScript-Laufzeit)](../chakra-hosting/reference-javascript-runtime.md)