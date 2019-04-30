---
title: IDebugErrorEvent2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorEvent2
helpviewer_keywords:
- IDebugErrorEvent2 interface
ms.assetid: 275b6f38-b3d4-4cae-8491-491177f524fb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ba7e17cb07e1a2d57d75dc573ceca5ebd522b2e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920119"
---
# <a name="idebugerrorevent2"></a>IDebugErrorEvent2
Diese Schnittstelle gibt eine Fehlermeldung angezeigt, die dem Benutzer gemeldet werden.

## <a name="syntax"></a>Syntax

```
IDebugErrorEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine (DE) implementiert diese Schnittstelle zum Melden von Fehlern als lesbare Nachrichten. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) Schnittstelle muss auf dasselbe Objekt wie diese Schnittstelle implementiert werden. Wird verwendet, das SDM [QueryInterface](/cpp/atl/queryinterface) für den Zugriff auf die `IDebugEvent2` Schnittstelle.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Die DE erstellt und sendet dieses Ereignisobjekt, um Fehler zu melden. Das Ereignis gesendet wird, mithilfe der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Callback-Funktion, die durch die SDM bereitgestellt wird, wenn diese an die zu debuggende Programm wird angefügt.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Diese Schnittstelle implementiert die folgende Methode:

|Methode|Beschreibung|
|------------|-----------------|
|`GetErrorMessage`|Gibt einen Fehler als lesbare Zeichenfolge zurück.|

## <a name="remarks"></a>Hinweise
 Wenn die Debug-Engine ein Fehler auftritt, können sie diese Schnittstelle verwenden, um die Nachricht mithilfe von Visual Studio für den Benutzer zu melden.

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)