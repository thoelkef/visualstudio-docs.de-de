---
title: "JsGetTrueValue-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsGetTrueValue"
helpviewer_keywords: 
  - "JsGetTrueValue-Funktion"
ms.assetid: c2a56d48-344b-492b-90b8-f570710f8310
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsGetTrueValue-Funktion
Ruft den Wert von `true` im aktuellen Skriptkontext ab.  
  
## Syntax  
  
```  
STDAPI_(JsErrorCode) JsGetTrueValue(  
   _Out_ JsValueRef *trueValue  
);  
```  
  
#### Parameter  
 `trueValue`  
 Der `true`\-Wert.  
  
## Rückgabewert  
 Der Code `JsNoError`, wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## Hinweise  
 Erfordert einen Active Script\-Kontext.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)