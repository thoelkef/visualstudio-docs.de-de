---
title: BP_FLAGS | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_FLAGS
helpviewer_keywords:
- BP_FLAGS enumeration
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 31f5153c3a2d0b55829a7743840fe8a791f023d0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319221"
---
# <a name="bpflags"></a>BP_FLAGS
Bietet optionale Kennzeichen, die verwendet werden können, um zusätzliche Informationen angeben, wenn Sie einen Haltepunkt festlegen.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BP_FLAGS {
    BP_FLAG_NONE            = 0x0000,
    BP_FLAG_MAP_DOCPOSITION = 0x0001,
    BP_FLAG_DONT_STOP       = 0x0002
};
typedef DWORD BP_FLAGS;
```

```csharp
public enum enum_BP_FLAGS {
    BP_FLAG_NONE            = 0x0000,
    BP_FLAG_MAP_DOCPOSITION = 0x0001,
    BP_FLAG_DONT_STOP       = 0x0002
};
```

## <a name="fields"></a>Felder
`BP_FLAG_NONE`\
Gibt kein Flag Haltepunkt an.

`BP_FLAG_MAP_DOCPOSITION`\
Gibt an, der den Haltepunkt, der die Dokumentposition mithilfe die Debug-Engine (DE) zugeordnet werden sollen. Dies gilt nur für Haltepunkte, die in den Skript-orientierten Quelldateien wie z. B. Active Server Pages (ASP).

`BP_FLAG_DONT_STOP`\
Gibt an, dass der Haltepunkt von der Debug-Engine verarbeitet werden sollen, aber die Debug-Engine letztlich nicht es beendet werden soll (d. h. eine [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) Ereignisobjekt sollte nicht gesendet werden). Dieses Flag dient in erster Linie mit Ablaufverfolgungspunkten verwendet werden.

## <a name="remarks"></a>Hinweise
Verwendet für die `dwFlags` Mitglied der [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) und [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Strukturen.

Diese Werte können kombiniert werden, mit einer bitweisen `OR`.

## <a name="requirements"></a>Anforderungen
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
