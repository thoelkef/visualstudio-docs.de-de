---
title: "JsSerializedScriptUnloadCallback-Typdef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8d18c392-cca0-411e-9f2b-0d788b16161a
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# JsSerializedScriptUnloadCallback-Typdef
Wird von der Laufzeit aufgerufen, wenn sie mit allen Ressourcen fertig ist, die sich auf die Skriptausführung beziehen. Der Aufrufer muss die Quelle \(sofern geladen\), den Bytecode und den Kontext zu diesem Zeitpunkt freigeben.  
  
## Syntax  
  
```  
 typedef void (CALLBACK * JsSerializedScriptUnloadCallback)(  
  _In_ JsSourceContext sourceContext  
);  
```  
  
#### Parameter  
 `sourceContext`  
 Der an `JsParseSerializedScriptWithCallback` oder `JsRunSerializedScriptWithCallback` übergebene Kontext.  
  
## Hinweise  
  
> [!WARNING]
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)