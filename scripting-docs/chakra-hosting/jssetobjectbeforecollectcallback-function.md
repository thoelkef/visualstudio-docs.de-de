---
title: "JsSetObjectBeforeCollectCallback-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: ea2cbd94-d8b0-4fa9-a4a1-c75a4e338eaf
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# JsSetObjectBeforeCollectCallback-Funktion
Legt eine Rückruffunktion fest, die vor der Garbage Collection eines Objekts von der Laufzeit aufgerufen wird.  
  
## Syntax  
  
```  
STDAPI_(JsErrorCode) JsSetObjectBeforeCollectCallback(  
   _In_ JsRef ref,  
   _In_opt_ void *callbackState,  
   _In_ JsObjectBeforeCollectCallback objectBeforeCollectCallback  
);  
```  
  
#### Parameter  
 `ref`  
 Das Objekt, für das der Rückruf registriert werden soll.  
  
 `callbackState`  
 Vom Benutzer angegebener Zustand, der wieder an den Rückruf übergeben wird.  
  
 `objectBeforeCollectCallback`  
 Die Rückruffunktion, die festgelegt wird.  Verwenden Sie NULL, um zuvor registrierte Rückrufe zu löschen.  
  
## Rückgabewert  
 Der Code `JsNoError`, wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## Hinweise  
 Der Rückruf erfolgt im aktuellen Laufzeitausführungsthread, und daher wird die Ausführung blockiert, bis der Rückruf abgeschlossen ist.  
  
 Diese API wird nur im Edge\-Modus unterstützt.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)