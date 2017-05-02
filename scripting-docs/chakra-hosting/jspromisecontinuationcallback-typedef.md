---
title: "JsPromiseContinuationCallback-Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 51a3fd02-9668-4cf7-bb0b-e1fd03b2528f
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# JsPromiseContinuationCallback-Typedef
Ein Zusagefortsetzungsrückruf.  
  
## Syntax  
  
```  
typedef void (CALLBACK *JsPromiseContinuationCallback)(  
  _In_ JsValueRef task,  
  _In_opt_ void *callbackState  
);  
```  
  
#### Parameter  
 `task`  
  `callbackState`  
  
## Hinweise  
 Der Host kann einen Zusagefortsetzungsrückruf in `JsSetPromiseContinuationCallback` angeben. Wenn ein Skript eine Aufgabe erstellt, die zu einem späteren Zeitpunkt ausgeführt wird, wird der Zusagefortsetzungsrückruf mit der Aufgabe aufgerufen, und die Aufgabe sollte in eine FIFO\-Warteschlange verschoben und ausgeführt werden, wenn die Ausführung des aktuellen Skripts abgeschlossen ist.  
  
 Diese API wird nur im Edge\-Modus unterstützt.  
  
## Anforderungen  
 jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)