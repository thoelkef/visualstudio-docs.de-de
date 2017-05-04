---
title: "JsRuntimeHandle-TypeDef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 69e59bfd-9b0e-4710-9aa8-fbd6844171bc
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# JsRuntimeHandle-TypeDef
Ein Handle für eine Chakra\-Laufzeit.  
  
## Syntax  
  
```  
typedef void *JsRuntimeHandle;  
```  
  
## Hinweise  
 Jede Chakra\-Laufzeit hat ihre eigene unabhängige Ausführungsengine, ihren eigenen JIT\-Compiler und ihren eigenen Heap mit Garbage Collection.  Daher ist jede Laufzeit vollständig von anderen Laufzeiten isoliert.  
  
 Laufzeiten können in jedem Thread verwendet werden, aber nur ein Thread kann jeweils einen Aufruf an eine Laufzeit vornehmen.  
  
> [!WARNING]
>  Ein JsRuntimeHandle weist im Gegensatz zu anderen Objektverweisen in der Chakra\-Hosting\-API keine Garbage Collection auf, da es den Heap mit Garbage Collection selbst enthält.  Eine Laufzeit ist so lange vorhanden, bis JsDisposeRuntime aufgerufen wird.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)