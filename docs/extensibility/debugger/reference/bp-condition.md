---
title: BP_CONDITION | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_CONDITION
helpviewer_keywords:
- BP_CONDITION structure
ms.assetid: 407f87a3-2878-429b-8c65-b68feb36622a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e20db594fcc00f641634bfaae8d5342d4b520d7f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337426"
---
# <a name="bpcondition"></a>BP_CONDITION
Beschreibt die Bedingungen, unter denen ein Haltepunkt ausgelöst wird.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _BP_CONDITION {
    IDebugThread2* pThread;
    BP_COND_STYLE  styleCondition;
    BSTR           bstrContext;
    BSTR           bstrCondition;
    UINT           nRadix;
} BP_CONDITION;
```

```csharp
public struct BP_CONDITION {
    public IDebugThread2 pThread;
    public uint          styleCondition;
    public string        bstrContext;
    public string        bstrCondition;
    public uint          nRadix;
};
```

## <a name="members"></a>Member
`pThread`\
Die [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) -Objekt, das den aktiven Thread für die Anwendung darstellt, die den Haltepunkt enthält.

`styleCondition`\
Ein Wert aus der [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md) Enumeration, der dieser Bedingung für Haltepunkt beschreibt.

`bstrContext`\
Die Position des Haltepunkts.

`bstrCondition`\
Die Bedingung der Auslösung des Haltepunkts.

`nRadix`\
Die Basis zum Auswerten von numerische Informationen verwendet werden.

## <a name="remarks"></a>Hinweise
Diese Struktur ist ein Mitglied der [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) und [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Strukturen.

Diese Struktur wird ebenfalls übergeben, als Parameter an die [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md) und [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md) Methoden.

## <a name="requirements"></a>Anforderungen
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)
- [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)
