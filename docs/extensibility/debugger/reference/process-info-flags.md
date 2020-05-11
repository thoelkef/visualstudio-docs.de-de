---
title: PROCESS_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 36c4cbbe17a109eacd69b76500e8c10d21d2d554
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713964"
---
# <a name="process_info_flags"></a>PROCESS_INFO_FLAGS

Beschreibt oder gibt Eigenschaften eines Prozesses an.

## <a name="syntax"></a>Syntax

```cpp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
typedef DWORD PROCESS_INFO_FLAGS;
```

```csharp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
```

## <a name="fields"></a>Felder

`PIFLAG_SYSTEM_PROCESS`\
Gibt an, dass es sich bei dem Prozess um einen Systemprozess handelt.

`PIFLAG_DEBUGGER_ATTACHED`\
Gibt an, dass der Prozess von einem Debugger gedebugft wird. Es kann [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] sich um einen Debugger oder um einen anderen Debugger, z. B. WinDbg, handelt.

`PIFLAG_PROCESS_STOPPED`\
Gibt an, dass der Prozess angehalten wurde. Gültig nur, wenn `PIFLAG_DEBUGGER_ATTACHED` ebenfalls angegeben ist. Verfügbar in Visual Studio 2005 und höher.

`PIFLAG_PROCESS_RUNNING`\
Gibt an, dass der Prozess ausgeführt wird. Gültig nur, wenn `PIFLAG_DEBUGGER_ATTACHED` ebenfalls angegeben ist. Verfügbar in Visual Studio 2005 und höher.

## <a name="remarks"></a>Bemerkungen

Wird für `Flags` das Element der [PROCESS_INFO-Struktur](../../../extensibility/debugger/reference/process-info.md) verwendet.

Diese Flags können mit einem `OR`bitwise kombiniert werden.

## <a name="requirements"></a>Requirements (Anforderungen)

Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen

- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
