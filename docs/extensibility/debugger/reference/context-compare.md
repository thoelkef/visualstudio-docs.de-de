---
title: CONTEXT_COMPARE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_COMPARE
helpviewer_keywords:
- CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1c88b50644d1adda2dd0eaa3b74a828f9739d70b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737604"
---
# <a name="context_compare"></a>CONTEXT_COMPARE
Gibt die Kriterien für den Vergleich von zwei Speicherkontexten an.

## <a name="syntax"></a>Syntax

```cpp
enum enum_CONTEXT_COMPARE {
    CONTEXT_EQUAL                 = 0x0001,
    CONTEXT_LESS_THAN             = 0x0002,
    CONTEXT_GREATER_THAN          = 0x0003,
    CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,
    CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,
    CONTEXT_SAME_SCOPE            = 0x0006,
    CONTEXT_SAME_FUNCTION         = 0x0007,
    CONTEXT_SAME_MODULE           = 0x0008,
    CONTEXT_SAME_PROCESS          = 0x0009
};
typedef DWORD CONTEXT_COMPARE;
```

```csharp
public enum enum_CONTEXT_COMPARE {
    CONTEXT_EQUAL                 = 0x0001,
    CONTEXT_LESS_THAN             = 0x0002,
    CONTEXT_GREATER_THAN          = 0x0003,
    CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,
    CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,
    CONTEXT_SAME_SCOPE            = 0x0006,
    CONTEXT_SAME_FUNCTION         = 0x0007,
    CONTEXT_SAME_MODULE           = 0x0008,
    CONTEXT_SAME_PROCESS          = 0x0009
};
```

## <a name="fields"></a>Felder
`CONTEXT_EQUAL`\
Suchen Sie den ersten Speicherkontext in der Liste, der dem Zielspeicherkontext entspricht.

`CONTEXT_LESS_THAN`\
Suchen Sie den ersten Speicherkontext in der Liste, der kleiner als der Zielspeicherkontext ist.

`CONTEXT_GREATER_THAN`\
Suchen Sie den ersten Speicherkontext in der Liste, der größer als der Zielspeicherkontext ist.

`CONTEXT_LESS_THAN_OR_EQUAL`\
Suchen Sie den ersten Speicherkontext in der Liste, der kleiner oder gleich dem Zielspeicherkontext ist.

`CONTEXT_GREATER_THAN_OR_EQUAL`\
Suchen Sie den ersten Speicherkontext in der Liste, der größer oder gleich dem Zielspeicherkontext ist.

`CONTEXT_SAME_SCOPE`\
Suchen Sie den ersten Speicherkontext in der Liste, der sich im gleichen Bereich wie der Zielspeicherkontext befindet.

`CONTEXT_SAME_FUNCTION`\
Suchen Sie den ersten Speicherkontext in der Liste, der sich in derselben Funktion wie der Zielspeicherbereich befindet.

`CONTEXT_SAME_MODULE`\
Suchen Sie den ersten Speicherkontext in der Liste, der sich im selben Modul wie der Zielspeicherkontext befindet.

`CONTEXT_SAME_PROCESS`\
Suchen Sie den ersten Speicherkontext in der Liste, der sich im gleichen Prozess wie der Zielspeicherkontext befindet.

## <a name="remarks"></a>Bemerkungen
Übergeben als Argument [Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md) an die Compare-Methode.

Diese Werte werden verwendet, um den ersten Speicherkontext in einer Liste zu finden, die die angegebenen Vergleichskriterien erfüllt. Einem Speicherkontext wird eine Liste von Speicherkontexten `IDebugMemoryContext2::Compare` gegeben, mit denen er sich durch die Methode vergleichen kann. Der erste Speicherkontext in der Liste, `true` für den der Vergleichsoperator angezeigt wird, wird zurückgegeben.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Vergleichen](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)
