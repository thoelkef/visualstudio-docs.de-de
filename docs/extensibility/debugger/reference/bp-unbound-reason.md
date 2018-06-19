---
title: BP_UNBOUND_REASON | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 65398ac0c4bde18dc772d75ceea203bdbfe3b189
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109002"
---
# <a name="bpunboundreason"></a>BP_UNBOUND_REASON
Gibt den Grund für den ein Haltepunkt aufgehoben wurde.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
typedef DWORD BP_UNBOUND_REASON;  
```  
  
```csharp  
public enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
```  
  
## <a name="members"></a>Member  
 BPUR_UNKNOWN  
 Der Grund ist unbekannt.  
  
 BPUR_CODE_UNLOADED  
 Der Code, der den Breakpoint enthält, wurde entladen.  
  
 BPUR_BREAKPOINT_REBIND  
 Der Haltepunkt wurde an einen anderen Speicherort erneut gebunden wurde. Dies kann auftreten, die nach dem Bearbeiten und Operations fortsetzen, wenn der Haltepunkt verschoben wird oder wenn der Breakpoint in einer Datei mit einem Pfad gebunden ist, die nicht mehr gültig ist.  
  
 BPUR_ BREAKPOINT_ERROR  
 Der Haltepunkt wird bestimmt, Fehler werden, nachdem es gebunden ist. Dies erfolgt in verwalteten Haltepunkte, deren Bedingungen nicht mehr gültig sind.  
  
## <a name="remarks"></a>Hinweise  
 Zurückgegebenes der [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)