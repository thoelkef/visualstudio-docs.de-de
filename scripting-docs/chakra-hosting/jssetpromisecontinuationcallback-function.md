---
title: "JsSetPromiseContinuationCallback-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 6ef0faf4-1500-4bd9-aeca-c208492af8ea
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# JsSetPromiseContinuationCallback-Funktion
Legt eine Zusagefortsetzungsrückruf\-Funktion fest, die vom Kontext aufgerufen wird, wenn ein Task für eine spätere Ausführung in die Warteschlange gestellt werden muss.  
  
## Syntax  
  
```  
STDAPI_(JsErrorCode) JsSetPromiseContinuationCallback(  
   _In_ JsPromiseContinuationCallback promiseContinuationCallback,  
   _In_opt_ void *callbackState  
);  
```  
  
#### Parameter  
 `promiseContinuationCallback`  
 Die Rückruffunktion, die festgelegt wird.  
  
 `callbackState`  
 Vom Benutzer angegebener Zustand, der wieder an den Rückruf übergeben wird.  
  
## Rückgabewert  
 Der Code `JsNoError`, wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## Hinweise  
 Erfordert einen Active Script\-Kontext.  
  
 Diese API wird nur im Edge\-Modus unterstützt.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)