---
title: MODULE_FLAGS | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_FLAGS
helpviewer_keywords:
- MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3ec96c5ba806e6eff735edc8093868b19ebaf5b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56681399"
---
# <a name="moduleflags"></a>MODULE_FLAGS
Dient zum Beschreiben eines Moduls.

## <a name="syntax"></a>Syntax

```cpp
enum enum_MODULE_FLAGS { 
   MODULE_FLAG_NONE        = 0x0000,
   MODULE_FLAG_SYSTEM      = 0x0001,
   MODULE_FLAG_SYMBOLS     = 0x0002,
   MODULE_FLAG_64BIT       = 0x0004,
   MODULE_FLAG_OPTIMIZED   = 0x0008,
   MODULE_FLAG_UNOPTIMIZED = 0x0010
};
typedef DWORD MODULE_FLAGS;
```

```csharp
public enum enum_MODULE_FLAGS { 
   MODULE_FLAG_NONE        = 0x0000,
   MODULE_FLAG_SYSTEM      = 0x0001,
   MODULE_FLAG_SYMBOLS     = 0x0002,
   MODULE_FLAG_64BIT       = 0x0004,
   MODULE_FLAG_OPTIMIZED   = 0x0008,
   MODULE_FLAG_UNOPTIMIZED = 0x0010
};
```

## <a name="members"></a>Member
 MODULE_FLAG_NONE gibt kein Modul an.

 MODULE_FLAG_SYSTEM gibt an, ein Systemmodul.

 MODULE_FLAG_SYMBOLS gibt ein Symbol-Modul an.

 MODULE_FLAG_64BIT gibt ein 64-Bit-Modul an.

 MODULE_FLAG_OPTIMIZED gibt an, die das Modul optimiert wurde. Dieser Status wird wiedergegeben, der **Module** Fenster.

 MODULE_FLAG_UNOPTIMIZED gibt an, die das Modul nicht optimiert wurde. Dieser Status wird wiedergegeben, der **Module** Fenster. Dies ist der Standardzustand.

## <a name="remarks"></a>Hinweise
 Verwendet für die `m_dwModuleFlags` Mitglied der [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) Struktur.

 Diese Flags können kombiniert werden, mit einer bitweisen `OR`.

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)