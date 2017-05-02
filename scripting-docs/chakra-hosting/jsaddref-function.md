---
title: "JsAddRef-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsAddRef"
helpviewer_keywords: 
  - "JsAddRef-Funktion"
ms.assetid: a7f3ed49-6a86-489a-abdf-c99428e79cae
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsAddRef-Funktion
Fügt einen Verweis auf ein Objekt mit Garbage Collection hinzu.  
  
## Syntax  
  
```  
STDAPI_(JsErrorCode) JsAddRef(  
   _In_ JsRef ref,  
   _Out_opt_ unsigned int *count  
);  
```  
  
#### Parameter  
 `ref`  
 Das Objekt, dem ein Verweis hinzugefügt werden soll.  
  
 `count`  
 Die neue Verweisanzahl des Objekts \(kann NULL übergeben\).  
  
## Rückgabewert  
 Der Code `JsNoError`, wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## Hinweise  
 Dies muss nur für `JsRef`\-Handles aufgerufen werden, die nicht irgendwo im Stapel gespeichert werden sollen.  Mit dem Aufrufen von `JsAddRef` wird sichergestellt, dass das Objekt, auf das der `JsRef` verweist, erst freigegeben wird, wenn `JsRelease` aufgerufen wird.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)