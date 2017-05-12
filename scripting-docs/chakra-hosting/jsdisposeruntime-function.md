---
title: "JsDisposeRuntime-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsDisposeRuntime"
helpviewer_keywords: 
  - "JsDisposeRuntime-Funktion"
ms.assetid: 0aefde3f-7250-48be-afc5-53ea85c12f30
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsDisposeRuntime-Funktion
Verwirft eine Laufzeit.  
  
## Syntax  
  
```  
STDAPI_(JsErrorCode) JsDisposeRuntime(  
   _In_ JsRuntimeHandle runtime  
);  
```  
  
#### Parameter  
 `runtime`  
 Die zu verwerfende Laufzeit.  
  
## Rückgabewert  
 Der Code `JsNoError`, wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## Hinweise  
 Sobald eine Laufzeit verworfen wurde, sind alle Ressourcen in ihrem Besitz ungültig und können nicht verwendet werden.  Wenn die Laufzeit aktiv ist \(d. h.  für einen bestimmten Thread als aktuell festgelegt ist\), kann sie nicht verworfen werden.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)