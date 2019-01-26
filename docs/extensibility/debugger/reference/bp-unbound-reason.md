---
title: BP_UNBOUND_REASON | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4d8dfc8e032eecc854a0572c8a7bd14b0c551df7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55028626"
---
# <a name="bpunboundreason"></a>BP_UNBOUND_REASON
Gibt den Grund an, die, den ein Haltepunkt aufgehoben wurde.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
typedef DWORD BP_UNBOUND_REASON;  
```  
  
```csharp  
public enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
```  
  
## <a name="members"></a>Member  
 BPUR_UNKNOWN  
 Der Grund dafür ist unbekannt.  
  
 BPUR_CODE_UNLOADED  
 Der Code mit dem Haltepunkt wurde entladen.  
  
 BPUR_BREAKPOINT_REBIND  
 Der Haltepunkt wurde an einen anderen Speicherort erneut gebunden wurde. Dies kann auftreten, die nach dem Bearbeiten und Vorgänge fortgesetzt, wenn der Haltepunkt verschoben wird oder wenn der Breakpoint in einer Datei mit einem Pfad gebunden ist, die nicht mehr gültig ist.  
  
 BPUR_ BREAKPOINT_ERROR  
 Der Haltepunkt wird bestimmt, um die Fehler werden, nachdem er gebunden ist. Dies geschieht mit verwalteten Haltepunkte, deren Bedingungen nicht mehr gültig sind.  
  
## <a name="remarks"></a>Hinweise  
 Zurückgegeben von der [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)