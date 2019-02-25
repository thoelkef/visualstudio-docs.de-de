---
title: EXCEPTION_STATE | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EXCEPTION_STATE
helpviewer_keywords:
- EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a9c0c5ed3f4432deeb26e97ff21f6d89de9ee109
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56720314"
---
# <a name="exceptionstate"></a>EXCEPTION_STATE
Gibt den Ausnahmezustand.

## <a name="syntax"></a>Syntax

```cpp
enum enum_EXCEPTION_STATE {
    EXCEPTION_NONE                          = 0x0000,
    EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,
    EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,
    EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,
    EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,
    EXCEPTION_STOP_ALL                      = 0x00FF,
    EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,

    // These are for exception types only
    EXCEPTION_CODE_SUPPORTED                = 0x1000,
    EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,
    EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,
    EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,

    // These are no longer used
    EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,
    EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,
    EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,
    EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,
};
typedef DWORD EXCEPTION_STATE;
```

```csharp
public enum enum_EXCEPTION_STATE {
    EXCEPTION_NONE                          = 0x0000,
    EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,
    EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,
    EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,
    EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,
    EXCEPTION_STOP_ALL                      = 0x00FF,
    EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,

    // These are for exception types only
    EXCEPTION_CODE_SUPPORTED                = 0x1000,
    EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,
    EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,
    EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,

    // These are no longer used
    EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,
    EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,
    EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,
    EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,
};
```

## <a name="members"></a>Member
EXCEPTION_NONE beenden Sie nicht an der Ausnahme.

EXCEPTION_STOP_FIRST_CHANCE beenden am ersten Auslösen der Ausnahme. Wenn Sie einem Ausnahmeereignis zu beschreiben, gibt dieses Flag an, dass die Ausnahmeereignis ein Ereignis für die Ausnahme der ersten Chance ist.

EXCEPTION_STOP_SECOND_CHANCE beenden am zweiten Auslösung der Ausnahme. Wenn Sie einem Ausnahmeereignis beschreiben zu können, gibt an, dass das Ausnahmeereignis eine zweite Chance Ausnahmeereignisses.

EXCEPTION_STOP_USER_FIRST_CHANCE beenden am ersten Auslösen einer Ausnahme des User-Modus. Wenn Sie einem Ausnahmeereignis beschreiben zu können, gibt an, dass das Ausnahmeereignis ein Ereignis für nicht abgefangene Ausnahme.

EXCEPTION_STOP_USER_UNCAUGHT wird beendet, wenn eine Benutzer-Modus-Ausnahme nicht abgefangen wird. Wenn Sie einem Ausnahmeereignis beschreiben zu können, gibt an, dass das Ausnahmeereignis eine nicht abgefangene Benutzerereignis Modus Ausnahme.

EXCEPTION_STOP_ALL werden bei jeder Ausnahme beendet. Nicht verwendet, wenn Sie ein Ausnahmeereignis beschreiben.

EXCEPTION_CANNOT_BE_CONTINUED beim Beschreiben von einem Ausnahmeereignis, gibt Sie an, dass die Ausnahme von fortgesetzt werden, kann nicht.

EXCEPTION_CODE_SUPPORTED gibt an, dass die Ausnahme unterstützen Code verfügt. Bei der Anzeige einer Ausnahme verwendet

EXCEPTION_CODE_DISPLAY_IN_HEX gibt an, dass der Ausnahmecode im Hexadezimalformat angezeigt werden soll. Bei der Anzeige einer Ausnahme verwendet.

EXCEPTION_JUST_MY_CODE_SUPPORTED gibt an, dass der Ausnahmecode JustMyCode unterstützt. Bei der Anzeige einer Ausnahme verwendet.

EXCEPTION_MANAGED_DEBUG_ASSISTANT gibt an, dass der Debugger für verwalteten Code Ausnahmen verarbeiten soll. Wenn dies nicht festgelegt ist, der Standarddebugger behandelt die Ausnahmen. Diese wird zum Übergeben der [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) Methode und nicht in verwendet die [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) Struktur.

EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT VERALTET, VERWENDEN SIE NICHT.

EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT VERALTET, VERWENDEN SIE NICHT.

EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT VERALTET, VERWENDEN SIE NICHT.

EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT VERALTET, VERWENDEN SIE NICHT.

## <a name="remarks"></a>Hinweise
Verwendet als die `dwState` Mitglied der [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) Struktur geben den Zustand der Ausnahme und wozu dazu verwendet werden können.

Diese Werte werden auch zum Übergeben der [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) Methode zum Festlegen des Status für alle Ausnahmen.

Diese Flags können mit einem bitweisen OR kombiniert werden.

## <a name="requirements"></a>Anforderungen
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)
