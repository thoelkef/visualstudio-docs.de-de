---
title: PENDING_BP_STATE_INFO | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PENDING_BP_STATE_INFO
helpviewer_keywords:
- PENDING_BP_STATE_INFO structure
ms.assetid: 4d73ceff-43f9-4e95-8dba-88e1fab2def3
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: af22ef2d8a77b8c44b9e494736630480a0614162
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205070"
---
# <a name="pending_bp_state_info"></a>PENDING_BP_STATE_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Enthält Informationen zum Zustand eines Breakpoints, der für die Bindung an einen Code Speicherort bereit ist.  
  
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
 state  
 Ein Wert aus der [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md) Enumeration, der den Status des ausstehenden halte Punkts angibt.  
  
 flags  
 Eine Kombination von Flags aus der [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md) -Enumeration, die angibt, ob der Breakpoint virtualisiert ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Struktur wird an die [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md) -Methode übermittelt, wo Sie ausgefüllt ist.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)   
 [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md)   
 [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md)
