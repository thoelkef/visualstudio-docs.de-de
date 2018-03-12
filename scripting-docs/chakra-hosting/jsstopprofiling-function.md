---
title: JsStopProfiling-Funktion | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsStopProfiling
helpviewer_keywords:
- JsStopProfiling function
ms.assetid: 3639c04f-a0f9-418b-be39-92f64b4e7ef8
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0bed003e848a7ac34100a322275be04213da76e7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="jsstopprofiling-function"></a>JsStopProfiling-Funktion
Beendet die Profilerstellung im aktuellen Kontext.  
  
## <a name="syntax"></a>Syntax  
  
```  
STDAPI_(JsErrorCode) JsStopProfiling(  
   _In_ HRESULT reason  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `reason`  
 Der Grund für das Beenden der Profilerstellung, der an den Profilerrückruf übergeben werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Der Code `JsNoError` , wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## <a name="remarks"></a>Hinweise  
 Gibt keinen Fehler zurück, wenn die Profilerstellung noch nicht gestartet wurde.  
  
 Erfordert einen Active Script-Kontext.  
  
 Diese API wird in Desktop-Apps unterstützt, aber nicht in Store-Apps.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** jsrt.h  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz (JavaScript-Laufzeit)](../chakra-hosting/reference-javascript-runtime.md)