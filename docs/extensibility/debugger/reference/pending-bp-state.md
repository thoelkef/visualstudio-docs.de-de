---
title: PENDING_BP_STATE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- PENDING_BP_STATE
helpviewer_keywords:
- PENDING_BP_STATE enumeration
ms.assetid: ac04ad72-fa92-4a15-ade2-0d0bbbadfc7f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ae632ab67a21d795a0594d37301c162c1c4ba753
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="pendingbpstate"></a>PENDING_BP_STATE
Gibt den Zustand eines ausstehenden Haltepunkts (einen Haltepunkt, die noch nicht gebunden).  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_PENDING_BP_STATE {   
   PBPS_NONE     = 0x0000,  
   PBPS_DELETED  = 0x0001,  
   PBPS_DISABLED = 0x0002,  
   PBPS_ENABLED  = 0x0003  
};  
typedef DWORD PENDING_BP_STATE;  
```  
  
```csharp  
public enum enum_PENDING_BP_STATE {   
   PBPS_NONE     = 0x0000,  
   PBPS_DELETED  = 0x0001,  
   PBPS_DISABLED = 0x0002,  
   PBPS_ENABLED  = 0x0003  
};  
```  
  
## <a name="members"></a>Member  
 PBPS_NONE  
 Platzhalter für 0 (null). Dieser Wert wird niemals zurückgegeben.  
  
 PBPS_DELETED  
 Gibt an, dass die ausstehende Haltepunkt gelöscht wurde.  
  
 PBPS_DISABLED  
 Gibt an, dass die ausstehende Haltepunkt deaktiviert ist.  
  
 PBPS_ENABLED  
 Gibt an, dass die ausstehende Breakpoint aktiviert ist.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden Sie als die `state` Mitglied der [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) Struktur.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)