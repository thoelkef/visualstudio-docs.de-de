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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58956956"
---
# <a name="bpflags90"></a>BP_FLAGS90
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Listet die gültigen Werte für optionale Kennzeichen. Die optionalen Kennzeichen können verwendet werden, um zusätzliche Informationen angeben, wenn Sie einen Haltepunkt festlegen. Diese Enumeration erweitert die [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) Enumeration.  
  
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
 Gibt kein Flag Haltepunkt an.  
  
 BP90_FLAG_MAP_DOCPOSITION  
 Gibt an, dass den Haltepunkt mit die Dokumentposition die Debug-Engine (DE) zugeordnet werden sollen. Dies gilt nur für Haltepunkte, die in den Skript-orientierten Quelldateien wie z. B. Active Server Pages (ASP).  
  
 BP90_FLAG_DONT_STOP  
 Gibt an, dass der Haltepunkt von der Debug-Engine verarbeitet werden sollen, aber die Debug-Engine letztlich nicht es beendet werden soll. d. h. eine [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) Ereignisobjekt nicht gesendet werden soll. Dieses Flag dient in erster Linie mit Punkten der Ablaufverfolgung verwendet werden.  
  
 BP90_FLAG_TRACEPOINT_CONTINUE  
 Durch die systemeigenen Debug-Engine verwendet, um festzustellen, ob es sich bei der schrittweisen Ausführung Zustand gelöscht werden sollen. Es unterscheidet sich von BP90_FLAG_DONT_STOP BP90_FLAG_DONT_STOP nicht festgelegt ist, wenn der Ablaufverfolgungspunkt ein Makro ausgeführt wird.  
  
## <a name="requirements"></a>Anforderungen  
 Header: Msdbg90.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
