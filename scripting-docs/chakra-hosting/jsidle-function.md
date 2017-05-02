---
title: "JsIdle-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsIdle"
helpviewer_keywords: 
  - "JsIdle-Funktion"
ms.assetid: 372d1c62-8e19-4886-aa33-364cabc09bba
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# JsIdle-Funktion
Weist die Laufzeit an, jegliche notwendige Leerlaufverarbeitung auszuführen.  
  
## Syntax  
  
```  
STDAPI_(JsErrorCode) JsIdle(  
   _Out_opt_ unsigned int *nextIdleTick  
);  
```  
  
#### Parameter  
 `nextIdleTick`  
 Der nächste Systemtick, bei dem mehr Leerlaufaufgaben anfallen.  Kann NULL sein.  Gibt die maximale Anzahl von Ticks zurück, wenn keine Leerlaufaufgaben anstehen.  
  
## Rückgabewert  
 Der Code `JsNoError`, wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## Hinweise  
 Wenn die Leerlaufverarbeitung für die aktuelle Laufzeit aktiviert wurde, wird die aktuelle Laufzeit durch Aufrufen von `JsIdle` informiert, dass der Host im Leerlauf ist und dass die Laufzeit Arbeitsspeicher\-Bereinigungsaufgaben ausführen kann.  
  
 `JsIdle` kann auch die Anzahl von Ticks zurückgeben, nach der wieder mehr Leerlaufaufgaben für die Laufzeit anstehen.  Das Aufrufen von `JsIdle`, bevor diese Anzahl von Ticks verstrichen ist, hat keine Auswirkungen.  
  
 Erfordert einen Active Script\-Kontext.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)