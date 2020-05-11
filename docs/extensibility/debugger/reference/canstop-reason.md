---
title: CANSTOP_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CANSTOP_REASON
helpviewer_keywords:
- CANSTOP_REASON enumeration
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d7be361d4468584c109db52f487b3de3c1fdff0a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737684"
---
# <a name="canstop_reason"></a>CANSTOP_REASON
Wird verwendet, um zu bestimmen, ob ein Programm die Ausführung beenden kann, nachdem es einen bestimmten Punkt in der Ausführung erreicht hat.

## <a name="syntax"></a>Syntax

```cpp
enum enum_CANSTOP_REASON {
    CANSTOP_ENTRYPOINT = 0x0000,
    CANSTOP_STEPIN     = 0x0001
};
typedef DWORD CANSTOP_REASON;
```

```csharp
public enum enum_CANSTOP_REASON {
    CANSTOP_ENTRYPOINT = 0x0000,
    CANSTOP_STEPIN     = 0x0001
};
```

## <a name="fields"></a>Felder
`CANSTOP_ENTRYPOINT`\
Gibt den Einstiegspunkt des angegebenen Programms an.

`CANSTOP_STEPIN`\
Gibt den Einstieg in eine Funktion an.

## <a name="remarks"></a>Bemerkungen
Übergeben als Argument an die [GetReason-Methode,](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) um mit dem Session Debug Manager (SDM) zu bestätigen, ob es in Ordnung ist, nach Erreichen des Einstiegspunkts des Programms oder nach dem Eintreten in eine Funktion oder Methode zu stoppen.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
