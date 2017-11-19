---
title: IDebugProgramProvider2::GetProviderProgramNode | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramProvider2::GetProviderProgramNode
helpviewer_keywords: IDebugProgramProvider2::GetProviderProgramNode
ms.assetid: e62e8e83-acbb-4c52-aedf-ffbd4670db29
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4ad5540d1f93e44b069cac4873880e9db9d96919
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogramprovider2getproviderprogramnode"></a>IDebugProgramProvider2::GetProviderProgramNode
Ruft die Programm-Knoten für ein bestimmtes Programm ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetProviderProgramNode(  
   PROVIDER_FLAGS       Flags,  
   IDebugDefaultPort2*  pPort,  
   AD_PROCESS_ID        processId,  
   REFGUID              guidEngine,  
   UINT64               programId,  
   IDebugProgramNode2** ppProgramNode  
);  
```  
  
```csharp  
int GetProviderProgramNode(  
   enum_PROVIDER_FLAGS    Flags,  
   IDebugDefaultPort2     pPort,  
   AD_PROCESS_ID          ProcessId,  
   ref Guid               guidEngine,  
   ulong                  programId,  
   out IDebugProgramNode2 ppProgramNode  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `Flags`  
 [in] Eine Kombination aus Flags aus der [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) Enumeration. Die folgenden Flags sind typisch für diesen Aufruf:  
  
|Flag|Beschreibung|  
|----------|-----------------|  
|`PFLAG_REMOTE_PORT`|Aufrufer, die auf dem Remotecomputer ausgeführt wird.|  
|`PFLAG_DEBUGGEE`|Aufrufer gerade gedebuggt wird (Weitere Informationen über das marshalling wird für jeden Knoten zurückgegeben werden).|  
|`PFLAG_ATTACHED_TO_DEBUGGEE`|Aufrufer wurde angefügt, aber nicht vom Debugger gestartet.|  
  
 `pPort`  
 [in] Der Port der aufrufende Prozess ausgeführt wird.  
  
 `processId`  
 [in] Ein [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) halten die ID des Prozesses mit dem Programm betreffende Struktur.  
  
 `guidEngine`  
 [in] GUID der Debugging-Modul, dem das Programm die (sofern vorhanden) zugeordnet ist.  
  
 `programId`  
 [in] Die ID des Programms für das Programm Knotens abgerufen.  
  
 `ppProgramNode`  
 [out] Ein [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) Objekt, das das angeforderte Programm Knoten darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)