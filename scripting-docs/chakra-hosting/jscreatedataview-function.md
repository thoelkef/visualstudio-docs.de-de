---
title: "JsCreateDataView Function | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 161e59eb-d429-46f7-9a38-bbf2149ccf44
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# JsCreateDataView Function
Erstellt ein Javascript `DataView`\-Objekt.  
  
## Syntax  
  
```  
JsErrorCode  JsCreateDataView(  
   _In_ JsValueRef arrayBuffer,  
   _In_ unsigned int byteOffset,  
   _In_ unsigned int byteLength,  
   _Out_ JsValueRef *result  
);  
```  
  
#### Parameter  
 `arrayBuffer`  
 Ein vorhandenes `ArrayBuffer`\-Objekt, das als Speicher für das Ergebnis\-`DataView`\-Objekt verwendet wird.  
  
 `byteOffset`  
 Der Offset in Bytes vom Anfang des `arrayBuffer` für das Ergebnis\-`DataView`, auf das verwiesen wird.  
  
 `byteLength`  
 Die Anzahl der Bytes im ArrayBuffer für das Ergebnis\-DataView, auf das verwiesen wird.  
  
 `result`  
 Das neue DataView\-Objekt.  
  
## Rückgabewert  
 Der Code `JsNoError`, wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## Hinweise  
 Erfordert einen Active Script\-Kontext.  
  
 Diese API wird nur im Edge\-Modus unterstützt.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)