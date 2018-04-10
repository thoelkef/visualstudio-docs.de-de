---
title: IDebugPortEvents2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPortEvents2
helpviewer_keywords:
- IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
caps.latest.revision: 18
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 0a5782f0a50ac37b45c4b7e3402bcdded96b4683
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/10/2018
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
Diese Schnittstelle wird einen Listener (in der Regel der Sitzung Debug-Manager [SDM] oder ein Debugging-Modul) von Prozess- und Programm erstellen und Zerstören eines bestimmten Ports benachrichtigt. Diese Informationen können verwendet werden, um eine Echtzeitansicht von der ausgeführten Prozessen und Programmen auf den Port vorhanden.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPortEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Visual Studio implementiert in der Regel diese Schnittstelle, um Benachrichtigungen über die Erstellung und Zerstörung empfangen. Ein Debugmodul kann auch diese Schnittstelle zum Überwachen von Ereignissen Port implementieren.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Alle [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) Schnittstellen können abgefragt werden, für eine <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> Schnittstelle. Die <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> Methode zum `IDebugPortEvents2` wird aufgerufen, der <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> abzurufenden Schnittstelle eine <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> Schnittstelle. Schließlich die <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> Methode in der <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> Schnittstelle aufgerufen, um die Ereignisse durch Senden der [Ereignis](../../../extensibility/debugger/reference/idebugportevents2-event.md) Methode.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methode der `IDebugPortEvents2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)|Sendet Ereignisse an, die die Erstellung und Zerstörung von Prozessen und Programmen auf den Port zu beschreiben.|  
  
## <a name="remarks"></a>Hinweise  
 `IDebugPortEvents2` durch die SDM dient auch zum Debuggen von Programmen, die in einem Prozess ausgeführt werden, die bereits debuggt wird.  
  
 Portereignisse werden an die SDM von dieser Schnittstelle übergeben.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)