---
title: "IDebugEngineLaunch2::CanTerminateProcess | Microsoft Docs"
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
  - "IDebugEngineLaunch2::CanTerminateProcess"
helpviewer_keywords: 
  - "IDebugEngineLaunch2::CanTerminateProcess"
ms.assetid: 7973454d-c957-4123-a0ee-80ebcdbbd2d1
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngineLaunch2::CanTerminateProcess
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Bestimmt, ob ein Prozess beendet werden kann.  
  
## Syntax  
  
```cpp#  
HRESULT CanTerminateProcess (   
   IDebugProcess2* pProcess  
);  
```  
  
```c#  
int CanTerminateProcess (   
   IDebugProcess2 pProcess  
);  
```  
  
#### Parameter  
 `pProcess`  
 \[in\]  Ein [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)\-Objekt, das den Prozess darstellt wird beendet.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. Andernfalls wird ein Fehlercode zurückgegeben.  Gibt `S_FALSE` zurück, wenn das Modul den Prozess nicht beendet werden kann, z. B. weil der Zugriff verweigert wird.  
  
## Hinweise  
 Wenn diese Methode `S_OK`zurückgibt, kann die [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)\-Methode aufgerufen werden, um den Vorgang tatsächlich zu beenden.  
  
## Siehe auch  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)