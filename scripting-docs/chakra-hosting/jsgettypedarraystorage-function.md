---
title: "JsGetTypedArrayStorage-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 52e4ac5f-cc71-456d-95de-a48f7327503d
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# JsGetTypedArrayStorage-Funktion
Ruft den zugrunde liegenden Speicher ab, der von einem typisierten Array verwendet wird.  
  
## Syntax  
  
```  
STDAPI_(JsErrorCode) JsGetTypedArrayStorage(  
   _In_ JsValueRef typedArray,  
   _Outptr_result_bytebuffer_(*bufferLength) BYTE **buffer,  
   _Out_ unsigned int *bufferLength,  
   _Out_opt_ JsTypedArrayType *arrayType,  
   _Out_opt_ int *elementSize  
);  
```  
  
#### Parameter  
 `typedArray`  
 Die Instanz des typisierten Arrays.  
  
 `buffer`  
 Der Arraypuffer.  Die Lebensdauer des zurückgegebenen Puffers ist identisch mit der Lebensdauer des Arrays.  Der Pufferzeiger zählt nicht als Verweis auf das Array zum Zweck der Garbage Collection.  
  
 `bufferLength`  
 Die Anzahl von Bytes im Puffer.  
  
 `arrayType`  
 Der Typ des Arrays.  
  
 `elementSize`  
 Die Größe eines Elements des Arrays.  
  
## Rückgabewert  
 Der Code `JsNoError`, wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## Hinweise  
 Erfordert einen Active Script\-Kontext.  
  
 Diese API wird nur im Edge\-Modus unterstützt.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)