---
title: IDebugProgramProvider2::GetProviderProcessData | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgramProvider2::GetProviderProcessData
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProcessData
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b86692c607aea3a428fea7e35e5346ae1595983d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49254916"
---
# <a name="idebugprogramprovider2getproviderprocessdata"></a>IDebugProgramProvider2::GetProviderProcessData
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft eine Liste von gerade ausgeführten Programmen von einem angegebenen Prozess.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetProviderProcessData(  
   PROVIDER_FLAGS         Flags,  
   IDebugDefaultPort2*    pPort,  
   AD_PROCESS_ID          processId,  
   CONST_GUID_ARRAY       EngineFilter,  
   PROVIDER_PROCESS_DATA* pProcess  
);  
```  
  
```csharp  
int GetProviderProcessData(  
   enum_PROVIDER_FLAGS     Flags,  
   IDebugDefaultPort2      pPort,  
   AD_PROCESS_ID           ProcessId,  
   CONST_GUID_ARRAY        EngineFilter,  
   PROVIDER_PROCESS_DATA[] pProcess  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `Flags`  
 [in] Eine Kombination von Flags aus der [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) Enumeration. Die folgenden Flags sind typisch für diesen Aufruf:  
  
|Flag|Beschreibung|  
|----------|-----------------|  
|`PFLAG_REMOTE_PORT`|Aufrufer wird auf dem Remotecomputer ausgeführt.|  
|`PFLAG_DEBUGGEE`|Aufrufer ist aktuell im Debugmodus befindlichen (Weitere Informationen über das marshalling von werden für jeden Knoten zurückgegeben werden).|  
|`PFLAG_ATTACHED_TO_DEBUGGEE`|Aufrufer wurde angefügt, aber nicht vom Debugger gestartet.|  
|`PFLAG_GET_PROGRAM_NODES`|Aufrufer werden eine Liste der programmknoten gefragt, zurückgegeben werden.|  
  
 `pPort`  
 [in] Der Port der aufrufende Prozess ausgeführt wird.  
  
 `processId`  
 [in] Ein [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) Struktur mit der betreffenden die ID des Prozesses, der das Programm enthält.  
  
 `EngineFilter`  
 [in] Ein Array von GUIDs für die Debug-Engines, die diesen Prozess zu debuggen (diese werden verwendet, Filtern die Programme, die tatsächlich zurückgegeben werden, basierend auf was die angegebenen Module unterstützen; Wenn keine Module angegeben werden, und klicken Sie dann alle Programme zurückgegeben werden) zugewiesen werden soll.  
  
 `pProcess`  
 [out] Ein [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) -Struktur, die mit den geforderten Informationen gefüllt wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird normalerweise durch einen Prozess zum Abrufen einer Liste der in diesem Prozess ausgeführte Programme aufgerufen. Die zurückgegebene Informationen ist eine Liste der [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) Objekte.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)   
 [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)

