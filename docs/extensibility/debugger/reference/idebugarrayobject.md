---
title: IDebugArrayObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject
helpviewer_keywords:
- IDebugArrayObject method
ms.assetid: a1c8e77e-dee1-4748-a516-6ab032a8f54f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 709273b89d89759163acb725220d1092d33ad72f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736213"
---
# <a name="idebugarrayobject"></a>IDebugArrayObject
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucksevaluatoren veraltet. Informationen zum Implementieren von CLR-Expressionsevaluatoren finden Sie unter [CLR Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) and [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Diese Schnittstelle stellt ein Arrayobjekt dar.

## <a name="syntax"></a>Syntax

```
IDebugArrayObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Der Ausdrucksauswertungswert implementiert diese Schnittstelle, um ein Array darzustellen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Die [IDebugObject-Schnittstelle](../../../extensibility/debugger/reference/idebugobject.md) kann diese Schnittstelle mithilfe von [QueryInterface](/cpp/atl/queryinterface) abrufen, wenn das Objekt ein Array darstellt.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den Methoden `IDebugObject` auf der Schnittstelle werden `IDebugArrayObject` die folgenden Methoden auf der Schnittstelle implementiert.

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)|Ruft die Anzahl der Elemente im Array ab.|
|[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)|Ruft ein Element des Arrays ab.|
|[GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)|Ruft alle Elemente des Arrays ab.|
|[GetRank](../../../extensibility/debugger/reference/idebugarrayobject-getrank.md)|Ruft den Rang des Arrays ab.|
|[GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)|Ruft die Dimensionen des Arrays ab.|

## <a name="remarks"></a>Bemerkungen
 Ein Ausdrucksauswertungsgeber verwendet diese Schnittstelle, um Arrays in einer Analysestruktur darzustellen.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
