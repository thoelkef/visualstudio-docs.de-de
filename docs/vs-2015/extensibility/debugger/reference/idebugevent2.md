---
title: IDebugEvent2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f663be5910b342a6adba5da0b84d7e0d80cacc10
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695414"
---
# <a name="idebugevent2"></a>IDebugEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle wird verwendet, um sowohl wichtige Debuginformationen, wie z. b. das Anhalten an einem Haltepunkt, als auch nicht kritische Informationen, wie z. b. eine Debugmeldung,  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debug-Engine (de) und der benutzerdefinierte Port Lieferant implementieren diese Schnittstelle für dasselbe Objekt wie alle anderen Ereignis Schnittstellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Mithilfe des IID-Arguments (Interface ID), das an ein [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) oder [Ereignis](../../../extensibility/debugger/reference/idebugportevents2-event.md)übergeben wird, ruft der Sitzungs-Debug-Manager (SDM) [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) für die `IDebugEvent2` Schnittstelle auf, um die entsprechende Ereignis Schnittstelle zu erhalten.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugEvent2` .  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Ruft die Attribute für dieses Debugereignis ab.|  
  
## <a name="remarks"></a>Bemerkungen  
 Die spezifischeren Ereignis Schnittstellen, wie z. b. [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md), werden nicht von der IDebugEvent2-Schnittstelle abgeleitet, sondern stattdessen als separate Schnittstelle für dasselbe Objekt implementiert `IDebugEvent2` .  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Kern Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Veranstalter](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
