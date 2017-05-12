---
title: "JsStopProfiling-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsStopProfiling"
helpviewer_keywords: 
  - "JsStopProfiling-Funktion"
ms.assetid: 3639c04f-a0f9-418b-be39-92f64b4e7ef8
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# JsStopProfiling-Funktion
Beendet die Profilerstellung im aktuellen Kontext.  
  
## Syntax  
  
```  
STDAPI_(JsErrorCode) JsStopProfiling(  
   _In_ HRESULT reason  
);  
```  
  
#### Parameter  
 `reason`  
 Der Grund für das Beenden der Profilerstellung, der an den Profilerrückruf übergeben werden soll.  
  
## Rückgabewert  
 Der Code `JsNoError`, wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## Hinweise  
 Gibt keinen Fehler zurück, wenn die Profilerstellung noch nicht gestartet wurde.  
  
 Erfordert einen Active Script\-Kontext.  
  
 Diese API wird in Desktop\-Apps unterstützt, aber nicht in Store\-Apps.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)