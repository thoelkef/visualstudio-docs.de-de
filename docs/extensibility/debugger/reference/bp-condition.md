---
title: BP_CONDITION | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_CONDITION
helpviewer_keywords:
- BP_CONDITION structure
ms.assetid: 407f87a3-2878-429b-8c65-b68feb36622a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 88ed6b6468c5765c8f987c1f15f3e4e8ade9c8c6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738104"
---
# <a name="bp_condition"></a>BP_CONDITION
Beschreibt die Bedingungen, unter denen ein Breakpoint ausgelöst wird.

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
Das [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) -Objekt, das den aktiven Thread für die Anwendung darstellt, die den Breakpoint enthält.

`styleCondition`\
Ein Wert aus der [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md) Enumeration, die den Stil dieser Haltepunkt Bedingung beschreibt.

`bstrContext`\
Der Speicherort des Breakpoints.

`bstrCondition`\
Die Auslöserbedingung des Breakpoints.

`nRadix`\
Radix, das bei der Auswertung numerischer Informationen verwendet werden soll.

## <a name="remarks"></a>Bemerkungen
Diese Struktur ist ein Member der [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) -und [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) -Strukturen.

Diese Struktur wird auch als Parameter an die [setcondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md) -Methode und die [setcondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md) -Methode übergeben.

## <a name="requirements"></a>Anforderungen
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)
- [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)
