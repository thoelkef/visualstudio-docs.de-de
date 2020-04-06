---
title: MACHINE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MACHINE_INFO
helpviewer_keywords:
- MACHINE_INFO structure
ms.assetid: e7564ff2-00b5-4750-8fd5-dc1029a16912
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad66992bd07afa2ef563c1b58fab0172e9a6121e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714556"
---
# <a name="machine_info"></a>MACHINE_INFO
Beschreibt einen bestimmten Computer.

## <a name="syntax"></a>Syntax

```cpp
typedef struct tagMACHINE_INFO { 
   MACHINE_INFO_FIELDS Fields;
   BSTR                bstrName;
   MACHINE_INFO_FLAGS  Flags;
} MACHINE_INFO;
```

```csharp
public struct MACHINE_INFO { 
   public uint   Fields;
   public string bstrName;
   public uint   Flags;
};
```

## <a name="members"></a>Member
 `Fields`\
 Eine Kombination von [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md) Flags aus der MACHINE_INFO_FIELDS-Enumeration, die angeben, welche Felder der Struktur initialisiert werden.

 `bstrName`\
 Der Computername Entspricht dem Aufruf von [GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md).

 `Flags`\
 Eine Kombination von [MACHINE_INFO_FLAGS](../../../extensibility/debugger/reference/machine-info-flags.md) Flags aus der MACHINE_INFO_FLAGS-Enumeration, die die Computerattribute beschreibt.

## <a name="remarks"></a>Bemerkungen
 Diese Struktur wird durch einen Aufruf der [GetMachineInfo-Methode](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) zurückgegeben.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)
- [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)
