---
title: "JsGetPropertyIdFromSymbol Function | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 190fe4b9-352e-4b10-9d0e-6c6bbd6363e8
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# JsGetPropertyIdFromSymbol Function
Ruft die dem Symbol zugeordnete Eigenschafts\-ID ab.  
  
## Syntax  
  
```  
STDAPI_(JsErrorCode) JsGetPropertyIdFromSymbol(  
   _In_ JsValueRef symbol,  
   _Out_ JsPropertyIdRef *propertyId  
);  
```  
  
#### Parameter  
 `symbol`  
 Das Symbol, dessen Eigenschafts\-ID abgerufen wird.  
  
 `propertyId`  
 Die Eigenschafts\-ID für das angegebene Symbol.  
  
## Rückgabewert  
 Der Code `JsNoError`, wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## Hinweise  
 Eigenschafts\-IDs sind spezifisch für einen Kontext und können nicht kontextübergreifend verwendet werden.  
  
 Erfordert einen Active Script\-Kontext.  
  
 Diese API wird nur im Edge\-Modus unterstützt.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)