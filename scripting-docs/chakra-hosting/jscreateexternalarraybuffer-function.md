---
title: "JsCreateExternalArrayBuffer-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4a02aaec-0f67-4bf9-b37c-71cdb1410ca4
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# JsCreateExternalArrayBuffer-Funktion
Erstellt ein Javascript `ArrayBuffer`\-Objekt, um auf externen Speicher zuzugreifen.  
  
## Syntax  
  
```  
STDAPI_(JsErrorCode) JsCreateExternalArrayBuffer(  
  _Pre_maybenull_ _Pre_writable_byte_size_(byteLength) void *data,  
  _In_ unsigned int byteLength,  
  _In_opt_ JsFinalizeCallback finalizeCallback,  
  _In_opt_ void *callbackState,  
  _Out_ JsValueRef *result  
);  
  
```  
  
#### Parameter  
 `data`  
 Ein Zeiger auf den externen Speicher.  
  
 `byteLength`  
 Die Anzahl von Bytes im externen Speicher.  
  
 `finalizeCallback`  
 Ein Rückruf, der erfolgt, wenn das Objekt abgeschlossen ist. Ist möglicherweise NULL.  
  
 `callbackState`  
 Vom Benutzer angegebener Zustand, der wieder an „finalizeCallback“ übergeben wird.  
  
 `result`  
 Das neue `ArrayBuffer`\-Objekt.  
  
## Rückgabewert  
 Der Code `JsNoError`, wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## Hinweise  
 Erfordert einen Active Script\-Kontext.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)