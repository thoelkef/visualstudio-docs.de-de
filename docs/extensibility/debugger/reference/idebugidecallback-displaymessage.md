---
title: "IDebugIDECallback::DisplayMessage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugIDECallback::DisplayMessage"
ms.assetid: c19b48ee-b370-4fce-91fe-f82bf1e63179
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugIDECallback::DisplayMessage
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Sendet die angegebene Meldungszeichenfolge in das Ausgabefenster des Debuggers.  
  
## Syntax  
  
```cpp#  
HRESULT DisplayMessage (  
   LPCOLESTR szMessage  
);  
```  
  
```c#  
int DisplayMessage (  
   string szMessage  
);  
```  
  
#### Parameter  
 `szMessage`  
 \[in\]  Im Ausgabefenster des Debuggers anzuzeigenden Meldungszeichenfolge.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)