---
title: "IDebugQueryEngine2::GetEngineInterface | Microsoft Docs"
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
  - "IDebugQueryEngine2::GetEngineInterface"
helpviewer_keywords: 
  - "IDebugQueryEngine2::GetEngineInterface"
ms.assetid: ed84aa98-7ec7-48f3-97ae-821090bc3664
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugQueryEngine2::GetEngineInterface
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft eine benutzerdefinierte Debuginformationen Schnittstelle des Moduls \(DE\) ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetEngineInterface(   
   IUnknown** ppUnk  
);  
```  
  
```c#  
int GetEngineInterface(   
   out object ppUnk  
);  
```  
  
#### Parameter  
 `ppUnk`  
 \[out\]  Gibt ein `IUnknown`\-Objekt darstellt, das Debugmodul \(DE\) zurück, und für jede andere gültige Schnittstelle abgefragt werden kann, die mit DE zugeordnet ist \(z [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) oder [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)\).  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Die resultierende Schnittstelle sollte sorgfältig verwendet werden, da durch Aufrufen der umgeht die Schnittstellen, die von dieser Methode abgerufenen Debuggen des Managers, der der Sitzung verarbeitet und führt möglicherweise das SDM, das in einem ungültigen Zustand oder während des Debuggens Fehler generiert.  
  
## Siehe auch  
 [IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)