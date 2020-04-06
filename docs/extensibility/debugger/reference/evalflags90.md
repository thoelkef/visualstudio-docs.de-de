---
title: EVALFLAGS90 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- EVALFLAGS90 enumeration
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 01951885541ba4acce33f3e4f06f7106116ccc62
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737104"
---
# <a name="evalflags90"></a>EVALFLAGS90
Zählt die gültigen Werte für Flags auf, die die Ausdrucksauswertung steuern. Diese Enumeration erweitert die EVALFLAGS-Enumeration. [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)

## <a name="syntax"></a>Syntax

```cpp
enum enum_EVALFLAGS90
{
    // VS 8.0 values
    EVAL90_RETURNVALUE                 = 0x0002,
    EVAL90_NOSIDEEFFECTS               = 0x0004,
    EVAL90_ALLOWBPS                    = 0x0008,
    EVAL90_ALLOWERRORREPORT            = 0x0010,
    EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,
    EVAL90_NOFUNCEVAL                  = 0x0080,
    EVAL90_NOEVENTS                    = 0x1000,
    EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,
    EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,

    // Values added in VS 9.0
    EVAL90_FORCE_EVALUATION_NOW        = 0x8000
};
typedef DWORD EVALFLAGS90;
```

```csharp
public enum enum_EVALFLAGS90
{
    // VS 8.0 values
    EVAL90_RETURNVALUE                 = 0x0002,
    EVAL90_NOSIDEEFFECTS               = 0x0004,
    EVAL90_ALLOWBPS                    = 0x0008,
    EVAL90_ALLOWERRORREPORT            = 0x0010,
    EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,
    EVAL90_NOFUNCEVAL                  = 0x0080,
    EVAL90_NOEVENTS                    = 0x1000,
    EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,
    EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,

    // Values added in VS 9.0
    EVAL90_FORCE_EVALUATION_NOW        = 0x8000
};
```

## <a name="fields"></a>Felder
`EVAL90_RETURNVALUE`\
Gibt an, dass der Rückgabewert, falls vorhanden, ausgewertet wird.

`EVAL90_NOSIDEEFFECTS`\
Gibt an, dass Nebenwirkungen nicht zugelassen werden.

`EVAL90_ALLOWBPS`\
Gibt das Beenden von Haltepunkten an.

`EVAL90_ALLOWERRORREPORT`\
Gibt an, dass die Fehlerberichterstattung an den Host zulässig ist. Hauptsächlich für die Ausdrucksauswertung im Skript in Internet Explorer verwendet.

`EVAL90_FUNCTION_AS_ADDRESS`\
Erzwingt, dass Funktionen als Adressen ausgewertet werden, anstatt die Funktion aufzuberufen.

`EVAL90_NOFUNCEVAL`\
Verhindert, dass die Funktion ausgewertet wird. Betrachten Sie beispielsweise `int` das Token `myExpression(int) + 10`im Ausdruck . Diese Funktion kann korrekt als Adresse ausgewertet werden, jedoch nicht als Wert.

`EVAL90_NOEVENTS`\
Flag, um anzugeben, dass Ereignisse, die während der Ausdrucksauswertung auftreten, nicht an den Sitzungsdebug-Manager (SDM) oder an die IDE gesendet werden sollen.

`EVAL90_DESIGN_TIME_EXPR_EVAL`\
Ermöglicht die Auswerteung von Entwurfszeitausdrucks.

`EVAL90_ALLOW_IMPLICIT_VARS`\
Ermöglicht die implizite Variablenerstellung.

`EVAL90_FORCE_EVALUATION_NOW`\
Erzwingt die sofortige Auswertung. Dies ist nützlich, wenn Sie eine Anforderung warten, z. B. eine Benutzeranforderung.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: Msdbg90.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
