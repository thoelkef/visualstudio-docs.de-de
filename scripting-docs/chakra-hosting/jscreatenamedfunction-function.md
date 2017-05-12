---
title: "JsCreateNamedFunction-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 72f40d06-ab82-4fed-a632-68af6b4126c2
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# JsCreateNamedFunction-Funktion
Erstellt eine neue JavaScript\-Funktion mit einem Namen.  
  
## Syntax  
  
```cpp  
STDAPI_(JsErrorCode) JsCreateNamedFunction(  
   _In_ JsValueRef name,  
   _In_ JsNativeFunction nativeFunction,  
   _In_opt_ void *callbackState,  
   _Out_ JsValueRef *function  
);  
```  
  
#### Parameter  
 `name`  
 Der Name dieser Funktion, die für die Diagnose und Stringificationzwecke verwendet wird.  
  
 `nativeFunction`  
 Die Methode, die bei einem Aufruf der Funktion aufgerufen wird.  
  
 `callbackState`  
 Vom Benutzer angegebener Zustand, der wieder an den Rückruf übergeben wird.  
  
 `function`  
 Das neue Funktionsobjekt.  
  
## Rückgabewert  
  
## Hinweise  
 Erfordert einen Active Script\-Kontext.  
  
 Diese API wird nur im Edge\-Modus unterstützt.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)