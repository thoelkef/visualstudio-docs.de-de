---
title: "JsGetDataViewStorage-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 7c2180e0-51d5-4cc8-ad21-8bf29ff7c583
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# JsGetDataViewStorage-Funktion
Ruft den zugrunde liegenden Speicher ab, der von einem `DataView` verwendet wird.  
  
## Syntax  
  
```cpp  
STDAPI_(JsErrorCode) JsGetDataViewStorage(  
   _In_ JsValueRef dataView,  
   _Outptr_result_bytebuffer_(*bufferLength) BYTE **buffer,  
   _Out_ unsigned int *bufferLength  
);  
```  
  
#### Parameter  
 `dataView`  
 Die DataView\-Instanz.  
  
 `buffer`  
 Der Puffer von DataView.  Die Lebensdauer des zurückgegebenen Puffers ist identisch mit der Lebensdauer des `DataView`.  Der Pufferzeiger zählt nicht als Verweis auf das `DataView` zum Zweck der Garbage Collection.  
  
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