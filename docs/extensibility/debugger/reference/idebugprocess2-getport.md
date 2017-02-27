---
title: "IDebugProcess2::GetPort | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::GetPort"
helpviewer_keywords: 
  - "IDebugProcess2::GetPort"
ms.assetid: e39b6e5a-64eb-48cf-a53d-da4fdb968e2d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess2::GetPort
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Anschluss ab, zu dem der Prozess ausgeführt wird.  
  
## Syntax  
  
```cpp#  
HRESULT GetPort(   
   IDebugPort2** ppPort  
);  
```  
  
```c#  
int GetPort(   
   out IDebugPort2 ppPort  
);  
```  
  
#### Parameter  
 `ppPort`  
 \[out\]  Gibt ein [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)\-Objekt zurück, das den Anschluss darstellt, mit dem der Prozess gestartet wurde.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)