---
title: "JsStringToPointer-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsStringToPointer"
helpviewer_keywords: 
  - "JsStringToPointer-Funktion"
ms.assetid: c7aa7a09-489d-4435-8f8a-aeb62f8875ae
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsStringToPointer-Funktion
Ruft den Zeichenfolgenzeiger für einen Zeichenfolgenwert ab.  
  
## Syntax  
  
```  
STDAPI_(JsErrorCode) JsStringToPointer(  
   _In_ JsValueRef value,  
   _Outptr_result_buffer_(*stringLength) const wchar_t **stringValue,  
   _Out_ size_t *stringLength  
);  
```  
  
#### Parameter  
 `value`  
 Der Zeichenfolgenwert, der in einen Zeichenfolgenzeiger konvertiert werden soll.  
  
 `stringValue`  
 Der Zeichenfolgenzeiger.  
  
 `stringLength`  
 Die Länge der Zeichenfolge.  
  
## Rückgabewert  
 Der Code `JsNoError`, wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## Hinweise  
 Diese Funktion ruft den Zeichenfolgenzeiger für einen Zeichenfolgenwert ab.  Sie schlägt mit `JsErrorInvalidArgument` fehl, wenn der Typ des Werts nicht "Zeichenfolge" ist.  Die Lebensdauer der zurückgegebenen Zeichenfolge entspricht der Lebensdauer des Werts, aus dem sie stammt. Der Zeichenfolgenzeiger wird jedoch nicht als Verweis auf den Wert angesehen \(und verhindert daher nicht ihre Erfassung\).  
  
 Erfordert einen Active Script\-Kontext.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)