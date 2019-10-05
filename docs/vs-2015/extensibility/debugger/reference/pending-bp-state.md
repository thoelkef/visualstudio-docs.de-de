---
title: PENDING_BP_STATE | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PENDING_BP_STATE
helpviewer_keywords:
- PENDING_BP_STATE enumeration
ms.assetid: ac04ad72-fa92-4a15-ade2-0d0bbbadfc7f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 15ac788bf81ce83c2658b8a88a68ac5281020373
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68205084"
---
# <a name="pendingbpstate"></a>PENDING_BP_STATE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt den Status eines ausstehenden Haltepunkts (einen Haltepunkt, die noch nicht gebunden ist).  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_PENDING_BP_STATE {   
   PBPS_NONE     = 0x0000,  
   PBPS_DELETED  = 0x0001,  
   PBPS_DISABLED = 0x0002,  
   PBPS_ENABLED  = 0x0003  
};  
typedef DWORD PENDING_BP_STATE;  
```  
  
```csharp  
public enum enum_PENDING_BP_STATE {   
   PBPS_NONE     = 0x0000,  
   PBPS_DELETED  = 0x0001,  
   PBPS_DISABLED = 0x0002,  
   PBPS_ENABLED  = 0x0003  
};  
```  
  
## <a name="members"></a>Member  
 PBPS_NONE  
 Platzhalter für 0 (null). Dieser Wert wird nie zurückgegeben.  
  
 PBPS_DELETED  
 Gibt an, dass es sich bei der ausstehenden Haltepunkt gelöscht wurde.  
  
 PBPS_DISABLED  
 Gibt an, dass der ausstehenden Haltepunkt deaktiviert ist.  
  
 PBPS_ENABLED  
 Gibt an, dass es sich bei der ausstehenden Haltepunkt aktiviert ist.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden Sie als die `state` Mitglied der [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) Struktur.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)
