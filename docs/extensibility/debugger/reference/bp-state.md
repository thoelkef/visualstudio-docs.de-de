---
title: BP_STATE | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_STATE
helpviewer_keywords:
- BP_STATE enumeration
ms.assetid: 08aa6a3f-3e5f-4c83-8eca-7b7b5f8e208d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4117b3cb92eef555d5ed9a6c3e829fb3302924ae
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56709251"
---
# <a name="bpstate"></a>BP_STATE
Gibt an, ob einen gebundenen Haltepunkt vorhanden ist, und gibt auch an, wenn es aktiviert ist.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BP_STATE {
    BPS_NONE     = 0x0000,
    BPS_DELETED  = 0x0001,
    BPS_DISABLED = 0x0002,
    BPS_ENABLED  = 0x0003
};
typedef DWORD BP_STATE;
```

```csharp
public enum enum_BP_STATE {
    BPS_NONE     = 0x0000,
    BPS_DELETED  = 0x0001,
    BPS_DISABLED = 0x0002,
    BPS_ENABLED  = 0x0003
};
```

## <a name="members"></a>Member
BPS_NONE gibt an, die kein Haltepunkt vorhanden ist.

BPS_DELETED gibt an, dass der Haltepunkt gelöscht wurde.

BPS_DISABLED gibt an, dass der Haltepunkt deaktiviert ist.

BPS_ENABLED gibt an, dass der Breakpoint aktiviert ist.

## <a name="remarks"></a>Hinweise
Zurückgegeben von der [GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md) Methode.

## <a name="requirements"></a>Anforderungen
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)
