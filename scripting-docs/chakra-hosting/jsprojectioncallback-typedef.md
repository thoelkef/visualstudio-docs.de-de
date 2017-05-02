---
title: "JsProjectionCallback Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 32f22d37-e57e-4196-b6cd-a3fc75bd0632
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# JsProjectionCallback Typedef
Der aufzurufende JsRT\-Rückruf mit an `JsProjectionEnqueueCallback` übergebenem Kontext im richtigen Thread.  
  
## Syntax  
  
```  
typedef void (CALLBACK *JsProjectionCallback)(  
  _In_ JsProjectionCallbackContext jsContext  
);  
```  
  
#### Parameter  
 `jsContext`  
 Erfordert das Aufrufen von `JsSetProjectionEnqueueCallback`, um Rückrufe zu empfangen.  
  
## Hinweise  
 Diese API wird nur im Edge\-Modus unterstützt.  
  
## Anforderungen  
 jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)