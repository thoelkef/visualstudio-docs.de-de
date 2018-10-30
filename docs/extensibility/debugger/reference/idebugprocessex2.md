---
title: IDebugProcessEx2 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7fa10fb5ebe2f9a78d44997c29ae51bc02e2c842
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49934937"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
Diese Schnittstelle kann die Sitzung mit dem Debug-Manager (SDM) einen Prozess, den zum Anfügen oder Trennen vom Prozess zu benachrichtigen.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProcessEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Ein benutzerdefinierten Port Lieferanten implementiert diese Schnittstelle auf dasselbe Objekt wie die [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) um Schnittstelle:  
  
- Unterstützung der nachverfolgung von Sitzungen, die an einen Prozess verbunden  
  
- Unterstützung für das automatische Anhängen über mehrere Debug-engines  
  
  Benutzerdefinierte Anschlusslieferanten kann diese Schnittstelle implementieren, wenn er entscheidet.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
  
-   Die SDM-Aufrufe [QueryInterface](/cpp/atl/queryinterface) auf eine `IDebugProcess2` Schnittstelle, um diese Schnittstelle zu erhalten.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugProcessEx2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Anfügen](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|Informiert dem Prozess, eine Sitzung jetzt Debuggen des Prozesses ist.|  
|[Trennen](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|Informiert dem Prozess, eine Sitzung nicht mehr Debuggen des Prozesses ist.|  
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|Programmknoten eine Liste von Debug-Engines hinzugefügt.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Schnittstelle ist privat zwischen den SDM und dem Prozess.  
  
## <a name="requirements"></a>Anforderungen  
 Header: Portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)