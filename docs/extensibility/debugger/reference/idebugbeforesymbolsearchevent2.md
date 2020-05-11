---
title: IDebugBeforeSymbolSearchEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBeforeSymbolSearchEvent2 interface
ms.assetid: 679fd7b1-765a-41a8-a046-63240c09a499
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9d6f3f78e165ba2f4453131b7b459e3061243ff6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736114"
---
# <a name="idebugbeforesymbolsearchevent2"></a>IDebugBeforeSymbolSearchEvent2
Das Debugmodul (DE) sendet diese Schnittstelle an den Sitzungsdebug-Manager (SDM), um die Statusleistenmeldung während des Symbolladens festzulegen.

## <a name="syntax"></a>Syntax

```
IDebugBeforeSymbolSearchEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die DE implementiert diese Schnittstelle, wenn sie die Statusleistenmeldung während des Symbolladens festlegen muss. Diese Schnittstelle wird nur von Debugmodulen implementiert, die mit Skriptinterpretern arbeiten oder Teil von Skriptinterpretern sind. Die [IDebugEvent2-Schnittstelle](../../../extensibility/debugger/reference/idebugevent2.md) muss auf demselben Objekt wie diese Schnittstelle implementiert werden (das SDM verwendet **QueryInterface,** um auf die **IDebugEvent2-Schnittstelle** zuzugreifen).

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Die DE erstellt und sendet dieses Ereignisobjekt, wenn es die Statusleistenmeldung während des Symbolladens festlegen muss. Das Ereignis wird mithilfe der [IDebugEventCallback2-Rückruffunktion](../../../extensibility/debugger/reference/idebugeventcallback2.md) gesendet, die vom SDM bereitgestellt wird, wenn es an das zu debuggende Programm angefügt wird.

## <a name="methods"></a>Methoden
 Die folgende Tabelle zeigt `IDebugBeforeSymbolSearchEvent2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetModuleName](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2-getmodulename.md)|Ruft den Namen des Moduls ab, das gerade gedebuggt wird.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
