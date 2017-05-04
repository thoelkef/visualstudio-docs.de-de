---
title: "JsEnableRuntimeExecution-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsEnableRuntimeExecution"
helpviewer_keywords: 
  - "JsEnableRuntimeExecution-Funktion"
ms.assetid: daa2036b-aef6-497d-a8ce-5a006b6ed13f
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsEnableRuntimeExecution-Funktion
Aktiviert die Skriptausführung in einer Laufzeit.  
  
## Syntax  
  
```  
STDAPI_(JsErrorCode) JsEnableRuntimeExecution(  
   _In_ JsRuntimeHandle runtime  
);  
```  
  
#### Parameter  
 `runtime`  
 Die zu aktivierende Laufzeit.  
  
## Rückgabewert  
 Der Code `JsNoError`, wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## Hinweise  
 Das Aktivieren der Skriptausführung in einer Laufzeit, in der die Skriptausführung bereits aktiviert ist, hat keine Auswirkungen.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)