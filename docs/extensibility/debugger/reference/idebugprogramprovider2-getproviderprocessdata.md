---
title: IDebugProgramProvider2::GetProviderProcessData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProcessData
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProcessData
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4e958900307f5f7915f58679709c88f80c2abfc9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721855"
---
# <a name="idebugprogramprovider2getproviderprocessdata"></a>IDebugProgramProvider2::GetProviderProcessData
Ruft eine Liste der ausgeführten Programme aus einem angegebenen Prozess ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetProviderProcessData(
   PROVIDER_FLAGS         Flags,
   IDebugDefaultPort2*    pPort,
   AD_PROCESS_ID          processId,
   CONST_GUID_ARRAY       EngineFilter,
   PROVIDER_PROCESS_DATA* pProcess
);
```

```csharp
int GetProviderProcessData(
   enum_PROVIDER_FLAGS     Flags,
   IDebugDefaultPort2      pPort,
   AD_PROCESS_ID           ProcessId,
   CONST_GUID_ARRAY        EngineFilter,
   PROVIDER_PROCESS_DATA[] pProcess
);
```

## <a name="parameters"></a>Parameter
`Flags`\
[in] Eine Kombination von [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) Flags aus der PROVIDER_FLAGS-Enumeration. Die folgenden Flags sind typisch für diesen Aufruf:

|Flag|BESCHREIBUNG|
|----------|-----------------|
|`PFLAG_REMOTE_PORT`|Der Anrufer wird auf dem Remotecomputer ausgeführt.|
|`PFLAG_DEBUGGEE`|Der Aufrufer wird derzeit gedebuggt (zusätzliche Informationen zum Marshalling werden für jeden Knoten zurückgegeben).|
|`PFLAG_ATTACHED_TO_DEBUGGEE`|Der Aufrufer wurde an den Debugger angefügt, aber nicht gestartet.|
|`PFLAG_GET_PROGRAM_NODES`|Der Anrufer fordert die Rückgabe einer Liste der Programmknoten.|

`pPort`\
[in] Der Port, auf dem der Aufrufenprozess ausgeführt wird.

`processId`\
[in] Eine [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) Struktur mit der ID des Prozesses, der das betreffende Programm enthält.

`EngineFilter`\
[in] Ein Array von GUIDs für Debug-Engines, die diesem Prozess zugewiesen sind (diese werden verwendet, um die Programme zu filtern, die tatsächlich zurückgegeben werden, basierend auf dem, was die bereitgestellten Module unterstützen; wenn keine Module angegeben sind, werden alle Programme zurückgegeben).

`pProcess`\
[out] Eine [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) Struktur, die mit den angeforderten Informationen ausgefüllt wird.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode wird normalerweise von einem Prozess aufgerufen, um eine Liste der in diesem Prozess ausgeführten Programme abzuerhalten. Die zurückgegebenen Informationen sind eine Liste von [IDebugProgramNode2-Objekten.](../../../extensibility/debugger/reference/idebugprogramnode2.md)

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
