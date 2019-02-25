---
title: CONTEXT_COMPARE | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_COMPARE
helpviewer_keywords:
- CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 21628bda9dc0437672b0b755bb64f1c882b0acbf
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689173"
---
# <a name="contextcompare"></a>CONTEXT_COMPARE
Gibt die Kriterien zum Vergleichen von zwei Speicher Kontexten.

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

## <a name="members"></a>Member
CONTEXT_EQUAL ermittelt die erste Speicherkontext in der Liste, die den Arbeitsspeicher Zielkontext entspricht.

CONTEXT_LESS_THAN ermittelt die erste Speicherkontext in der Liste, die kleiner als den Zielkontext der Arbeitsspeicher ist.

CONTEXT_GREATER_THAN Suchen der ersten Arbeitsspeicher-Kontext, in der Liste, die den Zielkontext der Arbeitsspeicher größer ist.

CONTEXT_LESS_THAN_OR_EQUAL ermittelt die erste Speicherkontext in der Liste, die kleiner als oder gleich den Zielkontext der Arbeitsspeicher ist.

CONTEXT_GREATER_THAN_OR_EQUAL ermittelt die erste Speicherkontext in der Liste, die größer als oder gleich den Zielkontext der Arbeitsspeicher ist.

CONTEXT_SAME_SCOPE ermittelt die erste Speicherkontext in der Liste, die im gleichen Bereich wie den Zielkontext der Arbeitsspeicher ist.

CONTEXT_SAME_FUNCTION ermittelt den Speicherkontext für ersten in der Liste, die in die gleiche Funktion wie der Zielbereich für den Arbeitsspeicher ist.

CONTEXT_SAME_MODULE ermittelt die erste Speicherkontext in der Liste, die im selben Modul wie den Zielkontext der Arbeitsspeicher ist.

CONTEXT_SAME_PROCESS ermittelt die erste Speicherkontext in der Liste, die in demselben Prozess wie den Zielkontext der Arbeitsspeicher ist.

## <a name="remarks"></a>Hinweise
Übergeben als Argument an die [vergleichen](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md) Methode.

Diese Werte werden zum ersten Arbeitsspeicher Kontext in einer Liste zu suchen, die die angegebenen Vergleichskriterien entspricht. Ein Kontext an Arbeitsspeicher erhält eine Liste von Kontexten, Speicher selbst vor über vergleichen die `IDebugMemoryContext2::Compare` Methode. Die erste Arbeitsspeicher-Kontext, in der Liste, die für die der Vergleichsoperator ist `true` wird zurückgegeben.

## <a name="requirements"></a>Anforderungen
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)
