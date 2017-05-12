---
title: "JsEnumerateHeap-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsEnumerateHeap"
helpviewer_keywords: 
  - "JsEnumerateHeap-Funktion"
ms.assetid: 3e518e0b-b959-4686-899c-83e6b1946c9d
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsEnumerateHeap-Funktion
Listet den Heap des aktuellen Kontexts auf.  
  
## Syntax  
  
```  
STDAPI_(JsErrorCode) JsEnumerateHeap(  
   _Out_ IActiveScriptProfilerHeapEnum **enumerator  
);  
```  
  
#### Parameter  
 `enumerator`  
 Der Heapenumerator.  
  
## Rückgabewert  
 Der Code `JsNoError`, wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## Hinweise  
 Während der Heap aufgelistet wird, kann der aktuelle Kontext nicht entfernt werden, und alle Aufrufe zum Ändern des Kontextzustands schlagen fehl, bis der Heapenumerator freigegeben wurde.  
  
 Erfordert einen Active Script\-Kontext.  
  
 Diese API wird in Desktop\-Apps unterstützt, aber nicht in Store\-Apps.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)