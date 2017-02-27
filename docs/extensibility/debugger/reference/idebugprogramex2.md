---
title: "IDebugProgramEx2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramEx2"
helpviewer_keywords: 
  - "IDebugProgramEx2-Schnittstelle"
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# IDebugProgramEx2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle ermöglicht die Debuginformationen Anfügen des Managers der Sitzung \(SDM\) mit einem Programm Programm und ruft den Knoten ab, der einem Programm zugeordnet ist.  
  
## Syntax  
  
```  
IDebugProgramEx2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Ein benutzerdefinierter Port lieferant implementiert diese Schnittstelle für dasselbe Objekt, das die [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)\-Schnittstelle für das SDM mit einem Programm, während gleichzeitig den Anschlusslieferanten ermöglichen anfügen können, um alle Sitzungen nachverfolgt auf das Programm angefügt.  Der benutzerdefinierte Port lieferant kann diese Schnittstelle implementieren, wenn er ausgewählt wird.  
  
## Hinweise für Aufrufer  
 Das SDM ruft [QueryInterface](/visual-cpp/atl/queryinterface) auf einer `IDebugProgram2`\-Schnittstelle auf, um diese Schnittstelle, um Sitzungen zu verfolgen, die in den Programmen verbunden haben.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugProgramEx2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[Anfügen](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Fügt ein Programm zu einer Sitzung an.|  
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Ruft den Knoten ab, der die Programmierung mit einem Programm zugeordnet ist.|  
  
## Hinweise  
 Diese Schnittstelle ist zwischen dem SDM und dem Programm privat.  
  
## Anforderungen  
 Header: Portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)