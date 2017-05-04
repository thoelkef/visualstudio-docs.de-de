---
title: "JsGetAndClearException-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsGetAndClearException"
helpviewer_keywords: 
  - "JsGetAndClearException-Funktion"
ms.assetid: 6aec8a88-41ee-47f6-b5f4-32f3cae6bb7b
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsGetAndClearException-Funktion
Gibt die Ausnahme zurück, durch die die Laufzeit des aktuellen Kontexts in den Ausnahmezustand versetzt wurde, und setzt den Ausnahmezustand für diese Laufzeit zurück.  
  
## Syntax  
  
```  
STDAPI_(JsErrorCode) JsGetAndClearException(  
   _Out_ JsValueRef *exception  
);  
```  
  
#### Parameter  
 `exception`  
 Die Ausnahme für die Laufzeit des aktuellen Kontexts.  
  
## Rückgabewert  
 Der Code `JsNoError`, wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## Hinweise  
 Wenn die Laufzeit des aktuellen Kontexts keinen Ausnahmezustand aufweist, gibt diese API `JsErrorInvalidArgument` zurück.  Wenn die Laufzeit deaktiviert ist, wird eine Ausnahme zurückgegeben, die angibt, dass das Skript beendet wurde. Die Ausnahme wird jedoch nicht gelöscht \(die Ausnahme wird gelöscht, wenn die Laufzeit mit `JsEnableRuntimeExecution` wieder aktiviert wird\).  
  
 Erfordert einen Active Script\-Kontext.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)