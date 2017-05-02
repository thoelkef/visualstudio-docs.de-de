---
title: "JsValueToVariant-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsValueToVariant"
helpviewer_keywords: 
  - "JsValueToVariant-Funktion"
ms.assetid: 070244be-a69d-4b78-971b-69c0579c03cf
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsValueToVariant-Funktion
Initialisiert die übergebene `VARIANT` als Projektion eines JavaScript\-Werts.  
  
## Syntax  
  
```  
STDAPI_(JsErrorCode) JsValueToVariant(  
   _In_ JsValueRef object,  
   _Out_ VARIANT *variant  
);  
```  
  
#### Parameter  
 `object`  
 Ein JavaScript\-Wert, der als `VARIANT` projiziert werden soll.  
  
 `variant`  
 Ein Zeiger auf eine `VARIANT`\-Struktur, die als Projektion initialisiert wird.  
  
## Rückgabewert  
  
## Hinweise  
 Die Projektion `VARIANT` kann von COM\-Automatisierungsclients verwendet werden, um das projizierte JavaScript\-Objekt aufzurufen.  
  
 Erfordert einen Active Script\-Kontext.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)