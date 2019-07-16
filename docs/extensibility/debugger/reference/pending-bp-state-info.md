---
title: PENDING_BP_STATE_INFO | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PENDING_BP_STATE_INFO
helpviewer_keywords:
- PENDING_BP_STATE_INFO structure
ms.assetid: 4d73ceff-43f9-4e95-8dba-88e1fab2def3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 306f3f6ac5f12d2a26da958d50fae87c6e174355
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349881"
---
# <a name="pendingbpstateinfo"></a>PENDING_BP_STATE_INFO
Enthält Informationen über den Zustand eines Haltepunkts an, die an einen Speicherort gebunden werden kann.

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
 Ein Wert aus der [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md) -Enumeration, die den Status des ausstehenden Haltepunkts angibt.

 `flags`\
 Eine Kombination von Flags aus der [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md) -Enumeration, der angibt, ob der Breakpoint virtualisiert wird.

## <a name="remarks"></a>Hinweise
 Diese Struktur wird zum Übergeben der [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md) Methode, in denen es ausgefüllt wird.

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)
- [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md)
- [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md)