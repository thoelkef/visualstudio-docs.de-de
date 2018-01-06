---
title: PENDING_BP_STATE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PENDING_BP_STATE
helpviewer_keywords: PENDING_BP_STATE enumeration
ms.assetid: ac04ad72-fa92-4a15-ade2-0d0bbbadfc7f
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f98396b7ed1066cacce91ebd08d3cd414042f84e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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