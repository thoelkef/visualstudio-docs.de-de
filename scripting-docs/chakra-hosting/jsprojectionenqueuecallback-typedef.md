---
title: "JsProjectionEnqueueCallback Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 19c1cefb-a7be-4196-b780-9fe6adf35ba5
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# JsProjectionEnqueueCallback Typedef
Der Rückruf der Anwendung, der von JsRT aufgerufen wird, wenn eine projizierte API in einem anderen als dem ursprünglichen Thread abgeschlossen wird.  
  
## Syntax  
  
```  
typedef void (CALLBACK *JsProjectionEnqueueCallback)(  
  _In_ JsProjectionCallback jsCallback,  
  _In_ JsProjectionCallbackContext jsContext,  
  _In_opt_ void *callbackState  
);  
```  
  
#### Parameter  
 `jsCallback`  
 Der Rückruf, der für den ursprünglichen Thread aufgerufen wird.  
  
 `jsContext`  
 Der Anwendungskontext.  
  
 `callbackState`  
 Der JsRT\-Kontext, der an `jsCallback` übergeben werden muss.  
  
## Hinweise  
 Erfordert den Aufruf von JsSetProjectionEnqueueCallback, um Rückrufe empfangen zu können.  
  
 Diese API wird nur im Edge\-Modus unterstützt.  
  
## Anforderungen  
 jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)