---
title: "JsGetTypedArrayInfo-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 992bc4e9-3d06-4ad2-8b6b-88a437360f81
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# JsGetTypedArrayInfo-Funktion
Ruft häufig verwendete Eigenschaften eines typisierten Arrays ab.  
  
## Syntax  
  
```  
STDAPI_(JsErrorCode) JsGetTypedArrayInfo(  
  _In_ JsValueRef typedArray,  
  _Out_opt_ JsTypedArrayType *arrayType,  
  _Out_opt_ JsValueRef *arrayBuffer,  
  _Out_opt_ unsigned int *byteOffset,  
  _Out_opt_ unsigned int *byteLength  
);  
  
```  
  
#### Parameter  
 `typedArray`  
 Die Instanz des typisierten Arrays.  
  
 `arrayType`  
 Der Typ des Arrays.  
  
 `arrayBuffer`  
 Der `ArrayBuffer`\-Speicherbereich des Arrays.  
  
 `byteOffset`  
 Der Offset in Bytes ab dem Anfang des Arraypuffers \(arrayBuffer\), auf den das Array verweist.  
  
 `byteLength`  
 Die Anzahl der Bytes im Array.  
  
## Rückgabewert  
 Der Code `JsNoError`, wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## Hinweise  
 Erfordert einen Active Script\-Kontext.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)