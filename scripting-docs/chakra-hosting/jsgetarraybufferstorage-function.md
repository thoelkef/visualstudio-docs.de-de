---
title: "JsGetArrayBufferStorage-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 712ae298-36a9-47ef-b089-e51835c056bc
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# JsGetArrayBufferStorage-Funktion
Ruft den zugrunde liegenden Speicher ab, der von einem `ArrayBuffer` verwendet wird.  
  
## Syntax  
  
```  
JsErrorCode STDAPI_ JsGetArrayBufferStorage(  
   _In_ JsValueRef arrayBuffer,  
   _Outptr_result_bytebuffer_(*bufferLength) BYTE **buffer,  
   _Out_ unsigned int *bufferLength  
);  
```  
  
#### Parameter  
 `arrayBuffer`  
 Die ArrayBuffer\-Instanz.  
  
 `buffer`  
 Der Puffer von ArrayBuffer.  Die Lebensdauer des zurückgegebenen Puffers ist identisch mit der Lebensdauer des `ArrayBuffer`.  Der Pufferzeiger zählt nicht als Verweis auf das `ArrayBuffer` zum Zweck der Garbage Collection.  
  
 `bufferLength`  
 Die Anzahl von Bytes im Puffer.  
  
## Rückgabewert  
 Der Code `JsNoError`, wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## Hinweise  
 Erfordert einen Active Script\-Kontext.  
  
 Diese API wird nur im Edge\-Modus unterstützt.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)