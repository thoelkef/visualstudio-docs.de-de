---
title: JsHasException-Funktion | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsHasException
helpviewer_keywords:
- JsHasException function
ms.assetid: ac7da3ce-c746-4154-bbb8-bcb0859a8d5b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 32334f4b8787bebaffb9553fcdd40f85334462cb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="jshasexception-function"></a>JsHasException-Funktion
Bestimmt, ob sich die Laufzeit des aktuellen Kontexts in einem Ausnahmezustand befindet.  
  
## <a name="syntax"></a>Syntax  
  
```  
STDAPI_(JsErrorCode) JsHasException(  
   _Out_ bool *hasException  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `hasException`  
 Gibt an, ob sich die Laufzeit des aktuellen Kontexts im Ausnahmezustand befindet.  
  
## <a name="return-value"></a>Rückgabewert  
 Der Code `JsNoError` , wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein Aufruf in die Laufzeit eine Ausnahme zurückgibt (z. B. wegen eines ausgeführten Skripts oder wegen eines Konvertierungsfehlers), wird die Laufzeit in einen "Ausnahmezustand" versetzt. Alle Aufrufe in einen von der Laufzeit erstellten Kontext (mit Ausnahme der Ausnahme-APIs) schlagen mit `JsErrorInExceptionState` fehl, bis die Ausnahme gelöscht wurde.  
  
 Wenn sich die Laufzeit des aktuellen Kontexts im Ausnahmezustand befindet, wenn ein Rückruf in die Engine zurückgegeben wird, löst die Engine die Ausnahme automatisch erneut aus.  
  
 Erfordert einen Active Script-Kontext.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** jsrt.h  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz (JavaScript-Laufzeit)](../chakra-hosting/reference-javascript-runtime.md)