---
title: IDebugDefaultPort2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e646a248e4b7da03a9dbad9bcea2470d9d0f450
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62876009"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
Diese Schnittstelle bietet mehrere Methoden für den Zugriff auf einen Port für den Server und Notification-Funktionen.

## <a name="syntax"></a>Syntax

```
IDebugDefaultPort2 : IDebugPort2
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Visual Studio implementiert diese Schnittstelle, um das Debuggen Port für den Zugriff auf Programme darstellen. Ein benutzerdefinierter Port Lieferant kann auch diese Schnittstelle implementieren, wenn die Methode behandelt das Remotedebuggen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Ein Argument auf Methoden in der [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) Schnittstelle stellt diese Schnittstelle. Aufrufen von [QueryInterface](/cpp/atl/queryinterface) auf eine [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) Schnittstelle kann auch abrufen, diese Schnittstelle.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den Methoden, die in definierten [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md), diese Schnittstelle implementiert die folgenden Methoden:

|Methode|Beschreibung|
|------------|-----------------|
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|Ruft die Port-Notification-Schnittstelle von diesem Port ab.|
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Ruft die Schnittstelle auf dem Hostserver diesen Port ab.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Bestimmt, ob dieser Port auf dem lokalen Computer ausgeführt wird.|

## <a name="remarks"></a>Hinweise
 Der Name "`IDebugDefaultPort2`" wird von ein wenig irreführend, da es keinen Standardport darstellt. Sie können "IDebugPort3." aufgerufen werden

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)