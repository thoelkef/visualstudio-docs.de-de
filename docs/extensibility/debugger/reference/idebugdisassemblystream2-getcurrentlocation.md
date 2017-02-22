---
title: "IDebugDisassemblyStream2::GetCurrentLocation | Microsoft Docs"
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
  - "IDebugDisassemblyStream2::GetCurrentLocation"
helpviewer_keywords: 
  - "IDebugDisassemblyStream2::GetCurrentLocation"
ms.assetid: 512302f1-12b1-4107-8a6e-c5bc878ce1c3
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDisassemblyStream2::GetCurrentLocation
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt einen Speicherort des Codes Bezeichner zurück, der den aktuellen Speicherort des Codes darstellt.  
  
## Syntax  
  
```cpp#  
HRESULT GetCurrentLocation(   
   UINT64* puCodeLocationId  
);  
```  
  
```c#  
int GetCurrentLocation(   
   out ulong puCodeLocationId  
);  
```  
  
#### Parameter  
 `puCodeLocationId`  
 \[out\]  Gibt den Speicherort des Codes Bezeichner zurück.  Weitere Informationen finden Sie im Abschnitt " Hinweise " für die [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)\-Methode zum Speicherort der Code eine Beschreibung eines Bezeichners.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Der Bezeichner der Speicherort des Codes kann einem Kontext Code konvertiert werden, indem die [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)\-Methode aufruft.  
  
## Siehe auch  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)