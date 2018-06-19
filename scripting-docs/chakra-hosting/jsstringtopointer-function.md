---
title: JsStringToPointer-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsStringToPointer
helpviewer_keywords:
- JsStringToPointer function
ms.assetid: c7aa7a09-489d-4435-8f8a-aeb62f8875ae
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ff84f929833941fed9a709497dc615189c39386
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569030"
---
# <a name="jsstringtopointer-function"></a>JsStringToPointer-Funktion
Ruft den Zeichenfolgenzeiger für einen Zeichenfolgenwert ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
STDAPI_(JsErrorCode) JsStringToPointer(  
   _In_ JsValueRef value,  
   _Outptr_result_buffer_(*stringLength) const wchar_t **stringValue,  
   _Out_ size_t *stringLength  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `value`  
 Der Zeichenfolgenwert, der in einen Zeichenfolgenzeiger konvertiert werden soll.  
  
 `stringValue`  
 Der Zeichenfolgenzeiger.  
  
 `stringLength`  
 Die Länge der Zeichenfolge.  
  
## <a name="return-value"></a>Rückgabewert  
 Der Code `JsNoError` , wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion ruft den Zeichenfolgenzeiger für einen Zeichenfolgenwert ab. Sie schlägt mit `JsErrorInvalidArgument` fehl, wenn der Typ des Werts nicht "Zeichenfolge" ist. Die Lebensdauer der zurückgegebenen Zeichenfolge entspricht der Lebensdauer des Werts, aus dem sie stammt. Der Zeichenfolgenzeiger wird jedoch nicht als Verweis auf den Wert angesehen (und verhindert daher nicht ihre Erfassung).  
  
 Erfordert einen Active Script-Kontext.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** jsrt.h  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz (JavaScript-Laufzeit)](../chakra-hosting/reference-javascript-runtime.md)