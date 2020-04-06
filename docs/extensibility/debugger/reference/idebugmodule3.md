---
title: IDebugModule3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3
helpviewer_keywords:
- IDebugModule3 interface
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84db1b672a9460ef3809162a2a1433f269796046
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726745"
---
# <a name="idebugmodule3"></a>IDebugModule3
Diese Schnittstelle stellt ein Modul dar, das alternative Positionen von Symbolen und JustMyCode-Zuständen unterstützt.

## <a name="syntax"></a>Syntax

```
IDebugModule3 : IDebugModule2
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Das Debugmodul (DE) implementiert diese Schnittstelle, um alternative Speicherorte von Symbolen zu unterstützen und mit JustMyCode-Zuständen zu arbeiten (eine Definition von "JustMyCode" finden Sie im [Visual Studio Debugger Glossary).](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md)

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Ein Aufruf von [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) gibt diese Schnittstelle zurück. Die DE sendet die [IDebugSymbolSearchEvent2-Schnittstelle](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) mithilfe der [Ereignismethode](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) an den Session Debug Manager (SDM). Außerdem gibt ein Aufruf von [QueryInterface](/cpp/atl/queryinterface) auf einer [IDebugModule2-Schnittstelle](../../../extensibility/debugger/reference/idebugmodule2.md) diese Schnittstelle zurück.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den Methoden auf der [IDebugModule2-Schnittstelle](../../../extensibility/debugger/reference/idebugmodule2.md) implementiert diese Schnittstelle die folgenden Methoden:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|Gibt eine Liste der Pfade zurück, die nach Symbolen gesucht wurden, und die Ergebnisse der Suche nach jedem Pfad.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|Lädt und initialisiert Symbole für das aktuelle Modul.|
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|Gibt das Flag zurück, das angibt, ob das Modul Benutzercode darstellt.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|Gibt an, ob das Modul als Benutzercode betrachtet werden soll oder nicht.|

## <a name="remarks"></a>Bemerkungen
 Visual Studio ist der typische Consumer dieser Schnittstelle.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
- [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)
