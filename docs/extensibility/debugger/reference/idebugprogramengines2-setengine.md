---
title: "IDebugProgramEngines2::SetEngine | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramEngines2::SetEngine"
helpviewer_keywords: 
  - "IDebugProgramEngines2::SetEngine"
ms.assetid: c05857ee-89cf-455e-8f1e-300cce4a2eab
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgramEngines2::SetEngine
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Teilt das Programm oder den Programm, das mit Knoten Debuggen, um das Programm zu debuggen zu verwendende Modul \(DE\).  
  
## Syntax  
  
```cpp#  
HRESULT SetEngine(   
   REFGUID guidEngine  
);  
```  
  
```c#  
int SetEngine(   
   ref Guid guidEngine  
);  
```  
  
#### Parameter  
 `guidEngine`  
 \[in\]  Die GUID DEs.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)