---
title: CANSTOP_REASON | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CANSTOP_REASON
helpviewer_keywords:
- CANSTOP_REASON enumeration
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 18861d7aa19281528e9a100f57399451194598a9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66327249"
---
# <a name="canstopreason"></a>CANSTOP_REASON
Verwendet, um zu bestimmen, ob ein Programm nach Erreichen einer bestimmten Stelle in der Ausführung beenden kann.

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
Gibt an, eine Funktion schrittweise.

## <a name="remarks"></a>Hinweise
Übergeben als Argument an die [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) Methode, mit der Sitzung Debug-Manager (SDM) zu bestätigen, wenn nach dem Erreichen des Einstiegspunkt des Programms oder nach einer Funktion oder Methode schrittweise beendet werden kann.

## <a name="requirements"></a>Anforderungen
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
