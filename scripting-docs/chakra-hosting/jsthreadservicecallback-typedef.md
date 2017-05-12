---
title: "JsThreadServiceCallback-TypeDef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: dbe67be5-418a-4f66-8b68-b38078a6d140
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# JsThreadServiceCallback-TypeDef
Ein Threaddienstrückruf.  
  
## Syntax  
  
```  
typedef bool (CALLBACK *JsThreadServiceCallback)(  
   _In_ JsBackgroundWorkItemCallback callback,  
   _In_opt_ void *callbackData  
);  
```  
  
#### Parameter  
 callback  
 Der Rückruf für die Hintergrundaufgabe.  
  
 callbackData  
 Das an den Rückruf übergebene Datenargument.  
  
## Hinweise  
 Der Host kann einen Hintergrundthreaddienst angeben, wenn er "JsCreateRuntime" aufruft.  Sofern angegeben, werden Hintergrundaufgaben mit diesem Rückruf an den Host übergeben.  Der Host soll die Ausführung der Hintergrundaufgaben sofort beginnen und "true" oder "false" zurückgeben, und die Laufzeit verarbeitet die Arbeitsaufgabe im Thread.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)