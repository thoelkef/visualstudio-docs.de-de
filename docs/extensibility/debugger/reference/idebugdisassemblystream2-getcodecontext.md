---
title: "IDebugDisassemblyStream2::GetCodeContext | Microsoft Docs"
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
  - "IDebugDisassemblyStream2::GetCodeContext"
helpviewer_keywords: 
  - "IDebugDisassemblyStream2::GetCodeContext"
ms.assetid: a6d0ae82-7617-4915-9713-369abe3e2e53
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDisassemblyStream2::GetCodeContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt ein Code für die gemäß einem angegebenen Speicherort des Codes Bezeichner zurück.  
  
## Syntax  
  
```cpp#  
HRESULT GetCodeContext(   
   UINT64               uCodeLocationId,  
   IDebugCodeContext2** ppCodeContext  
);  
```  
  
```c#  
int GetCodeContext(   
   ulong                  uCodeLocationId,  
   out IDebugCodeContext2 ppCodeContext  
);  
```  
  
#### Parameter  
 `uCodeLocationId`  
 \[in\]  Gibt den Speicherort des Codes Bezeichner an.  Weitere Informationen finden Sie im Abschnitt " Hinweise " für die [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)\-Methode zum Speicherort der Code eine Beschreibung eines Bezeichners.  
  
 `ppCodeContext`  
 \[out\]  Gibt ein [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)\-Objekt zurück, das den zugehörigen Code Elementkontext darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Der Speicherort des Codes Bezeichner kann von einem Aufruf der [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)\-Methode zurückgegeben werden und kann in der [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) Struktur angezeigt werden.  
  
 Um einen Code für Code in einen Bezeichner zu konvertieren, rufen Sie die [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)\-Methode auf.  
  
## Siehe auch  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)   
 [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)