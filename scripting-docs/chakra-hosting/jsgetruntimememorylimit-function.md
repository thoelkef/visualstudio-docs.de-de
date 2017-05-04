---
title: "JsGetRuntimeMemoryLimit-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsGetRuntimeMemoryLimit"
helpviewer_keywords: 
  - "JsGetRuntimeMemoryLimit-Funktion"
ms.assetid: ed81ca60-99fd-46b0-89ae-f6ac07926904
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsGetRuntimeMemoryLimit-Funktion
Ruft das aktuelle Arbeitsspeicherlimit für eine Laufzeit ab.  
  
## Syntax  
  
```  
STDAPI_(JsErrorCode) JsGetRuntimeMemoryLimit(  
   _In_ JsRuntimeHandle runtime,  
   _Out_ size_t *memoryLimit  
);  
```  
  
#### Parameter  
 `runtime`  
 Die Laufzeit, deren Speicherlimit abgerufen werden soll.  
  
 `memoryLimit`  
 Das aktuelle Arbeitsspeicherlimit der Laufzeit in Byte oder –1, wenn kein Limit festgelegt wurde.  
  
## Rückgabewert  
 Der Code `JsNoError`, wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## Hinweise  
 Das Arbeitsspeicherlimit einer Laufzeit kann immer abgerufen werden, unabhängig davon, ob die Laufzeit in einem anderen Thread aktiv ist.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)