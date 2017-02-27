---
title: "IDebugEngine2::DestroyProgram | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::DestroyProgram"
helpviewer_keywords: 
  - "IDebugEngine2::DestroyProgram"
ms.assetid: 0c9e2698-c70f-4770-a7bb-39650e9c3a1f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEngine2::DestroyProgram
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Teilt eine Debug\- Modul \(DE\), das das angegebene Programm atypisch beendet wurde und alle Verweise auf das Programm DE dem die Bereinigung sollte und sendet ein Programm zerstören Ereignis.  
  
## Syntax  
  
```cpp#  
HRESULT DestroyProgram(   
   IDebugProgram2* pProgram  
);  
```  
  
```cpp#  
int DestroyProgram(   
   IDebugProgram2 pProgram  
);  
```  
  
#### Parameter  
 `pProgram`  
 \[in\]  Ein [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)\-Objekt, das das Programm darstellt, das atypisch beendet wurde.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Nachdem diese Methode aufgerufen wurde, sendet daraufhin ein DE [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)\-Ereignis zurück zum Debuggen von Manager der Sitzung \(SDM\).  
  
 Diese Methode ist nicht implementiert \(gibt `E_NOTIMPL`\) zurück, wenn DE in demselben Prozess ausgeführt wird, der das Programm, das gedebuggt wird.  Diese Methode wird nur bei der Implementierung DE in demselben Prozess wie das SDM ausgeführt wird.  
  
## Siehe auch  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)