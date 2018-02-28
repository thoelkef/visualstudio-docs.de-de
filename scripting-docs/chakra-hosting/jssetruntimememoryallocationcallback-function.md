---
title: JsSetRuntimeMemoryAllocationCallback-Funktion | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsSetRuntimeMemoryAllocationCallback
helpviewer_keywords:
- JsSetRuntimeMemoryAllocationCallback function
ms.assetid: 6aa7d58d-6456-4df1-815f-1ba36fb4ae14
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 755ab36c8edb8c0350eb2b245e060344c8825dee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="jssetruntimememoryallocationcallback-function"></a>JsSetRuntimeMemoryAllocationCallback-Funktion
Legt einen Speicherbelegungsrückruf für die angegebene Laufzeit fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
STDAPI_(JsErrorCode) JsSetRuntimeMemoryAllocationCallback(  
   _In_ JsRuntimeHandle runtime,  
   _In_opt_ void *callbackState,  
   _In_ JsMemoryAllocationCallback allocationCallback  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `runtime`  
 Die Laufzeit, für die der Speicherbelegungsrückruf registriert werden soll.  
  
 `callbackState`  
 Vom Benutzer angegebener Zustand, der wieder an den Rückruf übergeben wird.  
  
 `allocationCallback`  
 Speicherbelegungsrückruf, der für Speicherbelegungsereignisse erfolgen soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Der Code `JsNoError` , wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## <a name="remarks"></a>Hinweise  
 Das Registrieren eines Speicherbelegungsrückrufs führt dazu, dass die Laufzeit immer dann einen Rückruf an den Host vornimmt, wenn sie Arbeitsspeicher vom Betriebssystem belegt oder freigibt. Die Rückrufroutine wird aufgerufen, bevor der Laufzeitarbeitsspeicher-Manager einen Speicherblock belegt. Die Speicherbelegung wird abgelehnt, wenn der Rückruf "false" zurückgibt. Der Laufzeitarbeitsspeicher-Manager löst die Rückrufroutine außerdem aus, nachdem er einen Speicherblock freigegeben hat sowie nach Speicherbelegungsfehlern.  
  
 Der Rückruf erfolgt im aktuellen Laufzeitausführungsthread, und daher wird die Ausführung blockiert, bis der Rückruf abgeschlossen ist.  
  
 Der Rückgabewert des Rückrufs wird nicht gespeichert; zuvor abgelehnte Speicherbelegungen verhindern nicht, dass die Laufzeit den Rückruf später erneut für neue Speicherbelegungen aufruft.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** jsrt.h  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz (JavaScript-Laufzeit)](../chakra-hosting/reference-javascript-runtime.md)