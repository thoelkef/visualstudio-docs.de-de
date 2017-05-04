---
title: "JsObjectBeforeCollectCallback-Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: f21a064a-579f-44cb-9d21-76b62e8c18f5
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# JsObjectBeforeCollectCallback-Typedef
Ein vor der Auflistung eines Objekts aufgerufener Rückruf.  
  
## Syntax  
  
```  
typedef void (CALLBACK *JsObjectBeforeCollectCallback)(  
  _In_ JsRef ref,  
  _In_opt_ void *callbackState  
);  
```  
  
#### Parameter  
 `ref`  
 Das aufzulistende Objekt.  
  
 `callbackState`  
 Der an `JsSetObjectBeforeCollectCallback` übergebene Zustand.  
  
## Hinweise  
 Diese API wird nur im Edge\-Modus unterstützt.  
  
## Anforderungen  
 jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)