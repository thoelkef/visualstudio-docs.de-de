---
title: "JsStartDebugging-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsStartDebugging"
helpviewer_keywords: 
  - "JsStartDebugging-Funktion"
ms.assetid: c48ba02d-6d47-466f-a970-02f087d525f3
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# JsStartDebugging-Funktion
Startet das Debuggen im aktuellen Kontext.  
  
## Syntax  
  
```  
// Edge mode signature  
STDAPI_(JsErrorCode) JsStartDebugging();  
  
// Legacy mode signature  
STDAPI_(JsErrorCode)  JsStartDebugging(  
   _In_ IDebugApplication *debugApplication  
);  
```  
  
#### Parameter  
 `debugApplication`  
 Die Debuganwendung, die zum Debuggen verwendet werden soll.  
  
## Rückgabewert  
 Der Code `JsNoError`, wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## Hinweise  
 Der Host muss sicherstellen, dass `CoInitializeEx` mindestens einmal mit `COINIT_MULTITHREADED` oder `COINIT_APARTMENTTHREADED` aufgerufen wird, bevor diese API verwendet wird.  
  
 Der `debugApplication`\-Parameter wird im Edgemodus nicht unterstützt.  Weitere Informationen zur Verwendung dieser API im Edgemodus finden Sie unter [Ansteuern des Edgemodus im Vergleich zu Legacy\-Modulen](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md).  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)