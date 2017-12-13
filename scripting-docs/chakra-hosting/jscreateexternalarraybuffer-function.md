---
title: JsCreateExternalArrayBuffer-Funktion | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a02aaec-0f67-4bf9-b37c-71cdb1410ca4
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 95459f9a9ff676f47d56ed584ad44a30f24fd4cb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="jscreateexternalarraybuffer-function"></a>JsCreateExternalArrayBuffer-Funktion
Erstellt ein Javascript `ArrayBuffer` -Objekt, um auf externen Speicher zuzugreifen.  
  
## <a name="syntax"></a>Syntax  
  
```  
STDAPI_(JsErrorCode) JsCreateExternalArrayBuffer(  
  _Pre_maybenull_ _Pre_writable_byte_size_(byteLength) void *data,  
  _In_ unsigned int byteLength,  
  _In_opt_ JsFinalizeCallback finalizeCallback,  
  _In_opt_ void *callbackState,  
  _Out_ JsValueRef *result  
);  
  
```  
  
#### <a name="parameters"></a>Parameter  
 `data`  
 Ein Zeiger auf den externen Speicher.  
  
 `byteLength`  
 Die Anzahl von Bytes im externen Speicher.  
  
 `finalizeCallback`  
 Ein Rückruf, der erfolgt, wenn das Objekt abgeschlossen ist. Ist möglicherweise NULL.  
  
 `callbackState`  
 Vom Benutzer angegebener Zustand, der wieder an „finalizeCallback“ übergeben wird.  
  
 `result`  
 Das neue `ArrayBuffer` -Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Der Code `JsNoError` , wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## <a name="remarks"></a>Hinweise  
 Erfordert einen Active Script-Kontext.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** jsrt.h  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz (JavaScript-Laufzeit)](../chakra-hosting/reference-javascript-runtime.md)