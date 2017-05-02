---
title: "JsSerializedScriptLoadSourceCallback-Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9406c488-76ac-49e5-b305-39751f3412ea
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# JsSerializedScriptLoadSourceCallback-Typedef
Von der Laufzeit zum Laden des Quellcodes des serialisierten Skripts aufgerufen. Der Aufrufer muss den Skriptpuffer bis `JsSerializedScriptUnloadCallback` gültig halten.  
  
## Syntax  
  
```  
typedef bool (CALLBACK * JsSerializedScriptLoadSourceCallback)(  
  _In_ JsSourceContextsourceContext,  
  _Outptr_result_z_ const wchar_t** scriptBuffer  
);  
```  
  
#### Parameter  
 `sourceContext`  
 Der an `JsParseSerializedScriptWithCallback` oder `JsRunSerializedScriptWithCallback` übergebene Kontext.  
  
 `scriptBuffer`  
 Das zurückgegebene Skript.  
  
## Hinweise  
  
> [!WARNING]
## Anforderungen  
 **Header:** jsrt.h  
  
## Siehe auch  
 [Verweis \(JavaScript\-Laufzeit\)](../chakra-hosting/reference-javascript-runtime.md)