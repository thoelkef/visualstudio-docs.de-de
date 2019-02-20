---
title: DUMPTYPE | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DUMPTYPE
helpviewer_keywords:
- DUMPTYPE enumeration
ms.assetid: ea8160db-8732-4056-a1d7-892ef72da71e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c81d9c9f3f5dc6b0a849e405133b7ecef1e4e59b
ms.sourcegitcommit: 7153e2fc717d32e0e9c8a9b8c406dc4053c9fd53
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "56412967"
---
# <a name="dumptype"></a>DUMPTYPE
Gibt an, welcher Teil eines Programms Zustand (z. B. ausgeführten Threads, Stapelrahmen und aktuelle Anweisungsadresse) sichern.

## <a name="syntax"></a>Syntax

```cpp
enum enum_DUMPTYPE {
    DUMP_MINIDUMP = 0,
    DUMP_FULLDUMP = 1
};
typedef DWORD DUMPTYPE;
```

```csharp
public enum enum_DUMPTYPE {
    DUMP_MINIDUMP = 0,
    DUMP_FULLDUMP = 1
};
```

## <a name="members"></a>Member
DUMP_MINIDUMP  
Gibt einen kleinen, compact-Dump an.

DUMP_FULLDUMP  
Gibt einen großen, vollständigen Dump an.

## <a name="remarks"></a>Hinweise
Übergeben als Argument an die [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md) Methode.

## <a name="requirements"></a>Anforderungen
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
[Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)
