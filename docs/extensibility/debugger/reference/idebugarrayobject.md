---
title: IDebugArrayObject | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject
helpviewer_keywords:
- IDebugArrayObject method
ms.assetid: a1c8e77e-dee1-4748-a516-6ab032a8f54f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f5943aae9fb8ef848bdaeecdebc0f1354be2c0e7
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56697077"
---
# <a name="idebugarrayobject"></a>IDebugArrayObject
> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Diese Schnittstelle stellt ein Arrayobjekt dar.

## <a name="syntax"></a>Syntax

```
IDebugArrayObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die ausdrucksauswertung implementiert diese Schnittstelle, um ein Array darstellen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Die [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Schnittstelle kann diese Schnittstelle abrufen, indem Sie mithilfe von [QueryInterface](/cpp/atl/queryinterface) , wenn das Objekt ein Array darstellt.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den Methoden für die `IDebugObject` -Schnittstelle, die folgenden Methoden werden implementiert, auf die `IDebugArrayObject` Schnittstelle.

|Methode|Beschreibung|
|------------|-----------------|
|[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)|Ruft die Anzahl der Elemente im Array ab.|
|[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)|Ruft ein Element des Arrays ab.|
|[GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)|Ruft alle Elemente des Arrays ab.|
|[GetRank](../../../extensibility/debugger/reference/idebugarrayobject-getrank.md)|Ruft den Rang des Arrays ab.|
|[GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)|Ruft die Dimensionen des Arrays ab.|

## <a name="remarks"></a>Hinweise
 Eine ausdrucksauswertung verwendet diese Schnittstelle, um Arrays in eine Analysestruktur darzustellen.

## <a name="requirements"></a>Anforderungen
 Header: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)