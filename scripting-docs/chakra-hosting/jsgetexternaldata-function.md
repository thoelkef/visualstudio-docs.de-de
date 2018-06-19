---
title: JsGetExternalData-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsGetExternalData
helpviewer_keywords:
- JsGetExternalData function
ms.assetid: 1919e1da-3ea7-4269-a5fb-a3be06bd029b
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da78672f85159070949d067867699cfb5223b31c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24567990"
---
# <a name="jsgetexternaldata-function"></a>JsGetExternalData-Funktion
Ruft die Daten aus einem externen Objekt ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
STDAPI_(JsErrorCode) JsGetExternalData(  
   _In_ JsValueRef object,  
   _Out_ void **externalData  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `object`  
 Das externe Objekt.  
  
 `externalData`  
 Die externen, im Objekt gespeicherten Daten. Kann NULL sein, wenn keine externen Daten im Objekt gespeichert sind.  
  
## <a name="return-value"></a>Rückgabewert  
 Der Code `JsNoError` , wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## <a name="remarks"></a>Hinweise  
 Erfordert einen Active Script-Kontext.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** jsrt.h  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz (JavaScript-Laufzeit)](../chakra-hosting/reference-javascript-runtime.md)