---
title: BP_UNBOUND_REASON | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ddff6130e2243d10c00cefec160d057516d60932
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153278"
---
# <a name="bp_unbound_reason"></a>BP_UNBOUND_REASON
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt den Grund für die Bindung eines Breakpoints an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 Der Grund ist unbekannt.  
  
 BPUR_CODE_UNLOADED  
 Der Code, der den Breakpoint enthält, wurde entladen.  
  
 BPUR_BREAKPOINT_REBIND  
 Der Breakpoint wurde an einen anderen Speicherort wieder gebunden. Dies kann nach dem Bearbeiten und Fortfahren erfolgen, wenn der Breakpoint verschoben wird, oder wenn der Breakpoint an eine Datei mit einem Pfad gebunden ist, der nicht mehr gültig ist.  
  
 BPUR_ BREAKPOINT_ERROR  
 Der Haltepunkt wird als fehlerhaft festgelegt, nachdem er gebunden wurde. Dies geschieht bei verwalteten Haltepunkten, deren Bedingungen nicht mehr gültig sind.  
  
## <a name="remarks"></a>Bemerkungen  
 Wird von der [geverrat](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) -Methode zurückgegeben.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)
