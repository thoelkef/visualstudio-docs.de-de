---
title: "JsCreateContext-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsCreateContext"
helpviewer_keywords: 
  - "JsCreateContext-Funktion"
ms.assetid: aceca043-2c73-4029-a06c-8ad6695109cf
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# JsCreateContext-Funktion
Erstellt einen Skriptkontext für ausgeführte Skripts.  
  
## Syntax  
  
```  
// Edge mode signature  
STDAPI_(JsErrorCode) JsCreateContext(  
   _In_ JsRuntimeHandle runtime,  
   _Out_ JsContextRef *newContext);  
  
// Legacy mode signature  
STDAPI_(JsErrorCode) JsCreateContext(  
   _In_ JsRuntimeHandle runtime,  
   _In_ IDebugApplication *debugApplication,  
   _Out_ JsContextRef *newContext  
);  
```  
  
#### Parameter  
 `runtime`  
 Die Laufzeit, in der der Skriptkontext erstellt wird.  
  
 `debugApplication`  
 Die Debuganwendung, die zum Debuggen verwendet werden soll.  Dieser Parameter kann NULL sein. In diesem Fall ist das Debuggen nicht für den Kontext aktiviert.  
  
 `newContext`  
 Der erstellte Skriptkontext.  
  
## Rückgabewert  
 Der Code `JsNoError`, wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## Hinweise  
 Jeder Skriptkontext hat ein eigenes globales Objekt, das von allen anderen Skriptkontexten isoliert ist.  
  
 Der `debugApplication`\-Parameter wird im Edgemodus nicht unterstützt.  Weitere Informationen zur Verwendung dieser API im Edgemodus finden Sie unter [Ansteuern des Edgemodus im Vergleich zu Legacy\-Modulen](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md).  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)