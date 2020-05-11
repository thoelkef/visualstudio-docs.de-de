---
title: BP_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_FLAGS
helpviewer_keywords:
- BP_FLAGS enumeration
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 62626ff75a4545d89835d3136649191004291f8f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738060"
---
# <a name="bp_flags"></a>BP_FLAGS
Stellt optionale Flags bereit, die verwendet werden können, um zusätzliche Informationen beim Festlegen eines Haltepunkts anzugeben.

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
Gibt kein Haltepunktflag an.

`BP_FLAG_MAP_DOCPOSITION`\
Gibt an, dass das Debugmodul (DE) den Haltepunkt mithilfe der Dokumentposition zuordnen soll. Dies gilt nur für Haltepunkte, die in skriptorientierten Quelldateien wie Active Server Pages (ASP) festgelegt sind.

`BP_FLAG_DONT_STOP`\
Gibt an, dass der Haltepunkt vom Debugmodul verarbeitet werden soll, dass das Debugmodul jedoch nicht dort anhalten sollte (d. h. ein [IDebugBreakpointEvent2-Ereignisobjekt](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) sollte nicht gesendet werden). Dieses Flag ist in erster Linie für Tracepoints konzipiert.

## <a name="remarks"></a>Bemerkungen
Wird für `dwFlags` das Mitglied der [BP_REQUEST_INFO-](../../../extensibility/debugger/reference/bp-request-info.md) und [BP_REQUEST_INFO2-Strukturen](../../../extensibility/debugger/reference/bp-request-info2.md) verwendet.

Diese Werte können mit einer `OR`bitweisen Kombination kombiniert werden.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
