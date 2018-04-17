---
title: EXCEPTION_STATE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- EXCEPTION_STATE
helpviewer_keywords:
- EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1faa847d907af938bb5f91206a5f438bcba886a3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="exceptionstate"></a>EXCEPTION_STATE
Gibt den Ausnahmestatus.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_EXCEPTION_STATE {   
   EXCEPTION_NONE                          = 0x0000,  
   EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,  
   EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,  
   EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,  
   EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,  
   EXCEPTION_STOP_ALL                      = 0x00FF,  
   EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,  
  
   // These are for exception types only  
   EXCEPTION_CODE_SUPPORTED                = 0x1000,  
   EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,  
   EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,  
   EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,  
  
   // These are no longer used  
   EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,  
   EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,  
   EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,  
   EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,  
};  
typedef DWORD EXCEPTION_STATE;  
```  
  
```csharp  
public enum enum_EXCEPTION_STATE {   
   EXCEPTION_NONE                          = 0x0000,  
   EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,  
   EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,  
   EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,  
   EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,  
   EXCEPTION_STOP_ALL                      = 0x00FF,  
   EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,  
  
   // These are for exception types only  
   EXCEPTION_CODE_SUPPORTED                = 0x1000,  
   EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,  
   EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,  
   EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,  
  
   // These are no longer used  
   EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,  
   EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,  
   EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,  
   EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,  
};  
```  
  
## <a name="members"></a>Member  
 EXCEPTION_NONE  
 Nicht an der Ausnahme beendet.  
  
 EXCEPTION_STOP_FIRST_CHANCE  
 Beenden Sie am ersten Auslösung der Ausnahme. Beim Beschreiben von einem Ausnahmeereignis gibt dieses Flag an, dass Ausnahmeereignisses Ereignis Ausnahme der ersten Chance ist.  
  
 EXCEPTION_STOP_SECOND_CHANCE  
 Beenden Sie am zweiten Auslösen der Ausnahme. Beim Beschreiben von einem Ausnahmeereignis gibt an, dass das Ausnahmeereignis einen zweiten Chance Ausnahmeereignisses.  
  
 EXCEPTION_STOP_USER_FIRST_CHANCE  
 Beenden Sie am ersten Auslösen einer Ausnahme des User-Modus. Beim Beschreiben von einem Ausnahmeereignis gibt an, dass das Ausnahmeereignis ein Ereignis für abgefangene Ausnahme.  
  
 EXCEPTION_STOP_USER_UNCAUGHT  
 Beendet, wenn eine Benutzer-Modus-Ausnahme nicht abgefangen wird. Beim Beschreiben von einem Ausnahmeereignis gibt an, dass das Ausnahmeereignis eine nicht abgefangene Benutzerereignis Modus Ausnahme.  
  
 EXCEPTION_STOP_ALL  
 Bei jeder Ausnahme beendet. Beim Beschreiben von einem Ausnahmeereignis verwendet nicht.  
  
 EXCEPTION_CANNOT_BE_CONTINUED  
 Beim Beschreiben von einem Ausnahmeereignis gibt an, dass die Ausnahme kann nicht fortgesetzt werden, aus.  
  
 EXCEPTION_CODE_SUPPORTED  
 Gibt an, dass die Ausnahme unterstützen Code verfügt. Anzeigen von einer Ausnahme verwendet  
  
 EXCEPTION_CODE_DISPLAY_IN_HEX  
 Gibt an, dass der Ausnahmecode im Hexadezimalformat angezeigt werden soll. Anzeigen von einer Ausnahme verwendet.  
  
 EXCEPTION_JUST_MY_CODE_SUPPORTED  
 Gibt an, dass der Ausnahmecode JustMyCode unterstützt. Anzeigen von einer Ausnahme verwendet.  
  
 EXCEPTION_MANAGED_DEBUG_ASSISTANT  
 Gibt an, dass der Debugger für verwalteten Code Ausnahmen behandeln soll. Wenn dies nicht festgelegt ist, die Standarddebugger Ausnahmen behandelt. Dies wird zum Übergeben der [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) Methode und nicht in verwendet das [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) Struktur.  
  
 EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT  
 VERALTET, VERWENDEN SIE NICHT.  
  
 EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT  
 VERALTET, VERWENDEN SIE NICHT.  
  
 EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT  
 VERALTET, VERWENDEN SIE NICHT.  
  
 EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT  
 VERALTET, VERWENDEN SIE NICHT.  
  
## <a name="remarks"></a>Hinweise  
 Verwendet als die `dwState` Mitglied der [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) Struktur an, dass der Status der Ausnahme und was dies erledigt werden kann.  
  
 Diese Werte werden auch zum Übergeben der [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) Methode zum Festlegen des Status aller Ausnahmen.  
  
 Diese Flags können mit einem bitweisen OR kombiniert werden.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)