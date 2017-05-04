---
title: "JsRef-TypeDef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 6aafc39f-6b9c-457f-8bf0-48831bffe9b8
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# JsRef-TypeDef
Ein Verweis auf ein Objekt, dessen Besitzer der Chakra\-Garbage\-Collector ist.  
  
## Syntax  
  
```  
typedef void *JsRef;  
```  
  
## Hinweise  
 Eine Chakra\-Laufzeit überwacht automatisch JsRef\-Verweise, sofern sie in lokalen Variablen oder in Parametern gespeichert sind \(d. h.  im Stapel\).  Das Speichern eines JsRef an einem anderen Ort als im Stapel erfordert das Aufrufen von JsAddRef und JsRelease, um die Lebensdauer des Objekts zu verwalten; andernfalls kann der Garbage Collector das Objekt freigeben, während es noch verwendet wird.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)