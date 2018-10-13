---
title: PENDING_BP_STATE_INFO | Microsoft-Dokumentation
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
- PENDING_BP_STATE_INFO
helpviewer_keywords:
- PENDING_BP_STATE_INFO structure
ms.assetid: 4d73ceff-43f9-4e95-8dba-88e1fab2def3
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3bcd498bdd9f195b9ab4f07d525537dc3ee17528
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49231373"
---
# <a name="pendingbpstateinfo"></a>PENDING_BP_STATE_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Enthält Informationen über den Zustand eines Haltepunkts an, die an einen Speicherort gebunden werden kann.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef struct _tagPENDING_BP_STATE_INFO {   
   PENDING_BP_STATE       state;  
   PENDING_BP_STATE_FLAGS flags;  
} PENDING_BP_STATE_INFO;  
```  
  
```csharp  
public struct PENDING_BP_STATE_INFO {   
   public uint state;  
   public uint flags;  
};  
```  
  
## <a name="members"></a>Member  
 Zustand  
 Ein Wert aus der [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md) -Enumeration, die den Status des ausstehenden Haltepunkts angibt.  
  
 Flags  
 Eine Kombination von Flags aus der [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md) -Enumeration, der angibt, ob der Breakpoint virtualisiert wird.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur wird zum Übergeben der [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md) Methode, in denen es ausgefüllt wird.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)   
 [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md)   
 [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md)

