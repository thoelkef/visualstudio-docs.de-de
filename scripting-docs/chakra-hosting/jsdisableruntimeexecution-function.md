---
title: "JsDisableRuntimeExecution-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsDisableRuntimeExecution"
helpviewer_keywords: 
  - "JsDisableRuntimeExecution-Funktion"
ms.assetid: 4bd4670a-a9da-4f8c-b3fd-1fd366d915c3
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsDisableRuntimeExecution-Funktion
Hält die Skriptausführung an und beendet alle ausgeführten Skripts in einer Laufzeit.  
  
## Syntax  
  
```  
STDAPI_(JsErrorCode) JsDisableRuntimeExecution(  
   _In_ JsRuntimeHandle runtime  
);  
```  
  
#### Parameter  
 `runtime`  
 Die anzuhaltende Laufzeit.  
  
## Rückgabewert  
 Der Code `JsNoError`, wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## Hinweise  
 Aufrufe an eine angehaltene Laufzeit schlagen fehl, bis `JsEnableRuntimeExecution` aufgerufen wird.  
  
 Diese API muss nicht in dem Thread aufgerufen werden, in dem die Laufzeit aktiv ist.  Wenn die Laufzeit in einen angehaltenen Zustand versetzt wird, werden ausgeführte Skripts möglicherweise nicht sofort angehalten. Aktive Skripts wird so schnell wie möglich mit einer "Nicht abfangbar"\-Ausnahme beendet.  
  
 Das Anhalten der Ausführung in einer Laufzeit, die bereits angehalten ist, ist nicht möglich.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)