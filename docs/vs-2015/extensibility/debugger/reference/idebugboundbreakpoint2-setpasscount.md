---
title: 'IDebugBoundBreakpoint2:: setpasscount | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugBoundBreakpoint2::SetPassCount method
ms.assetid: b32c12f9-b34d-43bd-a1b9-61af6cf8e51b
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9711ae6d9048b1de953d8a090b8e11b22c640345
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156175"
---
# <a name="idebugboundbreakpoint2setpasscount"></a>IDebugBoundBreakpoint2::SetPassCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Legt die mit diesem gebundenen Haltepunkt verknüpfte Durchlauf Anzahl fest oder ändert diese.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
```csharp  
int SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `bpPassCount`  
 in Die [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) -Struktur, die die Durchlauf Anzahl angibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. Gibt zurück `E_BP_DELETED` , wenn der Zustand des gebundenen Haltepunkt Objekts auf festgelegt ist `BPS_DELETED` (Teil der [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) Enumeration).  
  
## <a name="remarks"></a>Bemerkungen  
 Der Durchlauf Zähler bestimmt, wann der Breakpoint ausgelöst wird. Die aktuelle Durchlauf-oder Treffer Anzahl kann durch Aufrufen der [gethitcount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md) -Methode abgerufen werden.  
  
 Jeder Durchlauf Zähler, der zuvor mit diesem Breakpoint verknüpft war, geht verloren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [Gethitcount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
