---
title: IDebugSymbolSearchEvent2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolSearchEvent2
helpviewer_keywords:
- IDebugSymbolSearchEvent2
ms.assetid: 9b946d55-ff85-44eb-b40a-efbf8282eafd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cbe99422e506fb86b0a7e1d9d3242783f3258e6a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718785"
---
# <a name="idebugsymbolsearchevent2"></a>IDebugSymbolSearchEvent2
Diese Schnittstelle wird von der Debug-Engine (de) gesendet, um anzugeben, dass die Debugsymbole für ein Modul, das gedebuggt wird, geladen wurden.

## <a name="syntax"></a>Syntax

```
IDebugSymbolSearchEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die de implementiert diese Schnittstelle, um zu melden, dass die Symbole eines Moduls geladen wurden. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) -Schnittstelle muss auf demselben Objekt wie diese Schnittstelle implementiert werden. Der SDM verwendet [QueryInterface](/cpp/atl/queryinterface) für den Zugriff auf die- `IDebugEvent2` Schnittstelle.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Das de-Objekt erstellt und sendet dieses Ereignis Objekt, um zu melden, dass die Symbole eines Moduls geladen wurden. Das Ereignis wird mithilfe der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) -Rückruffunktion gesendet, die von der SDM bereitgestellt wird, wenn Sie an das Programm angefügt wird, das gedeppt wird.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die- `IDebugSymbolSearchEvent2` Schnittstelle macht die folgende Methode verfügbar.

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)|Ruft Informationen zu den Ergebnissen einer Symbol Suche ab.|

## <a name="remarks"></a>Bemerkungen
 Dieses Ereignis wird auch dann gesendet, wenn die Symbole nicht geladen werden konnten. `IDebugSymbolSearchEvent2::GetSymbolSearchInfo`Durch Aufrufen von kann der Handler dieses Ereignisses ermitteln, ob das Modul tatsächlich über Symbole verfügt.

 Visual Studio verwendet dieses Ereignis in der Regel, um den Status geladener Symbole im Fenster **Module** zu aktualisieren.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
