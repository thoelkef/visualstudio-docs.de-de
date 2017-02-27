---
title: "IDebugDisassemblyStream2::GetCodeLocationId | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDisassemblyStream2::GetCodeLocationId"
helpviewer_keywords: 
  - "IDebugDisassemblyStream2::GetCodeLocationId"
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDisassemblyStream2::GetCodeLocationId
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt einen Speicherort des Codes Bezeichner für einen bestimmten Code Elementkontext zurück.  
  
## Syntax  
  
```cpp#  
HRESULT GetCodeLocationId(   
   IDebugCodeContext2* pCodeContext,  
   UINT64*             puCodeLocationId  
);  
```  
  
```c#  
int GetCodeLocationId(   
   IDebugCodeContext2 pCodeContext,  
   out ulong          puCodeLocationId  
);  
```  
  
#### Parameter  
 `pCodeContext`  
 \[in\]  Ein mit einem Bezeichner zu konvertierende [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)\-Objekt.  
  
 `puCodeLocationId`  
 \[out\]  Gibt den Speicherort des Codes Bezeichner zurück.  Siehe Hinweise.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  Gibt `E_CODE_CONTEXT_OUT_OF_SCOPE` zurück, wenn der Code jedoch vom Kontext außerhalb des Bereichs gültig ist.  
  
## Hinweise  
 Der Speicherort des Codes Bezeichner entspricht dem Modul \(Debuggen\) DE die Disassembly unterstützt bestimmt.  Dieser Speicherort wird intern vom Bezeichner DE verwendet, um Positionen im Code verfolgen und ist in der Regel eine Adresse oder einen beliebigen Offsets.  Die einzige Anforderung ist, dass der Code bei Kontext aus einer Position kleiner als Kontext eines anderen Speicherorts des Codes ist, muss der entsprechende Code für kontexts Bezeichner des ersten Code geringer als der Speicherort des Codes Bezeichner des zweiten Code kontexts werden.  
  
 Um den Code Elementkontext eines Bezeichners Speicherort des Codes abzurufen, rufen Sie die [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)\-Methode auf.  
  
## Siehe auch  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)