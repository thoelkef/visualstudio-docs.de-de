---
title: "JsHasException-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsHasException"
helpviewer_keywords: 
  - "JsHasException-Funktion"
ms.assetid: ac7da3ce-c746-4154-bbb8-bcb0859a8d5b
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsHasException-Funktion
Bestimmt, ob sich die Laufzeit des aktuellen Kontexts in einem Ausnahmezustand befindet.  
  
## Syntax  
  
```  
STDAPI_(JsErrorCode) JsHasException(  
   _Out_ bool *hasException  
);  
```  
  
#### Parameter  
 `hasException`  
 Gibt an, ob sich die Laufzeit des aktuellen Kontexts im Ausnahmezustand befindet.  
  
## Rückgabewert  
 Der Code `JsNoError`, wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## Hinweise  
 Wenn ein Aufruf in die Laufzeit eine Ausnahme zurückgibt \(z. B. wegen eines ausgeführten Skripts oder wegen eines Konvertierungsfehlers\), wird die Laufzeit in einen "Ausnahmezustand" versetzt. Alle Aufrufe in einen von der Laufzeit erstellten Kontext \(mit Ausnahme der Ausnahme\-APIs\) schlagen mit `JsErrorInExceptionState` fehl, bis die Ausnahme gelöscht wurde.  
  
 Wenn sich die Laufzeit des aktuellen Kontexts im Ausnahmezustand befindet, wenn ein Rückruf in die Engine zurückgegeben wird, löst die Engine die Ausnahme automatisch erneut aus.  
  
 Erfordert einen Active Script\-Kontext.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)