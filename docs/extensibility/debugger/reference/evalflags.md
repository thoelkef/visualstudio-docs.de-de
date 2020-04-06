---
title: EVALFLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVALFLAGS
helpviewer_keywords:
- EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4136726e5c8b798121dbd38975d8f2bb935ed04a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737111"
---
# <a name="evalflags"></a>EVALFLAGS
Gibt Flags an, die die Ausdruckauswertung steuern.

## <a name="syntax"></a>Syntax

```cpp
enum enum_EVALFLAGS {
    EVAL_RETURNVALUE = 0x0002,
    EVAL_NOSIDEEFFECTS = 0x0004,
    EVAL_ALLOWBPS = 0x0008,
    EVAL_ALLOWERRORREPORT = 0x0010,
    EVAL_FUNCTION_AS_ADDRESS = 0x0040,
    EVAL_NOFUNCEVAL = 0x0080,
    EVAL_NOEVENTS = 0x1000
};
typedef DWORD EVALFLAGS;
```

```csharp
public enum enum_EVALFLAGS {
    EVAL_RETURNVALUE = 0x0002,
    EVAL_NOSIDEEFFECTS = 0x0004,
    EVAL_ALLOWBPS = 0x0008,
    EVAL_ALLOWERRORREPORT = 0x0010,
    EVAL_FUNCTION_AS_ADDRESS = 0x0040,
    EVAL_NOFUNCEVAL = 0x0080,
    EVAL_NOEVENTS = 0x1000
}
```

## <a name="fields"></a>Felder
`EVAL_RETURNVALUE`\
Gibt an, dass der Rückgabewert, falls vorhanden, ausgewertet wird.

`EVAL_NOSIDEEFFECTS`\
Gibt an, dass Nebenwirkungen nicht zugelassen werden.

`EVAL_ALLOWBPS`\
Gibt das Beenden von Haltepunkten an.

`EVAL_ALLOWERRORREPORT`\
Gibt die Fehlerberichterstattung an den Host an, um zugelassen zu werden. Hauptsächlich für die Ausdrucksauswertung im Skript in Internet Explorer verwendet.

`EVAL_FUNCTION_AS_ADDRESS`\
Erzwingt, dass Funktionen als Adressen ausgewertet werden, anstatt die Funktion aufzuberufen.

`EVAL_NOFUNCEVAL`\
Verhindert, dass die Funktion ausgewertet wird. Betrachten Sie beispielsweise `int` das Token `myExpression(int) + 10`im Ausdruck . Diese Funktion kann korrekt als Adresse ausgewertet werden, jedoch nicht als Wert.

`EVAL_NOEVENTS`\
Flag, um anzugeben, dass Ereignisse, die während der Ausdrucksauswertung auftreten, nicht an den Sitzungsdebug-Manager (SDM) oder an die IDE gesendet werden sollen.

## <a name="remarks"></a>Bemerkungen
Diese Flags werden als Argument an die [EvaluateAsync-](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) und [EvaluateSync-Methoden](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) übergeben.

Diese Flags können mit einem bitweisen ODER kombiniert werden.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
