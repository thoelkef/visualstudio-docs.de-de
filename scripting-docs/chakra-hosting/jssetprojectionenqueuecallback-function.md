---
title: "JsSetProjectionEnqueueCallback-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: c751ccef-20d2-4d41-9568-1c54adf47cdf
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# JsSetProjectionEnqueueCallback-Funktion
Legt den Rückruf fest, der verwendet werden soll, um einen Projektionsabschluss zurück im vom Aufrufer benötigten Thread aufzurufen.  
  
## Syntax  
  
```  
STDAPI_(JsErrorCode) JsSetProjectionEnqueueCallback(  
   _In_ JsProjectionEnqueueCallback projectionEnqueueCallback,  
   _In_opt_ void *projectionEnqueueContext);  
  
```  
  
#### Parameter  
 `projectionEnqueueContext`  
 Der Rückruf, der jedes Mal aufgerufen wird, wenn der Abschluss einer Projektion in einem Hintergrundthread auftritt.  
  
 `callbackState`  
 Der Anwendungskontext, der `projectionEnqueueContext` bereitgestellt wird.  
  
## Rückgabewert  
 Der Code `JsNoError`, wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## Hinweise  
 Erfordert einen Active Script\-Kontext.  
  
 Der Aufruf sollte aus einem anderen COM\-Apartment oder einem anderen Thread in derselben MTA stammen.  
  
 Diese API wird nur im Edge\-Modus unterstützt.  
  
> [!CAUTION]
>  PInvoke wird derzeit für diese API nicht unterstützt.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)