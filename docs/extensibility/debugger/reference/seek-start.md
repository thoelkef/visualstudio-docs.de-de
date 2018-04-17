---
title: SEEK_START | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SEEK_START
helpviewer_keywords:
- SEEK_START enumeration
ms.assetid: 55bd8901-626e-428b-a263-23b14417f4c6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 55be60c35ea3af97cb9129670ef422d1a649fead
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="seekstart"></a>SEEK_START
Gibt die Position, ab dem Suchvorgänge in einem Datenstrom Disassembly beginnen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_SEEK_START {   
   SEEK_START_BEGIN       = 0x0001,  
   SEEK_START_END         = 0x0002,  
   SEEK_START_CURRENT     = 0x0003,  
   SEEK_START_CODECONTEXT = 0x0004,  
   SEEK_START_CODELOCID   = 0x0005  
};  
typedef DWORD SEEK_START;  
```  
  
```csharp  
public enum enum_SEEK_START {   
   SEEK_START_BEGIN       = 0x0001,  
   SEEK_START_END         = 0x0002,  
   SEEK_START_CURRENT     = 0x0003,  
   SEEK_START_CODECONTEXT = 0x0004,  
   SEEK_START_CODELOCID   = 0x0005  
};  
```  
  
## <a name="members"></a>Member  
 SEEK_START_BEGIN  
 Das Element beginnt am Anfang des aktuellen Dokuments Suchvorgänge.  
  
 SEEK_START_END  
 Das Element beginnt am Ende des aktuellen Dokuments Suchvorgänge.  
  
 SEEK_START_CURRENT  
 Das Element beginnt an der aktuellen Position des aktuellen Dokuments Suchvorgänge.  
  
 SEEK_START_CODECONTEXT  
 Startet die Suchvorgänge in den angegebenen Codekontext des aktuellen Dokuments.  
  
 SEEK_START_CODELOCID  
 Das Element beginnt am angegebenen Speicherortbezeichner Suchvorgänge. Durch Aufrufen von Code Position-Bezeichner erhalten [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md).  
  
## <a name="remarks"></a>Hinweise  
 Übergeben als Argument an die [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)   
 [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)