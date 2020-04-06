---
title: IDebugProgramProvider2::GetProviderProgramNode | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
ms.assetid: e62e8e83-acbb-4c52-aedf-ffbd4670db29
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fd8ca7d5120ba20695caef2e9021ee25869df72f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721804"
---
# <a name="idebugprogramprovider2getproviderprogramnode"></a>IDebugProgramProvider2::GetProviderProgramNode
Ruft den Programmknoten für ein bestimmtes Programm ab.

## <a name="syntax"></a>Syntax

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

```csharp
int GetProviderProgramNode(
   enum_PROVIDER_FLAGS    Flags,
   IDebugDefaultPort2     pPort,
   AD_PROCESS_ID          ProcessId,
   ref Guid               guidEngine,
   ulong                  programId,
   out IDebugProgramNode2 ppProgramNode
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

`pPort`\
[in] Der Port, auf dem der Aufrufenprozess ausgeführt wird.

`processId`\
[in] Eine [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) Struktur mit der ID des Prozesses, der das betreffende Programm enthält.

`guidEngine`\
[in] GUID des Debugmoduls, an das das Programm angefügt ist (falls vorhanden).

`programId`\
[in] ID des Programms, für das der Programmknoten abgerufen werden soll.

`ppProgramNode`\
[out] Ein [IDebugProgramNode2-Objekt,](../../../extensibility/debugger/reference/idebugprogramnode2.md) das den angeforderten Programmknoten darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
