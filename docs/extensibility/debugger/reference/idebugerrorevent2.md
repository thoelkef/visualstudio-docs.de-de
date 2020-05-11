---
title: IDebugErrorEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorEvent2
helpviewer_keywords:
- IDebugErrorEvent2 interface
ms.assetid: 275b6f38-b3d4-4cae-8491-491177f524fb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 00fd8b4b42f11d18958f8a969bc4ccd58754ab93
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730001"
---
# <a name="idebugerrorevent2"></a>IDebugErrorEvent2
Diese Schnittstelle gibt eine Fehlermeldung an, die dem Benutzer gemeldet werden soll.

## <a name="syntax"></a>Syntax

```
IDebugErrorEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Das Debugmodul (DE) implementiert diese Schnittstelle, um Fehler als menschenlesbare Meldungen zu melden. Die [IDebugEvent2-Schnittstelle](../../../extensibility/debugger/reference/idebugevent2.md) muss für dasselbe Objekt wie diese Schnittstelle implementiert werden. Das SDM verwendet [QueryInterface,](/cpp/atl/queryinterface) um auf die `IDebugEvent2` Schnittstelle zuzugreifen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Die DE erstellt und sendet dieses Ereignisobjekt, um einen Fehler zu melden. Das Ereignis wird mithilfe der [IDebugEventCallback2-Rückruffunktion](../../../extensibility/debugger/reference/idebugeventcallback2.md) gesendet, die vom SDM bereitgestellt wird, wenn es an das zu debuggende Programm angefügt wird.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Diese Schnittstelle implementiert die folgende Methode:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|`GetErrorMessage`|Gibt einen Fehler als lesbare Zeichenfolge zurück.|

## <a name="remarks"></a>Bemerkungen
 Wenn beim Debugmodul ein Fehler auftritt, kann es diese Schnittstelle verwenden, um die Nachricht über Visual Studio an den Benutzer zu melden.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
