---
title: BP_FLAGS90 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef0844e4bf2c10128ee9c1a62669711e36eb401f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56682439"
---
# <a name="bpflags90"></a>BP_FLAGS90
Listet die gültigen Werte für optionale Kennzeichen. Die optionalen Kennzeichen können verwendet werden, um zusätzliche Informationen angeben, wenn Sie einen Haltepunkt festlegen. Diese Enumeration erweitert die [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) Enumeration.

## <a name="syntax"></a>Syntax

```cpp
enum enum_BP_FLAGS90
{
    // VS 8.0 values
    BP90_FLAG_NONE               = 0x0000,
    BP90_FLAG_MAP_DOCPOSITION    = 0x0001,
    BP90_FLAG_DONT_STOP          = 0x0002,

    // Values added in VS 9.0
    BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,
};
typedef DWORD BP_FLAGS90;
```

```csharp
public enum enum_BP_FLAGS90
{
    // VS 8.0 values
    BP90_FLAG_NONE                = 0x0000,
    BP90_FLAG_MAP_DOCPOSITION     = 0x0001,
    BP90_FLAG_DONT_STOP           = 0x0002,

    // Values added in VS 9.0
    BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,
};
```

#### <a name="parameters"></a>Parameter
BP90_FLAG_NONE gibt kein Flag Haltepunkt an.

BP90_FLAG_MAP_DOCPOSITION gibt an, dass den Haltepunkt mit die Dokumentposition die Debug-Engine (DE) zugeordnet werden sollen. Dies gilt nur für Haltepunkte, die in den Skript-orientierten Quelldateien wie z. B. Active Server Pages (ASP).

BP90_FLAG_DONT_STOP gibt an, die der Haltepunkt die Debug-Engine verarbeitet werden sollen, aber die Debug-Engine sollte nicht mehr vorhanden. d. h. eine [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) Ereignisobjekt nicht gesendet werden soll. Dieses Flag dient in erster Linie mit Punkten der Ablaufverfolgung verwendet werden.

BP90_FLAG_TRACEPOINT_CONTINUE wird von systemeigenen Debug-Engine zum bestimmen, ob es sich bei der schrittweisen Ausführung Zustand gelöscht werden sollen. Es unterscheidet sich von BP90_FLAG_DONT_STOP BP90_FLAG_DONT_STOP nicht festgelegt ist, wenn der Ablaufverfolgungspunkt ein Makro ausgeführt wird.

## <a name="requirements"></a>Anforderungen
Header: Msdbg90.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
