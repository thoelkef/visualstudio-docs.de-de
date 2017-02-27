---
title: "IDebugProgramProvider2::GetProviderProcessData | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramProvider2::GetProviderProcessData"
helpviewer_keywords: 
  - "IDebugProgramProvider2::GetProviderProcessData"
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugProgramProvider2::GetProviderProcessData
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft eine Liste der laufenden Programme aus einem angegebenen Prozess ab.  
  
## Syntax  
  
```cpp  
HRESULT GetProviderProcessData(  
   PROVIDER_FLAGS         Flags,  
   IDebugDefaultPort2*    pPort,  
   AD_PROCESS_ID          processId,  
   CONST_GUID_ARRAY       EngineFilter,  
   PROVIDER_PROCESS_DATA* pProcess  
);  
```  
  
```c#  
int GetProviderProcessData(  
   enum_PROVIDER_FLAGS     Flags,  
   IDebugDefaultPort2      pPort,  
   AD_PROCESS_ID           ProcessId,  
   CONST_GUID_ARRAY        EngineFilter,  
   PROVIDER_PROCESS_DATA[] pProcess  
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
|`PFLAG_GET_PROGRAM_NODES`|Aufrufer fordert eine Liste von Knoten Programm zurückgegeben werden soll.|  
  
 `pPort`  
 \[in\]  Der Port, den der aufrufende Prozess ausgeführt wird.  
  
 `processId`  
 \[in\]  Eine [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) Struktur, die die ID des Prozesses enthält, der das betreffende Programm enthält.  
  
 `EngineFilter`  
 \[in\]  Ein Array von GUIDs für die Debugmodule zugewiesen, um diesen Prozess zu debuggen \(diese werden verwendet, um Programme zu filtern, die tatsächlich zurückgegeben werden, was auf Grundlage der angegebenen unterstützt. Module wenn nichts angegeben werden, werden alle Programme zurückgegeben\).  
  
 `pProcess`  
 \[out\]  Eine [PROVIDER\_PROCESS\_DATA](../../../extensibility/debugger/reference/provider-process-data.md) Struktur, die den angeforderten Informationen gefüllt wird.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode wird i. d. R. durch Aufrufen eines Prozesses zum Abrufen einer Liste von Programmen, die in diesem Prozess ausgeführt werden.  Die zurückgegebenen Informationen sind eine Liste von [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)\-Objekten.  
  
## Siehe auch  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [CONST\_GUID\_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)   
 [PROVIDER\_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [PROVIDER\_PROCESS\_DATA](../../../extensibility/debugger/reference/provider-process-data.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)