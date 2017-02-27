---
title: "IDebugProgram2::GetProcess | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::GetProcess"
helpviewer_keywords: 
  - "IDebugProgram2::GetProcess"
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugProgram2::GetProcess
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Prozess ab, die in diesem Programm ausgeführt wird.  
  
## Syntax  
  
```cpp  
HRESULT GetProcess(  
   IDebugProcess2** ppProcess  
);  
```  
  
```c#  
int GetProcess(  
   out IDebugProcess2 ppProcess  
);  
```  
  
#### Parameter  
 `ppProcess`  
 \[out\]  Gibt die [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)\-Schnittstelle zurück, die den Prozess darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Sofern ein Modul \(Debug\) DE [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) die Schnittstelle implementiert, muss die DEs Implementierung dieser Methode `E_NOTIMPL` immer zurückgegeben, da DE nicht bestimmen kann, die sich in Verarbeitung ausgeführt wird und daher eine Implementierung dieser Methode nicht erfüllen kann.  
  
 Die `IDebugEngineLaunch2`\-Schnittstelle zu implementieren bedeutet, dass DE können muss einen Prozess erstellen. Deshalb ist die DEs Implementierung der [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)\-Schnittstelle in der Lage, zu wissen, welcher Prozess sie ausgeführt wird.  
  
## Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)