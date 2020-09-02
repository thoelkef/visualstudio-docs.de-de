---
title: MODULE_FLAGS | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- MODULE_FLAGS
helpviewer_keywords:
- MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ae51d604f455b12fd6933a54954b75a97aea4eb7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547467"
---
# <a name="module_flags"></a>MODULE_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Wird verwendet, um ein Modul zu beschreiben.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 Gibt kein Modul an.  
  
 MODULE_FLAG_SYSTEM  
 Gibt ein Systemmodul an.  
  
 MODULE_FLAG_SYMBOLS  
 Gibt ein Symbol Modul an.  
  
 MODULE_FLAG_64BIT  
 Gibt ein 64-Bit-Modul an.  
  
 MODULE_FLAG_OPTIMIZED  
 Gibt an, dass das Modul optimiert wurde. Dieser Status wird im Fenster **Module** widergespiegelt.  
  
 MODULE_FLAG_UNOPTIMIZED  
 Gibt an, dass das Modul nicht optimiert wurde. Dieser Status wird im Fenster **Module** widergespiegelt. Dies ist die Standardeinstellung.  
  
## <a name="remarks"></a>Bemerkungen  
 Wird für den `m_dwModuleFlags` Member der [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) -Struktur verwendet.  
  
 Diese Flags können mit einem bitweisen kombiniert werden `OR` .  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
