---
title: "IDebugProgramNodeAttach2::OnAttach | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNodeAttach2::OnAttach"
helpviewer_keywords: 
  - "IDebugProgramNodeAttach2::OnAttach"
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
caps.latest.revision: 3
caps.handback.revision: 3
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramNodeAttach2::OnAttach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Fügt dem entsprechenden Programm oder verzögert Anfügen an den Prozess zur [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)\-Methode.  
  
## Syntax  
  
```cpp#  
HRESULT OnAttach(  
   [in] REFGUID guidProgramId  
);  
```  
  
```c#  
int OnAttach(  
   ref Guid guidProgramId  
};  
```  
  
#### Parameter  
 `guidProgramId`  
 \[in\]  Programm zum zugeordneten `GUID` zuzuweisen.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück.  Gibt `S_FALSE` zurück, wenn die [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)\-Methode nicht aufgerufen wird.  Andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode wird beim Anfügen Prozesses aufgerufen, bevor die [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)\-Methode aufgerufen wird.  Die `OnAttach`\-Methode kann den Anfügen Prozess selbst ausgeführt wird \(in diesem Fall diese Methode `S_FALSE`zurückgibt\) oder den Prozess zum Anfügen `IDebugEngine2::Attach`\-Methode \(die verzögert `OnAttach`\-Methode gibt `S_OK`zurück\).  In jedem Ereignis kann die `OnAttach`\-Methode `GUID` Festlegen des Programms, das dem angegebenen `GUID`gedebuggt wird.  
  
## Siehe auch  
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)