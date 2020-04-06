---
title: PROVIDER_PROCESS_DATA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROVIDER_PROCESS_DATA
helpviewer_keywords:
- PROVIDER_PROCESS_DATA structure
ms.assetid: ec2362ed-4a0c-4a09-9d66-8ff04e4f41ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bdaf15d09af3199d026155cf7667f063f5bbe858
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713782"
---
# <a name="provider_process_data"></a>PROVIDER_PROCESS_DATA
Diese Struktur enthält Informationen zu Prozessen, die auf einem Computer ausgeführt werden.

## <a name="syntax"></a>Syntax

```cpp
typedef struct tagPROVIDER_PROCESS_DATA {
   PROVIDER_FIELDS    Fields;
   PROGRAM_NODE_ARRAY ProgramNodes;
   BOOL               fIsDebuggerPresent;
} PROVIDER_PROCESS_DATA;
```

```csharp
public struct PROVIDER_PROCESS_DATA {
   public uint               Fields;
   public PROGRAM_NODE_ARRAY ProgramNodes;
   public int                fIsDebuggerPresent;
}
```

## <a name="members"></a>Member
 `Fields`\
 Eine Kombination von [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md) Flags aus der PROVIDER_FIELDS-Enumeration, die angibt, welche Felder ausgefüllt werden.

 `ProgramNodes`\
 Eine [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) Struktur, die ein Array von Programmknoten enthält.

 `fIsDebuggerPresent`\
 Ein Wert`TRUE`ungleich [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Null ( ),`FALSE`wenn der Debugger ausgeführt wird, Null ( ), wenn dies nicht der Fall ist.

## <a name="remarks"></a>Bemerkungen
 Diese Struktur wird an die [GetProviderProcessData-Methode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) übergeben, bei der sie ausgefüllt wird.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)
- [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
