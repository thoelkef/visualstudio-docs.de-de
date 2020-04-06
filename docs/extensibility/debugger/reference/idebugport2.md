---
title: IDebugPort2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2
helpviewer_keywords:
- IDebugPort2 interface
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62912be9fdfecc98a264a58c9713cc12ccaf28f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725234"
---
# <a name="idebugport2"></a>IDebugPort2
Diese Schnittstelle stellt einen Debugport auf einem Computer dar.

## <a name="syntax"></a>Syntax

```
IDebugPort2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein benutzerdefinierter Portlieferant implementiert diese Schnittstelle, um einen Debugport auf einem Computer darzustellen.

 Wenn der Port das Senden von Portereignissen unterstützt, muss er auch die <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> Schnittstelle implementieren, um eine <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> Schnittstelle zu unterstützen, die wiederum die [IDebugPortEvents2-Schnittstelle](../../../extensibility/debugger/reference/idebugportevents2.md) bereitstellt.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Aufrufe von [GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md) oder [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) geben diese Schnittstelle zurück, die den angeforderten Port darstellt.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugPort2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|Gibt den Portnamen zurück.|
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|Gibt den Portbezeichner zurück.|
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|Gibt die Anforderung zurück, die zum Erstellen eines Ports verwendet wird (sofern verfügbar).|
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)|Gibt den Portlieferanten für diesen Port zurück.|
|[Getprocess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)|Gibt eine Schnittstelle an den Prozess zurück, die den Bezeichner des Prozesses verwendet.|
|[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)|Zählt alle Prozesse auf, die auf einem Port ausgeführt werden.|

## <a name="remarks"></a>Bemerkungen
 Der lokale Port bietet Zugriff auf alle Prozesse und Programme, die auf dem lokalen Computer ausgeführt werden. Andere Ports stellen möglicherweise eine serielle Kabelverbindung zu einem Windows CE-basierten Gerät oder eine Netzwerkverbindung zu einem Nicht-DCOM-Computer dar. Die `IDebugPort2` Schnittstelle wird verwendet, um den Namen und den Bezeichner eines Ports zu finden und alle Prozesse aufzuzählen, die auf dem Port ausgeführt werden. In der `IDebugPortEx2` Schnittstelle werden Einrichtungen zum Starten und Beenden von Prozessen am Port implementiert.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
