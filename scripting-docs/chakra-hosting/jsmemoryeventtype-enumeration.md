---
title: "JsMemoryEventType-Enumeration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsMemoryEventType"
helpviewer_keywords: 
  - "JsMemoryEventType-Enumeration"
ms.assetid: b4b176b6-b536-472e-8999-95b681a1df55
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsMemoryEventType-Enumeration
Speicherbelegungsrückruf\-Ereignistyp.  
  
## Syntax  
  
```  
enum JsMemoryEventType;  
```  
  
## Mitglieder  
  
### Werte  
  
|Name|Beschreibung|  
|----------|------------------|  
|`JsMemoryAllocate`|Gibt eine Anforderung für die Speicherbelegung an.|  
|`JsMemoryFailure`|Gibt ein fehlgeschlagenes Speicherbelegungsereignis an.|  
|`JsMemoryFree`|Gibt ein Ereignis an, durch das Speicher freigegeben wird.|  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)