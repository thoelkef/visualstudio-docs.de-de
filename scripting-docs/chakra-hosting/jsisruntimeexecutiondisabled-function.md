---
title: "JsIsRuntimeExecutionDisabled-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsIsRuntimeExecutionDisabled"
helpviewer_keywords: 
  - "JsIsRuntimeExecutionDisabled-Funktion"
ms.assetid: 77490280-fb84-4614-a1f0-6ac31e3bd607
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# JsIsRuntimeExecutionDisabled-Funktion
Gibt einen Wert zurück, der angibt, ob die Skriptausführung in der Laufzeit deaktiviert ist.  
  
## Syntax  
  
```vb  
STDAPI_(JsErrorCode) JsIsRuntimeExecutionDisabled(  
    _In_ JsRuntimeHandle runtime,  
    _Out_ bool *isDisabled  
);  
```  
  
#### Parameter  
 `runtime`  
 Gibt die Laufzeit an, um zu überprüfen, ob die Ausführung deaktiviert ist.  
  
 `isDisabled`  
 `true`, wenn die Ausführung deaktiviert ist, andernfalls `false`.  
  
## Rückgabewert  
 `JsNoError`, wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)