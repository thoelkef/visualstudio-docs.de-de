---
title: IDebugSymbolSearchEvent2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolSearchEvent2
helpviewer_keywords:
- IDebugSymbolSearchEvent2
ms.assetid: 9b946d55-ff85-44eb-b40a-efbf8282eafd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ed7108c9e1349b01115bed8a6b2a77a3eaa71f45
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66320389"
---
# <a name="idebugsymbolsearchevent2"></a>IDebugSymbolSearchEvent2
Diese Schnittstelle wird von der Debug-Engine (DE) gesendet, um anzugeben, dass die Debugsymbole für ein Modul, das im Debugmodus befindlichen geladen wurden.

## <a name="syntax"></a>Syntax

```
IDebugSymbolSearchEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die DE implementiert diese Schnittstelle, um zu melden, dass es sich bei einem Modul die Symbole geladen wurden. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) Schnittstelle muss auf dasselbe Objekt wie diese Schnittstelle implementiert werden. Wird verwendet, das SDM [QueryInterface](/cpp/atl/queryinterface) für den Zugriff auf die `IDebugEvent2` Schnittstelle.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Die DE erstellt und sendet dieses Ereignisobjekt zum Berichten des Moduls Symbole geladen wurden. Das Ereignis gesendet wird, mithilfe der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Callback-Funktion, die durch die SDM bereitgestellt wird, wenn diese an die zu debuggende Programm wird angefügt.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die `IDebugSymbolSearchEvent2` Schnittstelle verfügbar macht, die folgende Methode.

|Methode|Beschreibung|
|------------|-----------------|
|[GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)|Ruft Informationen zu den Ergebnissen einer Suche Symbol ab.|

## <a name="remarks"></a>Hinweise
 Dieses Ereignis wird gesendet werden, auch wenn die Symbole konnte nicht geladen werden. Aufrufen von `IDebugSymbolSearchEvent2::GetSymbolSearchInfo` , kann der Handler, der dieses Ereignis, um zu bestimmen, ob das Modul tatsächlich keine Symbole.

 Visual Studio verwendet dieses Ereignis in der Regel beim Aktualisieren des Status der geladenen Symbole in der **Module** Fenster.

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)