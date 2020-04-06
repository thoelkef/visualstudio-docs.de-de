---
title: IDebugCoreServer3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3
helpviewer_keywords:
- IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d110e66e937249fdee34f424d4f68a9b914113d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732807"
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
Diese Schnittstelle ermöglicht den Zugriff auf Informationen über den Server, auf dem der Prozess ausgeführt wird.

## <a name="syntax"></a>Syntax

```
IDebugCoreServer3 : IDebugCoreServer2
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Visual Studio implementiert diese Schnittstelle.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Verwenden Sie [QueryInterface,](/cpp/atl/queryinterface) um diese Schnittstelle von einer [IDebugCoreServer2-Schnittstelle](../../../extensibility/debugger/reference/idebugcoreserver2.md) abzurufen. Ein Aufruf von [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) kann auch diese Schnittstelle zurückgeben. Diese Schnittstelle wird am häufigsten von einem benutzerdefinierten Portanbieter verwendet, um Programme auf einem Server (lokal oder remote) zu starten.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den Methoden auf der [IDebugCoreServer2-Schnittstelle](../../../extensibility/debugger/reference/idebugcoreserver2.md) implementiert diese Schnittstelle die folgenden Methoden:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|Ruft den Namen des Servers ab.|
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|Ruft eine benutzerfreundliche Version des Servernamens ab|
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|Weist bestimmte Debugmodule an, beim Starten dieser Prozesse automatisch an Prozesse anzuhängen.|
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|Ruft einen bestimmten Fehlercode ab, wenn der automatische Anfügen fehlschlägt.|
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|Erstellt eine Instanz eines Debugmoduls auf dem Server.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|Ruft ein Flag ab, das angibt, ob sich der Server auf demselben Computer wie der Aufrufer befindet.|
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|Ruft einen Wert ab, der das Protokoll angibt, das für die Kommunikation mit dem Server verwendet wird.|
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|Deaktiviert alle Einstellungen für die automatische Anfügen für alle Debugmodule, die dieser Server kennt.|

## <a name="remarks"></a>Bemerkungen
 Ein benutzerdefinierter Portlieferant empfängt die [IDebugCoreServer2-Schnittstelle](../../../extensibility/debugger/reference/idebugcoreserver2.md) bei einem Aufruf von [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md). Die `IDebugCoreServer3` Schnittstelle kann von dieser Schnittstelle bezogen werden.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
