---
title: ATTACH_REASON | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- ATTACH_REASON
helpviewer_keywords:
- ATTACH_REASON enumeration
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a59e0c8b0d29529af068b3f0e2aec5f605b7e015
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512180"
---
# <a name="attachreason"></a>ATTACH_REASON
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [ATTACH_REASON](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/attach-reason).  
  
Gibt den Grund für die Debug-Engine (DE) Verbindung mit einem Programm-Knoten.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 Angefügt werden, da der Prozess derzeit im Debugmodus befindet.  
  
 ATTACH_REASON_LAUNCH  
 Angefügt werden, da der Prozess gestartet wurde.  
  
 ATTACH_REASON_USER  
 Fügen Sie aufgrund einer benutzeranforderung.  
  
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

