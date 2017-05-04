---
title: "JsCreateRuntime-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsCreateRuntime"
helpviewer_keywords: 
  - "JsCreateRuntime-Funktion"
ms.assetid: 92d09b89-6593-4d73-a562-88f9fec10228
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# JsCreateRuntime-Funktion
Erstellt eine neue Laufzeit.  
  
## Syntax  
  
```  
// Edge mode signature  
STDAPI_(JsErrorCode) JsCreateRuntime(  
   _In_ JsRuntimeAttributes attributes,  
   _In_opt_ JsThreadServiceCallback threadService,  
   _Out_ JsRuntimeHandle *runtime);  
  
// Legacy mode signature  
STDAPI_(JsErrorCode) JsCreateRuntime(  
   _In_ JsRuntimeAttributes attributes,  
   _In_ JsRuntimeVersion version,  
   _In_opt_ JsThreadServiceCallback threadService,  
   _Out_ JsRuntimeHandle *runtime  
);  
```  
  
#### Parameter  
 `attributes`  
 Die Attribute der zu erstellenden Laufzeit.  
  
 `version`  
 Die Version der zu erstellenden Laufzeit.  
  
 `threadService`  
 Der Threaddienst für die Laufzeit.  Kann NULL sein.  
  
 `runtime`  
 Die erstellte Laufzeit.  
  
## Rückgabewert  
 Der Code `JsNoError`, wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## Hinweise  
 Der `version`\-Parameter wird im Edgemodus nicht unterstützt.  Weitere Informationen zur Verwendung dieser API im Edgemodus finden Sie unter [Ansteuern des Edgemodus im Vergleich zu Legacy\-Modulen](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md).  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)