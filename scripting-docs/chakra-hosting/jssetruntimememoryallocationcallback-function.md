---
title: "JsSetRuntimeMemoryAllocationCallback-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsSetRuntimeMemoryAllocationCallback"
helpviewer_keywords: 
  - "JsSetRuntimeMemoryAllocationCallback-Funktion"
ms.assetid: 6aa7d58d-6456-4df1-815f-1ba36fb4ae14
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsSetRuntimeMemoryAllocationCallback-Funktion
Legt einen Speicherbelegungsrückruf für die angegebene Laufzeit fest.  
  
## Syntax  
  
```  
STDAPI_(JsErrorCode) JsSetRuntimeMemoryAllocationCallback(  
   _In_ JsRuntimeHandle runtime,  
   _In_opt_ void *callbackState,  
   _In_ JsMemoryAllocationCallback allocationCallback  
);  
```  
  
#### Parameter  
 `runtime`  
 Die Laufzeit, für die der Speicherbelegungsrückruf registriert werden soll.  
  
 `callbackState`  
 Vom Benutzer angegebener Zustand, der wieder an den Rückruf übergeben wird.  
  
 `allocationCallback`  
 Speicherbelegungsrückruf, der für Speicherbelegungsereignisse erfolgen soll.  
  
## Rückgabewert  
 Der Code `JsNoError`, wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## Hinweise  
 Das Registrieren eines Speicherbelegungsrückrufs führt dazu, dass die Laufzeit immer dann einen Rückruf an den Host vornimmt, wenn sie Arbeitsspeicher vom Betriebssystem belegt oder freigibt.  Die Rückrufroutine wird aufgerufen, bevor der Laufzeitarbeitsspeicher\-Manager einen Speicherblock belegt.  Die Speicherbelegung wird abgelehnt, wenn der Rückruf "false" zurückgibt.  Der Laufzeitarbeitsspeicher\-Manager löst die Rückrufroutine außerdem aus, nachdem er einen Speicherblock freigegeben hat sowie nach Speicherbelegungsfehlern.  
  
 Der Rückruf erfolgt im aktuellen Laufzeitausführungsthread, und daher wird die Ausführung blockiert, bis der Rückruf abgeschlossen ist.  
  
 Der Rückgabewert des Rückrufs wird nicht gespeichert; zuvor abgelehnte Speicherbelegungen verhindern nicht, dass die Laufzeit den Rückruf später erneut für neue Speicherbelegungen aufruft.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)