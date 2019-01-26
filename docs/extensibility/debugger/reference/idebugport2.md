---
title: IDebugPort2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPort2
helpviewer_keywords:
- IDebugPort2 interface
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 06026276b6f9b37f005ee296d56ee17df5c75ca8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54962747"
---
# <a name="idebugport2"></a>IDebugPort2
Diese Schnittstelle stellt einen Debugport auf einem Computer.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPort2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Ein benutzerdefinierten Port Lieferanten implementiert diese Schnittstelle, um eine Debugport auf einem Computer darstellen.  
  
 Wenn der Port senden portereignisse unterstützt, muss er auch implementieren die <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> -Schnittstelle zur Unterstützung einer <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> Schnittstelle, die wiederum bietet die [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) Schnittstelle.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Aufrufe von [GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md) oder [Port hinzufügen](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) zurückgeben dieser Schnittstelle, die den angeforderten Port darstellt.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugPort2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|Gibt den Namen des Anschlusses.|  
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|Gibt den Port-Bezeichner.|  
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|Gibt die Anforderung zum Erstellen eines Ports (falls verfügbar) verwendet.|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)|Gibt den Port Lieferanten für diesen Port zurück.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)|Gibt eine Schnittstelle an den Prozess des Prozesses Bezeichner zurück.|  
|[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)|Listet alle Prozesse auf einem Port ausgeführt wird.|  
  
## <a name="remarks"></a>Hinweise  
 Der lokale Port ermöglicht den Zugriff auf alle Prozesse und Programme, die auf dem lokalen Computer ausgeführt. Andere Ports können es sich um eine serielle Kabel-Verbindung mit einem Windows CE-basierten Gerät oder eine Netzwerkverbindung mit einem nicht-DCOM-Computer darstellen. Die `IDebugPort2` Schnittstelle wird zum Suchen des Namens und Bezeichners, eines Ports und Auflisten aller Prozesse, die an den Port verwendet. Möglichkeiten zum Starten und Beenden von Prozessen auf dem Port werden implementiert, der `IDebugPortEx2` Schnittstelle.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)