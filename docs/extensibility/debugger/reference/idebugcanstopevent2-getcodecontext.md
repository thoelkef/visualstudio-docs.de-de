---
title: "IDebugCanStopEvent2::GetCodeContext | Microsoft Docs"
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
  - "IDebugCanStopEvent2::GetCodeContext"
helpviewer_keywords: 
  - "IDebugCanStopEvent2::GetCodeContext"
ms.assetid: eecf08b6-f9b7-4358-941b-3a448a92ac62
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCanStopEvent2::GetCodeContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Kontext des Codes ab, der die Position dieses Ereignisses beschreibt.  
  
## Syntax  
  
```cpp#  
HRESULT GetCodeContext(   
   IDebugCodeContext2** ppCodeContext  
);  
```  
  
```c#  
int GetCodeContext(   
   out IDebugCodeContext2 ppCodeContext  
);  
```  
  
#### Parameter  
 `ppCodeContext`  
 \[out\]  Gibt das [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)\-Objekt zurück, das den aktuellen Speicherort des Codes darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Für die meisten von architekturen Code kann ein Kontext für eine Adresse des Programms Laufzeit in einem datenstrom gehalten werden, und zeigen auf eine bestimmte Anweisung.  
  
 Um den Dokumentenkontext abzurufen, der zu den Quellcodezeilen ausgerichtet ist, rufen Sie die [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)\-Methode auf.  
  
## Siehe auch  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)