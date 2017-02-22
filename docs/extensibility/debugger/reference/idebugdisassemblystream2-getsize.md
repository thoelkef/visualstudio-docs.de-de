---
title: "IDebugDisassemblyStream2::GetSize | Microsoft Docs"
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
  - "IDebugDisassemblyStream2::GetSize"
helpviewer_keywords: 
  - "IDebugDisassemblyStream2::GetSize"
ms.assetid: 8f512704-12d0-46d2-959a-4f8dffe117b5
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDisassemblyStream2::GetSize
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft die Größe in Anweisungen dieses Disassemblys datenstroms ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetSize(   
   UINT64* pnSize  
);  
```  
  
```c#  
int GetSize(   
   out ulong pnSize  
);  
```  
  
#### Parameter  
 `pnSize`  
 \[out\]  Gibt die Größe in Anweisungen zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Der Wert, der aus dieser Methode zurückgegeben wird, kann verwendet werden, um ein Array [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) Strukturen zugeordnet werden soll, das dann an die [Lesen](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)\-Methode übergeben wird.  
  
## Siehe auch  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [Lesen](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)