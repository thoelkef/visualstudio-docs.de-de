---
title: "IEnumDebugProcesses2::Reset | Microsoft Docs"
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
  - "IEnumDebugProcesses2::Reset"
helpviewer_keywords: 
  - "IEnumDebugProcesses2::Reset"
ms.assetid: 31cbde4f-0bba-497a-9969-d2c342ef4a7b
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugProcesses2::Reset
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Setzt die Enumeration auf das erste Element zurück.  
  
## Syntax  
  
```cpp#  
HRESULT Reset(  
   void  
);  
```  
  
```c#  
int Reset();  
```  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Nachdem diese Methode aufgerufen wurde, gibt der nächste Aufruf der [Weiter](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)\-Methode das erste Element der Enumeration zurück.  
  
## Siehe auch  
 [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)