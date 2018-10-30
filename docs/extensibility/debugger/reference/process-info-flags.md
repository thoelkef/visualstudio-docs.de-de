---
title: PROCESS_INFO_FLAGS | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 04bc34de6e7ecbc438cfc63ed08c684cf4224366
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49917023"
---
# <a name="processinfoflags"></a>PROCESS_INFO_FLAGS

Beschreibt, oder gibt die Eigenschaften eines Prozesses an.

## <a name="syntax"></a>Syntax

```cpp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
typedef DWORD PROCESS_INFO_FLAGS;
```

```csharp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
```

## <a name="members"></a>Member

PIFLAG_SYSTEM_PROCESS  
Gibt an, dass der Prozess ein Systemprozess ist.

PIFLAG_DEBUGGER_ATTACHED  
Gibt an, dass der Prozess von einem Debugger debuggt wird. Es ist möglicherweise eine [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Debugger, oder es möglicherweise einige andere Debugger, z. B. WinDbg.

PIFLAG_PROCESS_STOPPED  
Gibt an, dass der Prozess beendet wird. Nur gültig, wenn `PIFLAG_DEBUGGER_ATTACHED` ist ebenfalls angegeben. In Visual Studio 2005 und höher verfügbar.

PIFLAG_PROCESS_RUNNING  
Gibt an, dass der Prozess ausgeführt wird. Nur gültig, wenn `PIFLAG_DEBUGGER_ATTACHED` ist ebenfalls angegeben. In Visual Studio 2005 und höher verfügbar.

## <a name="remarks"></a>Hinweise

Verwendet für die `Flags` Mitglied der [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) Struktur.

Diese Flags können kombiniert werden, mit einer bitweisen `OR`.

## <a name="requirements"></a>Anforderungen

Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch

[Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)