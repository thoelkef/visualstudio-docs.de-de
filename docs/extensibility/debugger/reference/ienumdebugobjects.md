---
title: IEnumDebugObjects | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects
helpviewer_keywords:
- IEnumDebugObjects interface
ms.assetid: 0950364c-6c8a-4b6c-ba37-c6aa359fa72c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c04409fb695613fea5d54b285946c04719fbe5b0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716265"
---
# <a name="ienumdebugobjects"></a>IEnumDebugObjects
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucksevaluatoren veraltet. Informationen zum Implementieren von CLR-Expressionsevaluatoren finden Sie unter [CLR Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) and [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Diese Schnittstelle stellt eine Auflistung von Objekten dar, die die [IDebugObject-Schnittstelle](../../../extensibility/debugger/reference/idebugobject.md) implementieren.

## <a name="syntax"></a>Syntax

```
IEnumDebugObjects : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Der Ausdrucksauswertungswert implementiert diese Schnittstelle, um Objektsätze bereitzustellen, die die [IDebugObject-Schnittstelle](../../../extensibility/debugger/reference/idebugobject.md) implementieren. Beachten Sie, dass dies keine Standard-COM-Enumeration aufgrund des Vorhandenseins der [GetCount-Methode](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md) ist.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
- [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md) gibt diese Schnittstelle zurück.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Diese Schnittstelle implementiert die folgenden Methoden.

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Weiter](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|Ruft den nächsten Satz von [IDebugObject-Objekten](../../../extensibility/debugger/reference/idebugobject.md) aus der Enumeration ab.|
|[Überspringen](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|Überspringt eine angegebene Anzahl von Einträgen.|
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|Setzt die Enumeration auf den ersten Eintrag zurück.|
|[Klon](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md)|Ruft eine Kopie der aktuellen Enumeration ab.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|Ruft die Anzahl der Einträge in der Enumeration ab.|

## <a name="remarks"></a>Bemerkungen
 Diese Schnittstelle ermöglicht es einem Debugmodul, über eine Reihe von Objekten in einem Array aufzuzählen.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)
