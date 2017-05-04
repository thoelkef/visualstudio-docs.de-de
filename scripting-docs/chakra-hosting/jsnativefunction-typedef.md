---
title: "JsNativeFunction-TypeDef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 56ef6cdf-4ca9-4f7c-b953-e661addb1a8e
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# JsNativeFunction-TypeDef
Ein Funktionsrückruf.  
  
## Syntax  
  
```  
typedef _Ret_maybenull_ JsValueRef (CALLBACK * JsNativeFunction)(  
   _In_ JsValueRef callee,  
   _In_ bool isConstructCall,  
   _In_ JsValueRef *arguments,  
   _In_ unsigned short argumentCount  
);  
```  
  
#### Parameter  
 Aufgerufener  
 Ein `Function`\-Objekt, das die aufgerufene Funktion darstellt.  
  
 isConstructCall  
 Gibt an, ob dies ein regulärer Aufruf oder ein "neuer" Aufruf ist.  
  
 arguments  
 Die Argumente für den Aufruf.  
  
 argumentCount  
 Die Anzahl der Argumente.  
  
## Eigenschaftswert\/Rückgabewert  
 Das Ergebnis des Aufrufs, falls vorhanden.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)