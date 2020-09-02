---
title: BP_FLAGS90 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9f7192eb7b2fa6d8bc886c0e601788ecba8eebcd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153498"
---
# <a name="bp_flags90"></a>BP_FLAGS90
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Listet gültige Werte für optionale Flags auf. Die optionalen Flags können verwendet werden, um zusätzliche Informationen anzugeben, wenn Sie einen Haltepunkt festlegen. Diese Enumeration erweitert die [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) Enumeration.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_BP_FLAGS90  
{  
   // VS 8.0 values  
   BP90_FLAG_NONE               = 0x0000,  
   BP90_FLAG_MAP_DOCPOSITION    = 0x0001,  
   BP90_FLAG_DONT_STOP          = 0x0002,  
  
   // Values added in VS 9.0  
   BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,  
};  
typedef DWORD BP_FLAGS90;  
```  
  
```csharp  
public enum enum_BP_FLAGS90  
{  
   // VS 8.0 values  
   BP90_FLAG_NONE                = 0x0000,  
   BP90_FLAG_MAP_DOCPOSITION     = 0x0001,  
   BP90_FLAG_DONT_STOP           = 0x0002,  
  
   // Values added in VS 9.0  
   BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,  
};  
```  
  
#### <a name="parameters"></a>Parameter  
 BP90_FLAG_NONE  
 Gibt kein breakpointflag an.  
  
 BP90_FLAG_MAP_DOCPOSITION  
 Gibt an, dass die Debug-Engine (de) den Breakpoint mithilfe der Dokument Position zuordnen soll. Dies gilt nur für Breakpoints, die in Skript orientierten Quelldateien, z. b. Active Server Seiten (ASP), festgelegt sind.  
  
 BP90_FLAG_DONT_STOP  
 Gibt an, dass der Breakpoint von der Debug-Engine verarbeitet werden soll, dass die Debug-Engine aber letztendlich nicht angehalten werden soll. Das heißt, ein [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) -Ereignis Objekt sollte nicht gesendet werden. Dieses Flag ist so konzipiert, dass es hauptsächlich mit Ablauf Verfolgungs Punkten verwendet wird.  
  
 BP90_FLAG_TRACEPOINT_CONTINUE  
 Wird von der systemeigenen Debug-Engine verwendet, um zu bestimmen, ob der Schritt Zustand gelöscht werden soll. Dies unterscheidet sich von BP90_FLAG_DONT_STOP, da BP90_FLAG_DONT_STOP nicht festgelegt ist, wenn der Ablauf Verfolgungs Punkt ein Makro ausführt.  
  
## <a name="requirements"></a>Anforderungen  
 Header: Msdbg90. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
