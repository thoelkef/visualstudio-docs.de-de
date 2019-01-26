---
title: BP_STATE | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BP_STATE
helpviewer_keywords:
- BP_STATE enumeration
ms.assetid: 08aa6a3f-3e5f-4c83-8eca-7b7b5f8e208d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9638256c3aaf3d025b59b7fba89cf33e72a47a1a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55006423"
---
# <a name="bpstate"></a>BP_STATE
Gibt an, ob einen gebundenen Haltepunkt vorhanden ist, und gibt auch an, wenn es aktiviert ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_BP_STATE {   
   BPS_NONE     = 0x0000,  
   BPS_DELETED  = 0x0001,  
   BPS_DISABLED = 0x0002,  
   BPS_ENABLED  = 0x0003  
};  
typedef DWORD BP_STATE;  
```  
  
```csharp  
public enum enum_BP_STATE {   
   BPS_NONE     = 0x0000,  
   BPS_DELETED  = 0x0001,  
   BPS_DISABLED = 0x0002,  
   BPS_ENABLED  = 0x0003  
};  
```  
  
## <a name="members"></a>Member  
 BPS_NONE  
 Gibt an, dass kein Haltepunkt vorhanden ist.  
  
 BPS_DELETED  
 Gibt an, dass der Haltepunkt gelöscht wurde.  
  
 BPS_DISABLED  
 Gibt an, dass der Haltepunkt deaktiviert ist.  
  
 BPS_ENABLED  
 Gibt an, dass der Breakpoint aktiviert ist.  
  
## <a name="remarks"></a>Hinweise  
 Zurückgegeben von der [GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)