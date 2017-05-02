---
title: "JsSetException-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsSetException"
helpviewer_keywords: 
  - "JsSetException-Funktion"
ms.assetid: c528793a-2e1b-4ee1-bd2e-e63fd547dc40
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsSetException-Funktion
Versetzt die Laufzeit des aktuellen Kontexts in einen Ausnahmezustand.  
  
## Syntax  
  
```  
STDAPI_(JsErrorCode) JsSetException(  
   _In_ JsValueRef exception  
);  
```  
  
#### Parameter  
 `exception`  
 Die für die Laufzeit des aktuellen Kontexts festzulegende JavaScript\-Ausnahme.  
  
## Rückgabewert  
 `JsNoError`, wenn die Engine in einen Ausnahmezustand versetzt wurde, andernfalls ein Fehlercode.  
  
## Hinweise  
 Wenn die Laufzeit des aktuellen Kontexts bereits einen Ausnahmezustand aufweist, gibt diese API `JsErrorInExceptionState` zurück.  
  
 Erfordert einen Active Script\-Kontext.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)