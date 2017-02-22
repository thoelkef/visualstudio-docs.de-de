---
title: "IDebugProcessEx2::AddImplicitProgramNodes | Microsoft Docs"
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
  - "IDebugProcessEx2::AddImplicitProgramNodes"
helpviewer_keywords: 
  - "IDebugProcessEx2::AddImplicitProgramNodes-Methode"
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcessEx2::AddImplicitProgramNodes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode fügt für jedes Programm einen Knoten hinzu, das Debuggen Modul \(DE\) angegeben hat.  
  
## Syntax  
  
```cpp#  
HRESULT AddImplicitProgramNodes(  
   REFGUID guidLaunchingEngine,  
   GUID*   rgguidSpecificEngines,  
   DWORD   celtSpecificEngines  
);  
```  
  
```c#  
int AddImplicitProgramNodes(  
   ref Guid guidLaunchingEngine,  
   Guid[]   rgguidSpecificEngines,  
   uint     celtSpecificEngines  
);  
```  
  
#### Parameter  
 `guidLaunchingEngine`  
 \[in\]  DE `GUID` aus, das verwendet werden soll, um Programme zu starten \(und wird angenommen, dass seine eigenen Knoten Programm hinzufügen\).  
  
 `rgguidSpecificEngines`  
 \[in\]  Array von `GUID`aus dem Knoten für das Programm hinzugefügt werden.  
  
 `celtSpecificEngines`  
 \[in\]  Die Anzahl der `GUID`im `rgguidSpecificEngines` Array.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 DE[Programm\-Knoten](../../../extensibility/debugger/program-nodes.md) wird für jedes hinzugefügte, das in `rgguidSpecificEngines`— moduls Starten ohne den aufgeführten \(wie angegeben\), das in `guidLaunchingEngine`angenommen wird, um den eigenen Knoten Programms hinzuzufügen, wenn es ein Programm gestartet wird.  
  
## Siehe auch  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Programm\-Knoten](../../../extensibility/debugger/program-nodes.md)