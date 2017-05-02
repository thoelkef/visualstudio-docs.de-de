---
title: "JsCreateFunction-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsCreateFunction"
helpviewer_keywords: 
  - "JsCreateFunction-Funktion"
ms.assetid: b298a96a-5ef7-4203-a8c8-55f9bfc6d2bb
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# JsCreateFunction-Funktion
Erstellt eine neue JavaScript\-Funktion.  
  
## Syntax  
  
```  
STDAPI_(JsErrorCode) JsCreateFunction(  
   _In_ JsNativeFunction nativeFunction,  
   _In_opt_ void *callbackState,  
   _Out_ JsValueRef *function  
);  
```  
  
#### Parameter  
 `nativeFunction`  
 Die Methode, die bei einem Aufruf der Funktion aufgerufen wird.  
  
 `callbackState`  
 Vom Benutzer angegebener Zustand, der wieder an den Rückruf übergeben wird.  
  
 `function`  
 Das neue Funktionsobjekt.  
  
## Rückgabewert  
 Das Ergebnis des Aufrufs, falls vorhanden.  
  
## Hinweise  
 Erfordert einen Active Script\-Kontext.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)