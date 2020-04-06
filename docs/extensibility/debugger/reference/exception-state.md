---
title: EXCEPTION_STATE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EXCEPTION_STATE
helpviewer_keywords:
- EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cd2e280cd03ae413e0853950d13fbfefb69bc15f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736960"
---
# <a name="exception_state"></a>EXCEPTION_STATE
Gibt den Ausnahmestatus an.

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

## <a name="fields"></a>Felder
`EXCEPTION_NONE`\
Beenden Sie nicht die Ausnahme.

`EXCEPTION_STOP_FIRST_CHANCE`\
Beenden Sie beim ersten Auslösen der Ausnahme. Beim Beschreiben eines Ausnahmeereignisses gibt dieses Flag an, dass es sich bei dem Ausnahmeereignis um ein Ausnahmeereignis der ersten Chance handelt.

`EXCEPTION_STOP_SECOND_CHANCE`\
Stoppen Sie beim zweiten Auslösen der Ausnahme. Wenn Sie ein Ausnahmeereignis beschreiben, gibt dies an, dass das Ausnahmeereignis ein Ausnahmeereignis der zweiten Chance ist.

`EXCEPTION_STOP_USER_FIRST_CHANCE`\
Beenden Sie beim ersten Auslösen einer Benutzermodusausnahme. Wenn Sie ein Ausnahmeereignis beschreiben, gibt dies an, dass das Ausnahmeereignis ein Benutzerausnahmeereignis der ersten Chance ist.

`EXCEPTION_STOP_USER_UNCAUGHT`\
Beenden, wenn eine Benutzermodusausnahme nicht abgefangen wird. Wenn Sie ein Ausnahmeereignis beschreiben, gibt dies an, dass es sich bei dem Ausnahmeereignis um ein Nicht abgefangenes Ausnahmeereignis im Benutzermodus handelt.

`EXCEPTION_STOP_ALL`\
Beenden Sie bei jeder Ausnahme. Wird nicht verwendet, wenn ein Ausnahmeereignis beschrieben wird.

`EXCEPTION_CANNOT_BE_CONTINUED`\
Wenn Sie ein Ausnahmeereignis beschreiben, gibt dies an, dass die Ausnahme nicht fortgesetzt werden kann.

`EXCEPTION_CODE_SUPPORTED`\
Gibt an, dass die Ausnahme Code unterstützt. Wird beim Anzeigen einer Ausnahme verwendet

`EXCEPTION_CODE_DISPLAY_IN_HEX`\
Gibt an, dass der Ausnahmecode in hexadezimal angezeigt werden soll. Wird zum Anzeigen einer Ausnahme verwendet.

`EXCEPTION_JUST_MY_CODE_SUPPORTED`\
Gibt an, dass der Ausnahmecode JustMyCode unterstützt. Wird zum Anzeigen einer Ausnahme verwendet.

`EXCEPTION_MANAGED_DEBUG_ASSISTANT`\
Gibt an, dass der Debugger für verwalteten Code Ausnahmen behandeln soll. Wenn nicht festgelegt, behandelt der Standarddebugger die Ausnahmen. Dies wird an die [SetAllExceptions-Methode](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) übergeben und nicht in der [EXCEPTION_INFO-Struktur](../../../extensibility/debugger/reference/exception-info.md) verwendet.

`EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT`\
VERALTET, NICHT VERWENDEN.

`EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT`\
VERALTET, NICHT VERWENDEN.

`EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT`\
VERALTET, NICHT VERWENDEN.

`EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT`\
VERALTET, NICHT VERWENDEN.

## <a name="remarks"></a>Bemerkungen
Wird als `dwState` Member der [EXCEPTION_INFO-Struktur](../../../extensibility/debugger/reference/exception-info.md) verwendet, um den Zustand der Ausnahme anzugeben und anzugeben, was dagegen getan werden kann.

Diese Werte werden auch an die [SetAllExceptions-Methode](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) übergeben, um den Status aller Ausnahmen festzulegen.

Diese Flags können mit einem bitweisen ODER kombiniert werden.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)
