---
title: ATTACH_REASON | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATTACH_REASON
helpviewer_keywords:
- ATTACH_REASON enumeration
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 527e7a445356a46abdd6f2edb0555b7c5c9c7de8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="attachreason"></a>ATTACH_REASON
Gibt den Grund für das Debugging-Modul (DE) für die Verbindung mit einem Programm Knoten an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_ATTACH_REASON {   
   ATTACH_REASON_LAUNCH = 0x0001,  
   ATTACH_REASON_USER   = 0x0002,  
   ATTACH_REASON_AUTO   = 0x0003  
};  
typedef DWORD ATTACH_REASON;  
```  
  
```csharp  
public enum enum_ATTACH_REASON {   
   ATTACH_REASON_LAUNCH = 0x0001,  
   ATTACH_REASON_USER   = 0x0002,  
   ATTACH_REASON_AUTO   = 0x0003  
};  
```  
  
## <a name="members"></a>Member  
 ATTACH_REASON_AUTO  
 Angefügt werden, da der Prozess derzeit im Debugmodus ausgeführt wird.  
  
 ATTACH_REASON_LAUNCH  
 Angefügt werden, da der Prozess gestartet wurde.  
  
 ATTACH_REASON_USER  
 Aufgrund einer benutzeranforderung anfügen.  
  
## <a name="remarks"></a>Hinweise  
 Diese Werte werden verwendet, als Parameter an die [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md) und [Anfügen](../../../extensibility/debugger/reference/idebugprogramex2-attach.md) Methoden.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Anfügen](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)