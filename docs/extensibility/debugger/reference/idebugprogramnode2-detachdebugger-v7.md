---
title: "IDebugProgramNode2::DetachDebugger_V7 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNode2::DetachDebugger"
helpviewer_keywords: 
  - "IDebugProgramNode2::DetachDebugger"
  - "IDebugProgramNode2::DetachDebugger_V7"
ms.assetid: d2d4b78e-a2dd-4217-97a6-ab648fd2ee2f
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProgramNode2::DetachDebugger_V7
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

VERALTET.  NOT TUN USE.  
  
## Syntax  
  
```cpp#  
HRESULT DetachDebugger_V7 (   
   void   
);  
```  
  
```c#  
int DetachDebugger_V7 ();  
```  
  
## Rückgabewert  
 Eine Implementierung sollte immer `E_NOTIMPL`zurückgeben.  
  
## Hinweise  
  
> [!WARNING]
>  Ab [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)]wird diese Methode nicht mehr verwendet und sollte immer `E_NOTIMPL`zurückgeben.  
  
 Diese Methode wird aufgerufen, wenn der Debugger unerwartet beendet wird.  Wenn diese Methode aufgerufen wird, sollte DE das Programm fortgesetzt werden, wenn der Benutzer als der von ihr getrennt wird.  Nicht mehr die Ereignisse gesendet werden sollen.  Das Programm sollte sich in einem Zustand, in dem sich das von einer anderen Instanz des Debuggers anfügbar ist.  
  
## Siehe auch  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)