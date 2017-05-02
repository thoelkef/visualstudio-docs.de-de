---
title: "JsIsEnumeratingHeap-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsIsEnumeratingHeap"
helpviewer_keywords: 
  - "JsIsEnumeratingHeap-Funktion"
ms.assetid: 5d14518e-3153-43f2-9a9c-068580cbd54f
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsIsEnumeratingHeap-Funktion
Gibt einen Wert zurück, der angibt, ob der Heap des aktuellen Kontexts aufgelistet wird.  
  
## Syntax  
  
```  
STDAPI_(JsErrorCode) JsIsEnumeratingHeap(  
   _Out_ bool *isEnumeratingHeap  
);  
```  
  
#### Parameter  
 `isEnumeratingHeap`  
 Gibt an, ob der Heap aufgelistet wird.  
  
## Rückgabewert  
 Der Code `JsNoError`, wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## Hinweise  
 Erfordert einen Active Script\-Kontext.  
  
 Diese API wird in Desktop\-Apps unterstützt, aber nicht in Store\-Apps.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)