---
title: MODULE_FLAGS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- MODULE_FLAGS
helpviewer_keywords:
- MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2dcd4b4d63942d7c2f94eda558ea491fa7a1e57e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="moduleflags"></a>MODULE_FLAGS
Dient zum Beschreiben eines Moduls.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_MODULE_FLAGS {   
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
public enum enum_MODULE_FLAGS {   
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
 Gibt kein Modul an.  
  
 MODULE_FLAG_SYSTEM  
 Gibt ein Systemmodul an.  
  
 MODULE_FLAG_SYMBOLS  
 Gibt ein Symbol-Modul an.  
  
 MODULE_FLAG_64BIT  
 Gibt einen 64-Bit-Modul an.  
  
 MODULE_FLAG_OPTIMIZED  
 Gibt an, dass das Modul optimiert wurde. Dieser Status wird wiedergegeben, der **Module** Fenster.  
  
 MODULE_FLAG_UNOPTIMIZED  
 Gibt an, dass das Modul nicht optimiert wurden. Dieser Status wird wiedergegeben, der **Module** Fenster. Dies ist der Standardzustand zurückgesetzt.  
  
## <a name="remarks"></a>Hinweise  
 Verwendet für die `m_dwModuleFlags` Mitglied der [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) Struktur.  
  
 Diese Flags können kombiniert werden, mit einem bitweisen `OR`.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)