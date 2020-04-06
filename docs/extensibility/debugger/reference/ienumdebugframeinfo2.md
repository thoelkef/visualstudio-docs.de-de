---
title: IEnumDebugFrameInfo2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFrameInfo2
helpviewer_keywords:
- IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0aa67792ced94afd9c4439cbc6ea577e6b85f28b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716609"
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
Diese Schnittstelle zählt [FRAMEINFO-Strukturen](../../../extensibility/debugger/reference/frameinfo.md) auf.

## <a name="syntax"></a>Syntax

```
IEnumDebugFrameInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Das Debugmodul (DE) implementiert diese Schnittstelle, um eine Liste von Strukturen bereitzustellen, die die aktuelle Aufrufliste beschreiben.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Visual Studio ruft [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) auf, um diese Schnittstelle zu erhalten, wenn ein Haltepunkt, eine Ausnahme oder ein Anhalten in einem zu debuggenden Programm auftritt.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IEnumDebugFrameInfo2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Weiter](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|Ruft eine angegebene Anzahl von [FRAMEINFO-Strukturen](../../../extensibility/debugger/reference/frameinfo.md) in einer Enumerationssequenz ab.|
|[Überspringen](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|Überspringt eine angegebene Anzahl von [FRAMEINFO-Strukturen](../../../extensibility/debugger/reference/frameinfo.md) in einer Enumerationssequenz.|
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|
|[Klon](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|Erstellt einen Enumerator, der denselben Enumerationsstatus wie der aktuelle Enumerator enthält.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|Ruft die Anzahl der [FRAMEINFO-Strukturen](../../../extensibility/debugger/reference/frameinfo.md) in einem Enumerator ab.|

## <a name="remarks"></a>Bemerkungen
 Visual Studio ruft diese Schnittstelle als ersten Schritt zum Behandeln eines Haltepunkts, einer Ausnahme oder einer benutzergenerierten Pause für das zu debuggende Programm ab. Die Liste der [FRAMEINFO-Strukturen](../../../extensibility/debugger/reference/frameinfo.md) stellt die aktuelle Aufrufliste dar, wobei der aktuelle Funktionsaufruf am Anfang der Liste und der älteste Funktionsaufruf am Ende der Liste angezeigt wird. Jeder `FRAMEINFO` stellt einen Stapelrahmen dar, einen Kontext, in dem Ausdrücke ausgewertet und lokale Variablen betrachtet werden können.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
