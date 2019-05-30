---
title: IEnumDebugObjects | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects
helpviewer_keywords:
- IEnumDebugObjects interface
ms.assetid: 0950364c-6c8a-4b6c-ba37-c6aa359fa72c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dea4b4781fd8026c29436bbd37a6bfa6824e73b3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66339481"
---
# <a name="ienumdebugobjects"></a>IEnumDebugObjects
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Diese Schnittstelle stellt eine Auflistung von Objekten, die Implementierung der [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Schnittstelle.

## <a name="syntax"></a>Syntax

```
IEnumDebugObjects : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die ausdrucksauswertung implementiert diese Schnittstelle zum Bereitstellen von Gruppen von Objekten, das Implementieren der [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Schnittstelle. Beachten Sie, dass dies keine standard-COM-Enumeration durch das Vorhandensein der [GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md) Methode.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
- [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md) dieser Schnittstelle zurück.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Diese Schnittstelle implementiert die folgenden Methoden.

|Methode|Beschreibung|
|------------|-----------------|
|[Nächste](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|Ruft den nächsten Satz von [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Objekte aus der Enumeration.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|Überspringt eine angegebene Anzahl von Einträgen.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|Setzt die Enumeration an den ersten Eintrag zurück.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md)|Ruft eine Kopie der aktuellen Enumeration.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|Ruft die Anzahl der Einträge in der Enumeration ab.|

## <a name="remarks"></a>Hinweise
 Diese Schnittstelle ermöglicht eine Debug-Engine einen Satz von Objekten in einem Array durchlaufen.

## <a name="requirements"></a>Anforderungen
 Header: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)