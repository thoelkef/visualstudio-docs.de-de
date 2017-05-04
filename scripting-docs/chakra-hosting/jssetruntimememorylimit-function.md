---
title: "JsSetRuntimeMemoryLimit-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsSetRuntimeMemoryLimit"
helpviewer_keywords: 
  - "JsSetRuntimeMemoryLimit-Funktion"
ms.assetid: 74feb31f-19f6-43e3-b117-0694c59ac593
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsSetRuntimeMemoryLimit-Funktion
Legt das aktuelle Arbeitsspeicherlimit für eine Laufzeit fest.  
  
## Syntax  
  
```  
STDAPI_(JsErrorCode) JsSetRuntimeMemoryLimit(  
   _In_ JsRuntimeHandle runtime,  
   _In_ size_t memoryLimit  
);  
```  
  
#### Parameter  
 `runtime`  
 Die Laufzeit, deren Arbeitsspeicherlimit festgelegt werden soll.  
  
 `memoryLimit`  
 Das neue Laufzeit\-Arbeitsspeicherlimit in Bytes oder –1 für kein Arbeitsspeicherlimit.  
  
## Rückgabewert  
 Der Code `JsNoError`, wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## Hinweise  
 Ein Arbeitsspeicherlimit führt dazu, dass jeder Vorgang, der das Limit überschreitet, mit einem Fehler aufgrund von ungenügendem Arbeitsspeicher fehlschlägt.  Das Festlegen des Arbeitsspeicherlimits einer Laufzeit auf –1 bedeutet, dass die Laufzeit kein Arbeitsspeicherlimit aufweist.  Neue Laufzeiten weisen standardmäßig keine Arbeitsspeicherlimits auf.  Wenn das neue Arbeitsspeicherlimit über der aktuellen Auslastung liegt, wird der Aufruf erfolgreich ausgeführt, und alle zukünftigen Speicherbelegungen in dieser Laufzeit schlagen fehl, bis die Speicherauslastung der Laufzeit wieder unter dem Limit liegt.  
  
 Das Arbeitsspeicherlimit einer Laufzeit kann immer festgelegt werden, unabhängig davon, ob die Laufzeit in einem anderen Thread aktiv ist.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)