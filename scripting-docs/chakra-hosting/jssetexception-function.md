---
title: JsSetException-Funktion | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsSetException
helpviewer_keywords: JsSetException function
ms.assetid: c528793a-2e1b-4ee1-bd2e-e63fd547dc40
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5d8fce71f14dedea02e1809fb72281f575f60604
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="jssetexception-function"></a>JsSetException-Funktion
Versetzt die Laufzeit des aktuellen Kontexts in einen Ausnahmezustand.  
  
## <a name="syntax"></a>Syntax  
  
```  
STDAPI_(JsErrorCode) JsSetException(  
   _In_ JsValueRef exception  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `exception`  
 Die für die Laufzeit des aktuellen Kontexts festzulegende JavaScript-Ausnahme.  
  
## <a name="return-value"></a>Rückgabewert  
 `JsNoError`, wenn die Engine in einen Ausnahmezustand versetzt wurde, andernfalls ein Fehlercode.  
  
## <a name="remarks"></a>Hinweise  
 Wenn die Laufzeit des aktuellen Kontexts bereits einen Ausnahmezustand aufweist, gibt diese API `JsErrorInExceptionState` zurück.  
  
 Erfordert einen Active Script-Kontext.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** jsrt.h  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz (JavaScript-Laufzeit)](../chakra-hosting/reference-javascript-runtime.md)