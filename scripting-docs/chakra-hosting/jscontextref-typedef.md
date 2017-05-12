---
title: "JsContextRef-TypeDef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 8586bfcc-bb24-430d-a6f2-1a3b3e34ec2e
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# JsContextRef-TypeDef
Ein Verweis auf einen Skriptkontext.  
  
## Syntax  
  
```  
typedef JsRef JsContextRef;  
```  
  
## Hinweise  
 Jeder Skriptkontext enthält ein eigenes globales Objekt, das sich vom globalen Objekt in anderen Skriptkontexten unterscheidet.  
  
 Viele Chakra\-Hosting\-APIs erfordern einen "aktiven" Skriptkontext, der mit `JsSetCurrentContext` festgelegt werden kann.  Bei Chakra\-Hosting\-APIs, die einen aktuellen Kontext erfordern, wird in der Dokumentation explizit darauf hingewiesen.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)