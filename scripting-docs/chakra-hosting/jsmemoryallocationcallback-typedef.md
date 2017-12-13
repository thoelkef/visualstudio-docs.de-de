---
title: JsMemoryAllocationCallback-TypeDef | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 511babc7-3caa-4ee5-82a2-943bbd34db8d
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9672c23f48a2cb3e20de58012b267b30f4514d66
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="jsmemoryallocationcallback-typedef"></a>JsMemoryAllocationCallback-TypeDef
Vom Benutzer implementierte Rückrufroutine für Speicherbelegungsereignisse.  
  
## <a name="syntax"></a>Syntax  
  
```  
typedef bool (CALLBACK * JsMemoryAllocationCallback)(  
   _In_opt_ void *callbackState,  
   _In_ JsMemoryEventType allocationEvent,  
   _In_ size_t allocationSize  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 callbackState  
 Der an JsSetRuntimeMemoryAllocationCallback übergebene Zustand.  
  
 allocationEvent  
 Der Typ des Typbelegungsereignisses.  
  
 allocationSize  
 Die Größe der Speicherbelegung.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Wenn für das JsMemoryAllocate-Ereignis "true" zurückgegeben wird, kann die Laufzeit mit der Speicherbelegung fortfahren. Die Rückgabe von "false" bedeutet, dass die Speicherbelegungsanforderung abgelehnt wird. Der Rückgabewert wird für andere Speicherbelegungsereignisse ignoriert.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden Sie JsSetRuntimeMemoryAllocationCallback zum Registrieren dieses Rückrufs.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** jsrt.h  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz (JavaScript-Laufzeit)](../chakra-hosting/reference-javascript-runtime.md)