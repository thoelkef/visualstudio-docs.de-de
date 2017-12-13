---
title: JsGetRuntimeMemoryLimit-Funktion | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsGetRuntimeMemoryLimit
helpviewer_keywords: JsGetRuntimeMemoryLimit function
ms.assetid: ed81ca60-99fd-46b0-89ae-f6ac07926904
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6373e166ff4efe6bc8c5a33d203d60647c4be9b7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="jsgetruntimememorylimit-function"></a>JsGetRuntimeMemoryLimit-Funktion
Ruft das aktuelle Arbeitsspeicherlimit für eine Laufzeit ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
STDAPI_(JsErrorCode) JsGetRuntimeMemoryLimit(  
   _In_ JsRuntimeHandle runtime,  
   _Out_ size_t *memoryLimit  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `runtime`  
 Die Laufzeit, deren Speicherlimit abgerufen werden soll.  
  
 `memoryLimit`  
 Das aktuelle Arbeitsspeicherlimit der Laufzeit in Byte oder –1, wenn kein Limit festgelegt wurde.  
  
## <a name="return-value"></a>Rückgabewert  
 Der Code `JsNoError` , wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## <a name="remarks"></a>Hinweise  
 Das Arbeitsspeicherlimit einer Laufzeit kann immer abgerufen werden, unabhängig davon, ob die Laufzeit in einem anderen Thread aktiv ist.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** jsrt.h  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz (JavaScript-Laufzeit)](../chakra-hosting/reference-javascript-runtime.md)