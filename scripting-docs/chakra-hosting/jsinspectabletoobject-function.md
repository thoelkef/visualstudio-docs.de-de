---
title: "JsInspectableToObject-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: dd0ad567-2ba8-4a63-bee4-2c6ff5ce9fa9
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# JsInspectableToObject-Funktion
Erstellt einen JavaScript\-Wert, der eine Projektion des übergebenen `IInspectable`\-Zeigers ist.  
  
## Syntax  
  
```  
STDAPI_(JsErrorCode) JsInspectableToObject(  
        _In_ IInspectable  *inspectable,  
        _Out_ JsValueRef *value  
);  
```  
  
#### Parameter  
 `inspectable`  
 Eine zu projizierende `IInspectable`.  
  
 `value`  
 Ein JavaScript\-Wert, der eine Projektion der `IInspectable` ist.  
  
## Rückgabewert  
 Der Code `JsNoError`, wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## Hinweise  
 Der projizierte Wert kann vom Skript verwendet werden, um ein WinRT\-Objekt aufzurufen.  Hosts sind verantwortlich zum Erzwingen von COM\-Threadingregeln.  
  
 Erfordert einen Active Script\-Kontext.  
  
 Diese API wird nur im Edge\-Modus unterstützt.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)