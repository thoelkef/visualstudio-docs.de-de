---
title: PENDING_BP_STATE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PENDING_BP_STATE_INFO
helpviewer_keywords:
- PENDING_BP_STATE_INFO structure
ms.assetid: 4d73ceff-43f9-4e95-8dba-88e1fab2def3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d66ecc63e133a75148f06b59b8f1ccf61fe2658d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714078"
---
# <a name="pending_bp_state_info"></a>PENDING_BP_STATE_INFO
Enthält Informationen über den Status eines Haltepunkts, der an einen Codespeicherort gebunden werden kann.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagPENDING_BP_STATE_INFO { 
   PENDING_BP_STATE       state;
   PENDING_BP_STATE_FLAGS flags;
} PENDING_BP_STATE_INFO;
```

```csharp
public struct PENDING_BP_STATE_INFO { 
   public uint state;
   public uint flags;
};
```

## <a name="members"></a>Member
 `state`\
 Ein Wert [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md) aus der PENDING_BP_STATE-Enumeration, der den Status des ausstehenden Haltepunkts angibt.

 `flags`\
 Eine Kombination von [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md) Flags aus der PENDING_BP_STATE_FLAGS-Enumeration, die angibt, ob der Haltepunkt virtualisiert ist.

## <a name="remarks"></a>Bemerkungen
 Diese Struktur wird an die [GetState-Methode](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md) übergeben, wo sie ausgefüllt wird.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)
- [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md)
- [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md)
