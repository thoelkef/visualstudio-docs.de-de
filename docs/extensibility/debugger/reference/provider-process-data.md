---
title: "PROVIDER_PROCESS_DATA | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PROVIDER_PROCESS_DATA"
helpviewer_keywords: 
  - "PROVIDER_PROCESS_DATA-Struktur"
ms.assetid: ec2362ed-4a0c-4a09-9d66-8ff04e4f41ee
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# PROVIDER_PROCESS_DATA
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Struktur enthält Informationen über die Prozesse bereit, die auf einem Computer ausgeführt werden.  
  
## Syntax  
  
```cpp#  
typedef struct tagPROVIDER_PROCESS_DATA {  
   PROVIDER_FIELDS    Fields;  
   PROGRAM_NODE_ARRAY ProgramNodes;  
   BOOL               fIsDebuggerPresent;  
} PROVIDER_PROCESS_DATA;  
```  
  
```c#  
public struct PROVIDER_PROCESS_DATA {  
   public uint               Fields;  
   public PROGRAM_NODE_ARRAY ProgramNodes;  
   public int                fIsDebuggerPresent;  
}  
```  
  
## Mitglieder  
 Felder  
 Eine Kombination von Flags aus der [PROVIDER\_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)\-Enumeration, die angibt, welche Felder aufgefüllt werden.  
  
 ProgramNodes  
 Eine [PROGRAM\_NODE\_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) Programm Struktur, die ein Array von Knoten enthält.  
  
 fIsDebuggerPresent  
 Ein Wert ungleich 0 \(`TRUE`\), wenn der [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Debugger ausgeführt wird,`FALSE`\(null\), wenn dies nicht der Fall ist.  
  
## Hinweise  
 Diese Struktur wird auf die [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)\-Methode übergeben, in der er eingetragen wird.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROVIDER\_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)   
 [PROGRAM\_NODE\_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)