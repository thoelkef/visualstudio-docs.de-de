---
title: SEEK_START | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SEEK_START
helpviewer_keywords:
- SEEK_START enumeration
ms.assetid: 55bd8901-626e-428b-a263-23b14417f4c6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 203371cd1ee2d1a9efe4c50f8d5a73f2fa7d7980
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54961873"
---
# <a name="seekstart"></a>SEEK_START
Gibt die Position, ab dem mit dem Sie suchen, die in einem Stream Disassembly.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_SEEK_START {   
   SEEK_START_BEGIN       = 0x0001,  
   SEEK_START_END         = 0x0002,  
   SEEK_START_CURRENT     = 0x0003,  
   SEEK_START_CODECONTEXT = 0x0004,  
   SEEK_START_CODELOCID   = 0x0005  
};  
typedef DWORD SEEK_START;  
```  
  
```csharp  
public enum enum_SEEK_START {   
   SEEK_START_BEGIN       = 0x0001,  
   SEEK_START_END         = 0x0002,  
   SEEK_START_CURRENT     = 0x0003,  
   SEEK_START_CODECONTEXT = 0x0004,  
   SEEK_START_CODELOCID   = 0x0005  
};  
```  
  
## <a name="members"></a>Member  
 SEEK_START_BEGIN  
 Beginnt die Suche am Anfang des aktuellen Dokuments.  
  
 SEEK_START_END  
 Beginnt die Suche am Ende des aktuellen Dokuments.  
  
 SEEK_START_CURRENT  
 Beginnt die Suche an der aktuellen Position des aktuellen Dokuments.  
  
 SEEK_START_CODECONTEXT  
 Startet die Suchvorgänge in den angegebenen Code-Kontext des aktuellen Dokuments.  
  
 SEEK_START_CODELOCID  
 Wird gestartet, an der angegebenen Code Standortbezeichner suchen. Speicherort der Codebezeichner erhalten Sie durch Aufrufen von [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md).  
  
## <a name="remarks"></a>Hinweise  
 Übergeben als Argument an die [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Suchen](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)   
 [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)