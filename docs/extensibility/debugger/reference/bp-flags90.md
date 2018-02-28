---
title: BP_FLAGS90 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: af59e06ad31b56c04127ca89b43a903db36d3615
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="bpflags90"></a>BP_FLAGS90
Listet die gültigen Werte für optionale Kennzeichen. Das optionalen Kennzeichen können verwendet werden, um zusätzliche Informationen angeben, wenn Sie einen Haltepunkt festlegen. Diese Enumeration erweitert die [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) Enumeration.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
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
 Gibt kein Haltepunkt-Flag an.  
  
 BP90_FLAG_MAP_DOCPOSITION  
 Gibt an, dass den Haltepunkt mithilfe der Dokumentposition Debugging-Modul (DE) zugeordnet werden sollen. Dies gilt nur für Haltepunkte in Skripts orientierten Quelldateien z. B. Active Server Pages (ASP).  
  
 BP90_FLAG_DONT_STOP  
 Gibt an, dass der Haltepunkt von Debugging-Modul verarbeitet werden sollen, aber das Debugmodul letztendlich nicht es beendet werden soll. d. h. eine [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) Ereignisobjekt nicht gesendet werden soll. Dieses Flag dient in erster Linie mit nachverfolgungspunkte verwendet werden soll.  
  
 BP90_FLAG_TRACEPOINT_CONTINUE  
 Von der systemeigenen Debugging-Modul verwendet, um festzustellen, ob es sich bei der schrittweisen Zustand gelöscht werden soll. Es unterscheidet sich vom BP90_FLAG_DONT_STOP, da BP90_FLAG_DONT_STOP nicht festgelegt ist, wenn die Trace-Punkt ein Makro ausgeführt wird.  
  
## <a name="requirements"></a>Anforderungen  
 Header: Msdbg90.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)