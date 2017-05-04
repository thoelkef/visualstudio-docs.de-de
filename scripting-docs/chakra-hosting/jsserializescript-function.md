---
title: "JsSerializeScript-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsSerializeScript"
helpviewer_keywords: 
  - "JsSerializeScript-Funktion"
ms.assetid: ca42c194-e1c1-407d-b542-b9d494e3ac4e
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsSerializeScript-Funktion
Serialisiert ein analysiertes Skript in einen Puffer, der wiederverwendet werden kann.  
  
## Syntax  
  
```  
STDAPI_(JsErrorCode) JsSerializeScript(  
   _In_z_ const wchar_t *script,  
   _Out_writes_to_opt_(*bufferSize,  
   *bufferSize) BYTE *buffer,  
   _Inout_ unsigned long *bufferSize  
);  
```  
  
#### Parameter  
 `script`  
 Das zu serialisierende Skript.  
  
 `buffer`  
 Der Puffer für das serialisierte Skript.  Kann NULL sein.  
  
 `bufferSize`  
 Beim Eintritt ist dies die Größe des Puffers in Byte; beim Austritt ist dies die Größe des Puffers in Byte, die nötig ist, um das serialisierte Skript aufzunehmen.  
  
## Rückgabewert  
 Der Code `JsNoError`, wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## Hinweise  
 `JsSerializeScript` analysiert ein Skript und speichert dann das analysierte Formular des Skripts in einem laufzeitunabhängigen Format.  Das serialisierte Skript kann anschließend in jeder Laufzeit deserialisiert werden, ohne dass das Skript erneut analysiert werden muss.  
  
 Erfordert einen Active Script\-Kontext.  
  
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)