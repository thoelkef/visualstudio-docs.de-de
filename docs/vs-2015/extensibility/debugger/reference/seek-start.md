---
title: SEEK_START | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SEEK_START
helpviewer_keywords:
- SEEK_START enumeration
ms.assetid: 55bd8901-626e-428b-a263-23b14417f4c6
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9a12e72ea6534bed226ece7aa79788e48813797f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903854"
---
# <a name="seekstart"></a>SEEK_START
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt die Position, ab dem mit dem Sie suchen, die in einem Stream Disassembly.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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

