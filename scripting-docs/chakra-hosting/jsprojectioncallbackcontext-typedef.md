---
title: "JsProjectionCallbackContext Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 50c705c5-664f-4a1a-92f6-4882fc718ab1
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# JsProjectionCallbackContext Typedef
Der von JsRT an den Anwendungsrückruf \(JsProjectionEnqueueCallback\) übergebene Kontext, der anschließend von der Anwendung im korrekten Thread im angegebenen Rückruf \(`JsProjectionCallback`\) zurück an JsRT übergeben wird.  
  
## Syntax  
  
```cpp  
typedef void *JsProjectionCallbackContext;  
```  
  
## Hinweise  
 Erfordert das Aufrufen von `JsSetProjectionEnqueueCallback`, um Rückrufe zu empfangen.  
  
 Diese API wird nur im Edge\-Modus unterstützt.  
  
## Anforderungen  
 jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)