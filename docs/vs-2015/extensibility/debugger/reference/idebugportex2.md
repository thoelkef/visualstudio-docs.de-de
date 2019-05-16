---
title: IDebugPortEx2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortEx2
helpviewer_keywords:
- IDebugPortEx2 interface
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bb866c5cb968a4f03c718f04193026ac5308f7d4
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65681124"
---
# <a name="idebugportex2"></a>IDebugPortEx2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle kann die Sitzung, die für das Debuggen von Manager (SDM)-Steuerelement, Programme und Prozesse, die auf einem Port ausgeführt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPortEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Ein benutzerdefinierten Port Lieferanten implementiert diese Schnittstelle für das gleiche Objekt, das implementiert [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md).  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Die SDM-Aufrufe [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) auf die `IDebugPort2` Schnittstelle, um diese Schnittstelle zu erhalten.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugPortEx2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|Wird eine ausführbare Datei gestartet.|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|Setzt die Ausführung eines Prozesses.|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|Bestimmt, ob ein Prozess beendet werden kann.|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|Beendet einen Prozess an.|  
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|Ruft die Prozess-ID des Ports selbst ab.|  
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|Ruft ein Programm mit einem Programm-Knoten verknüpft ist.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Schnittstelle ist normalerweise privat zwischen den SDM und den benutzerdefinierten Port Lieferanten.  
  
 Falls gewünscht, kann eine Debug-Engine (DE) für diese Schnittstelle auf Suchen der [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) Schnittstelle zu übergeben, um [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) und [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) auf das Programm zu starten. Dies ist nicht zwingend erforderlich, allerdings und eine bereitgestellten Kompatibilitätsrichtlinie möglich, was sie tun, um das Programm für die Anforderung zu starten muss.  
  
## <a name="requirements"></a>Anforderungen  
 Header: portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
