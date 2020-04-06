---
title: IDebugEngine3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3
helpviewer_keywords:
- IDebugEngine3 interface
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7026156eac7f60e7435e32244c3cc03ae5f08e1e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730650"
---
# <a name="idebugengine3"></a>IDebugEngine3
Stellt ein einzelnes Debugmodul (DE) dar, das das Debuggen eines oder mehrerer Module steuert.

## <a name="syntax"></a>Syntax

```
IDebugEngine3 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird von einer benutzerdefinierten DE implementiert (wenn sie Symbole unterstützt), um den JustMyCode-Status zu aktivieren. Diese Schnittstelle muss von der DE implementiert werden, wenn sie Symbole und JustMyCode unterstützt.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Diese Schnittstelle wird vom Sitzungsdebug-Manager (SDM) aufgerufen, um Benutzeroptionen für Speicherorte weiterzugeben, von denen Symbole geladen werden sollen. Es wird auch aufgerufen, die GUID des Moduls festzulegen, wenn es instanziiert wird (diese GUID basiert auf den Metriken aus dem Zeitpunkt der Motorregistrierung). Das SDM ruft diese Schnittstelle auch auf, um den JustMyCode-Status festzulegen und alle vom Debugger bekannten Ausnahmen auf einen angegebenen Zustand festzulegen.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den methoden, die von [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)geerbt wurden, macht die `IDebugEngine3` Schnittstelle die folgenden Methoden verfügbar.

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|Legt den Pfad oder die Pfade fest, die de zum Suchen nach Debugsymbolen verwendet.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|Lädt die Symbole für alle Module, deren Symbole noch nicht geladen wurden.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|Teilt die DE die JustMyCode-Informationen mit.|
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|Legt die DE-GUID aus den Metriken fest.|
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|Legen Sie alle derzeit ausstehenden Ausnahmen auf einen angegebenen Status fest.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
