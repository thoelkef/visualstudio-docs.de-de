---
title: "JsStrictEquals-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsStrictEquals"
helpviewer_keywords: 
  - "JsStrictEquals-Funktion"
ms.assetid: b35bc655-7ff8-496a-b678-8950bb976047
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsStrictEquals-Funktion
Vergleicht zwei JavaScript\-Werte hinsichtlich ihrer exakten Gleichheit.  
  
## Syntax  
  
```  
STDAPI_(JsErrorCode) JsStrictEquals(  
   _In_ JsValueRef object1,  
   _In_ JsValueRef object2,  
   _Out_ bool *result  
);  
```  
  
#### Parameter  
 `object1`  
 Das erste zu vergleichende Objekt.  
  
 `object2`  
 Das zweite zu vergleichende Objekt.  
  
 `result`  
 Gibt an, ob die Werte exakt identisch sind.  
  
## Rückgabewert  
 Der Code `JsNoError`, wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## Hinweise  
 Diese Funktion entspricht dem Operator `===` in JavaScript.  
  
 Erfordert einen Active Script\-Kontext.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)