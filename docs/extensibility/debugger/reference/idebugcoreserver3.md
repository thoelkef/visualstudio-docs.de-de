---
title: IDebugCoreServer3 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3
helpviewer_keywords:
- IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 629e35e8756be1dfa6df9f21eda02624b4c363de
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56691318"
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
Diese Schnittstelle bietet Zugriff auf Informationen über den Server, die, den der Prozess ausgeführt wird.

## <a name="syntax"></a>Syntax

```
IDebugCoreServer3 : IDebugCoreServer2
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Visual Studio implementiert diese Schnittstelle.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Verwendung [QueryInterface](/cpp/atl/queryinterface) dieser Schnittstelle vom Abrufen einer [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) Schnittstelle. Ein Aufruf von [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) können diese Schnittstelle auch zurückgeben. Diese Schnittstelle wird meist ein Lieferant benutzerdefinierten Port verwendet, um Programme auf einem Server (lokal oder remote) zu starten.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den Methoden für die [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) Schnittstelle, die diese Schnittstelle implementiert die folgenden Methoden:

|Methode|Beschreibung|
|------------|-----------------|
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|Ruft den Namen des Servers.|
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|Ruft eine benutzerfreundliche Version des Servernamens.|
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|Teilt bestimmte Debug-Engines automatisch an Prozesse anfügen, wenn die Prozesse starten.|
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|Ruft einen bestimmten Fehlercode ab, wenn automatische anfügen erzeugt einen Fehler.|
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|Erstellt eine Instanz von einer Debug-Engine auf dem Server.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|Ruft ein Flag, der angibt, ob der Server auf dem gleichen Computer wie der Aufrufer ist ab.|
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|Ruft einen Wert, der angibt, des Protokolls für die Kommunikation mit dem Server verwendet wird.|
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|Deaktiviert alle Anhängen Einstellungen für alle Debug-Engines, die, denen diesem Server bekannt sind, automatische.|

## <a name="remarks"></a>Hinweise
 Ein benutzerdefinierter Port Lieferant empfängt die [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) Schnittstelle, die bei einem Aufruf von [Ereignis](../../../extensibility/debugger/reference/idebugportevents2-event.md). Die `IDebugCoreServer3` Schnittstelle kann von dieser Schnittstelle abgerufen werden.

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)