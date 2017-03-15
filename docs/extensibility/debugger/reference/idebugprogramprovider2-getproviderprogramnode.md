---
title: "IDebugProgramProvider2::GetProviderProgramNode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramProvider2::GetProviderProgramNode"
helpviewer_keywords: 
  - "IDebugProgramProvider2::GetProviderProgramNode"
ms.assetid: e62e8e83-acbb-4c52-aedf-ffbd4670db29
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugProgramProvider2::GetProviderProgramNode
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Knoten Programm für ein bestimmtes Programm ab.  
  
## Syntax  
  
```cpp  
HRESULT GetProviderProgramNode(  
   PROVIDER_FLAGS       Flags,  
   IDebugDefaultPort2*  pPort,  
   AD_PROCESS_ID        processId,  
   REFGUID              guidEngine,  
   UINT64               programId,  
   IDebugProgramNode2** ppProgramNode  
);  
```  
  
```c#  
int GetProviderProgramNode(  
   enum_PROVIDER_FLAGS    Flags,  
   IDebugDefaultPort2     pPort,  
   AD_PROCESS_ID          ProcessId,  
   ref Guid               guidEngine,  
   ulong                  programId,  
   out IDebugProgramNode2 ppProgramNode  
);  
```  
  
#### Parameter  
 `Flags`  
 \[in\]  Eine Kombination von Flags aus der [PROVIDER\_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)\-Enumeration.  Die folgenden Flags sind für diesen Aufruf typisch:  
  
|Flag|Beschreibung|  
|----------|------------------|  
|`PFLAG_REMOTE_PORT`|Aufrufer auf dem Remotecomputer ausgeführt wird.|  
|`PFLAG_DEBUGGEE`|Aufrufer zur Zeit gedebuggt wird \(weitere Informationen über Marshalling wird für jeden Knoten zurückgegeben\).|  
|`PFLAG_ATTACHED_TO_DEBUGGEE`|Aufrufer angefügt wurde, aber nicht vom Debugger gestartet.|  
  
 `pPort`  
 \[in\]  Der Port, den der aufrufende Prozess ausgeführt wird.  
  
 `processId`  
 \[in\]  Eine [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) Struktur, die die ID des Prozesses enthält, der das betreffende Programm enthält.  
  
 `guidEngine`  
 \[in\]  GUID des Debugmoduls, dass das Programm angefügt wurde \(sofern vorhanden\).  
  
 `programId`  
 \[in\]  ID des Programms, sodass das Programm den Knoten abgerufen werden soll.  
  
 `ppProgramNode`  
 \[out\]  Ein Objekt, das den angeforderten [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) Knoten Programm darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [PROVIDER\_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)