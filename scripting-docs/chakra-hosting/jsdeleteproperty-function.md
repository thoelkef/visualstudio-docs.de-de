---
title: "JsDeleteProperty-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsDeleteProperty"
helpviewer_keywords: 
  - "JsDeleteProperty-Funktion"
ms.assetid: 0f6ac6a7-3576-42f5-98d0-1c06542c8149
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsDeleteProperty-Funktion
Löscht die Eigenschaft eines Objekts.  
  
## Syntax  
  
```  
STDAPI_(JsErrorCode) JsDeleteProperty(  
   _In_ JsValueRef object,  
   _In_ JsPropertyIdRef propertyId,  
   _In_ bool useStrictRules,  
   _Out_ JsValueRef *result  
);  
```  
  
#### Parameter  
 `object`  
 Das Objekt, das die Eigenschaft enthält.  
  
 `propertyId`  
 Die ID der Eigenschaft.  
  
 `useStrictRules`  
 Der festgelegte Eigenschaft sollte Strict\-Modus\-Regeln folgen.  
  
 `result`  
 Ob die Eigenschaft gelöscht wurde.  
  
## Rückgabewert  
 Der Code `JsNoError`, wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## Hinweise  
 Erfordert einen Active Script\-Kontext.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)