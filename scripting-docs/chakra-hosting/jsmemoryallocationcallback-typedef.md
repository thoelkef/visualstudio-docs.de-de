---
title: "JsMemoryAllocationCallback-TypeDef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 511babc7-3caa-4ee5-82a2-943bbd34db8d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# JsMemoryAllocationCallback-TypeDef
Vom Benutzer implementierte Rückrufroutine für Speicherbelegungsereignisse.  
  
## Syntax  
  
```  
typedef bool (CALLBACK * JsMemoryAllocationCallback)(  
   _In_opt_ void *callbackState,  
   _In_ JsMemoryEventType allocationEvent,  
   _In_ size_t allocationSize  
);  
```  
  
#### Parameter  
 callbackState  
 Der an JsSetRuntimeMemoryAllocationCallback übergebene Zustand.  
  
 allocationEvent  
 Der Typ des Typbelegungsereignisses.  
  
 allocationSize  
 Die Größe der Speicherbelegung.  
  
## Eigenschaftswert\/Rückgabewert  
 Wenn für das JsMemoryAllocate\-Ereignis "true" zurückgegeben wird, kann die Laufzeit mit der Speicherbelegung fortfahren.  Die Rückgabe von "false" bedeutet, dass die Speicherbelegungsanforderung abgelehnt wird.  Der Rückgabewert wird für andere Speicherbelegungsereignisse ignoriert.  
  
## Hinweise  
 Verwenden Sie JsSetRuntimeMemoryAllocationCallback zum Registrieren dieses Rückrufs.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)