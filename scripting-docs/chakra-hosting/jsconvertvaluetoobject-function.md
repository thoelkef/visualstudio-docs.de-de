---
title: JsConvertValueToObject-Funktion | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsConvertValueToObject
helpviewer_keywords:
- JsConvertValueToObject function
ms.assetid: 6528b28a-1d2b-417f-bf78-bf05547c52e1
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c93a9f16f76553468839be6c745c3ebc13979f5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="jsconvertvaluetoobject-function"></a>JsConvertValueToObject-Funktion
Konvertiert den Wert mit standardmäßigen JavaScript-Semantiken in ein Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
STDAPI_(JsErrorCode) JsConvertValueToObject(  
   _In_ JsValueRef value,  
   _Out_ JsValueRef *object  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `value`  
 Der zu konvertierende Wert.  
  
 `object`  
 Der konvertierte Wert.  
  
## <a name="return-value"></a>Rückgabewert  
 Der Code `JsNoError` , wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## <a name="remarks"></a>Hinweise  
 Erfordert einen Active Script-Kontext.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** jsrt.h  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz (JavaScript-Laufzeit)](../chakra-hosting/reference-javascript-runtime.md)