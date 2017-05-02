---
title: "JsBackgroundWorkItemCallback-TypeDef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: e6db52e1-830c-46a2-b9f9-cc2d450a1da8
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# JsBackgroundWorkItemCallback-TypeDef
Ein Hintergrundaufgabenrückruf.  
  
## Syntax  
  
```  
typedef void (CALLBACK *JsBackgroundWorkItemCallback)(  
   _In_opt_ void *callbackData  
);  
```  
  
#### Parameter  
 callbackData  
 Das an den Threaddienst übergebene Datenargument.  
  
## Hinweise  
 Dies wird an den Threaddienst des Hosts übergeben \(wenn vorhanden\), um es dem Host zu ermöglichen, den Arbeitsaufgabenrückruf im Hintergrundthread seiner Wahl aufzurufen.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)