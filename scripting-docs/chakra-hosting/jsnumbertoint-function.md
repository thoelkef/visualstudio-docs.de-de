---
title: "JsNumberToInt-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 8b9256d6-76ac-4c74-a97c-fbb16c13f5f5
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# JsNumberToInt-Funktion
Ruft den `int`\-Wert eines Zahlenwerts ab.  
  
## Syntax  
  
```  
STDAPI_(JsErrorCode) JsNumberToInt(  
      _In_ JsValueRef value,  
      _Out_ int *intValue  
);  
```  
  
#### Parameter  
 `value`  
 Der Zahlenwert, der in einen `int`\-Wert konvertiert werden soll.  
  
 `intValue`  
 Der `int`\-Wert.  
  
## Rückgabewert  
  
## Hinweise  
 Diese Funktion ruft den Wert eines Zahlenwerts ab und konvertiert ihn in einen `int`\-Wert.  Sie schlägt mit `JsErrorInvalidArgument` fehl, wenn der Typ des Werts nicht "Zahl" ist.  
  
 Erfordert einen Active Script\-Kontext.  
  
 Diese API wird nur im Edge\-Modus unterstützt.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)