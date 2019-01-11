---
title: MODULE_FLAGS | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- MODULE_FLAGS
helpviewer_keywords:
- MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a1082e2e0c1e0d85270b95d4793d1029bbbb79e2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53955645"
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
 MODULE_FLAG_NONE  
 Gibt an, kein Modul.  
  
 MODULE_FLAG_SYSTEM  
 Gibt an, ein Systemmodul.  
  
 MODULE_FLAG_SYMBOLS  
 Gibt ein Symbol-Modul an.  
  
 MODULE_FLAG_64BIT  
 Gibt an, ein 64-Bit-Modul.  
  
 MODULE_FLAG_OPTIMIZED  
 Gibt an, dass das Modul optimiert wurde. Dieser Status wird wiedergegeben, der **Module** Fenster.  
  
 MODULE_FLAG_UNOPTIMIZED  
 Gibt an, dass das Modul nicht optimiert wurde. Dieser Status wird wiedergegeben, der **Module** Fenster. Dies ist der Standardzustand.  
  
## <a name="remarks"></a>Hinweise  
 Verwendet für die `m_dwModuleFlags` Mitglied der [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) Struktur.  
  
 Diese Flags können kombiniert werden, mit einer bitweisen `OR`.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)