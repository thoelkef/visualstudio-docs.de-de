---
title: IDebugPort2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPort2
helpviewer_keywords:
- IDebugPort2 interface
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d1811ad7e46865d00eed2066d061daec78d7ab2b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
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
 Aufrufe von [GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md) oder [hinzufügen](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) zurückgeben dieser Schnittstelle, die den angeforderten Port darstellt.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugPort2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|Gibt den Namen des Anschlusses zurück.|  
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|Gibt den Port-Bezeichner.|  
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|Gibt die Anforderung zum Erstellen eines Ports (falls verfügbar) verwendet.|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)|Gibt den Port Lieferanten für diesen Port.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)|Gibt eine Schnittstelle für den Prozess erhält die Prozess-ID zurück.|  
|[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)|Listet die Prozesse, die auf einem Port ausgeführt wird.|  
  
## <a name="remarks"></a>Hinweise  
 Der lokale Port ermöglicht den Zugriff auf die Prozesse und Programme, die auf dem lokalen Computer ausgeführt. Andere Ports können es sich um eine serielle Kabel-Verbindung mit einem Windows CE-basierten Gerät oder eine Netzwerkverbindung mit einem nicht-DCOM-Computer darstellen. Die `IDebugPort2` Schnittstelle wird verwendet, um suchen den Namen und Bezeichner eines Ports auflisten alle Prozesse auf dem Port, und geben Funktionen für starten und Beenden von Prozessen auf dem Port.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)