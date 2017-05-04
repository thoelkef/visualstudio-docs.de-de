---
title: "Die Funktion JsGetIndexedPropertiesExternalData | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 2c313163-3462-42fd-8dee-3dfb3ac7f43f
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Die Funktion JsGetIndexedPropertiesExternalData
Ruft die externen Daten der indizierten Eigenschaften eines Objekts ab.  
  
## Syntax  
  
```  
STDAPI_(JsErrorCode) JsGetIndexedPropertiesExternalData(  
   _In_ JsValueRef object,  
   _Out_ void** data,  
   _Out_ JsTypedArrayType* arrayType,  
   _Out_ unsigned int* elementLength  
);  
```  
  
#### Parameter  
 `object`  
 Das Objekt.  
  
 `data`  
 Die externen Daten, die als Sicherungsspeicher für indizierte Eigenschaften des Objekts verwendet werden.  
  
 `arrayType`  
 Der Arrayelementtyp in externen Daten.  
  
 `elementLength`  
 Die Anzahl der Arrayelemente in externen Daten.  
  
## Rückgabewert  
 Der Code `JsNoError`, wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## Hinweise  
 Diese API wird nur im Edge\-Modus unterstützt.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)