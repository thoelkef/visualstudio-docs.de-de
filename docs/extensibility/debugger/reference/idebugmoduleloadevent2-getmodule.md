---
title: "IDebugModuleLoadEvent2::GetModule | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModuleLoadEvent2::GetModule"
helpviewer_keywords: 
  - "IDebugModuleLoadEvent2::GetModule"
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugModuleLoadEvent2::GetModule
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft das Modul ab, das geladen oder entladen wird.  
  
## Syntax  
  
```cpp#  
HRESULT GetModule(   
   IDebugModule2** pModule,  
   BSTR*           pbstrDebugMessage,  
   BOOL*           pbLoad  
);  
```  
  
```c#  
int GetModule(   
   out IDebugModule2 pModule,  
   ref string        pbstrDebugMessage,  
   ref int           pbLoad  
);  
```  
  
#### Parameter  
 `pModule`  
 \[out\]  Gibt ein [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)\-Objekt zurück, das das Modul darstellt, das geladen oder entladen wird.  
  
 `pbstrDebugMessage`  
 \[in, out\]  Gibt eine optionale Nachricht zurück, die dieses Ereignis beschreibt.  Wenn dieser Parameter ein NULL\-Wert ist, wird keine Meldung angefordert.  
  
 `pbLoad`  
 \[in, out\]  Ein Wert ungleich 0 \(`TRUE`\) wenn das Modul geladen und`FALSE`\(null\), wenn das Modul entladen wird.  Wenn dieser Parameter ein NULL\-Wert ist, wird kein Status angefordert.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)