---
title: IDebugPointerObject | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject
helpviewer_keywords:
- IDebugPointerObject interface
ms.assetid: 257fa167-b46e-4ffb-9a12-272efbf26702
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c884f2794031d92add956bf4364824165ee1edfb
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66343927"
---
# <a name="idebugpointerobject"></a>IDebugPointerObject
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Diese Schnittstelle stellt ein Zeigerobjekt.

## <a name="syntax"></a>Syntax

```
IDebugPointerObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die ausdrucksauswertung implementiert diese Schnittstelle, um ein Zeigerobjekt darstellen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Die [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Schnittstelle kann diese Schnittstelle abrufen, indem Sie mithilfe von [QueryInterface](/cpp/atl/queryinterface) Wenn die `IDebugObject` stellt einen Zeiger dar.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den von geerbten Methoden [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), `IDebugPointerObject` Schnittstelle verfügbar macht, die folgenden Methoden.

|Methode|Beschreibung|
|------------|-----------------|
|[Dereference](../../../extensibility/debugger/reference/idebugpointerobject-dereference.md)|Ruft das Objekt ab, das die Schnittstelle verweist.|
|[GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)|Ruft den Wert, den die Schnittstelle als eine Reihe von aufeinander folgenden Bytes verweist.|
|[SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)|Legt den Wert, den die Schnittstelle aus einer Reihe von aufeinander folgenden Bytes verweist.|

## <a name="remarks"></a>Hinweise
 Eine ausdrucksauswertung verwendet diese Schnittstelle, um einen Zeiger in eine Analysestruktur darzustellen.

## <a name="requirements"></a>Anforderungen
 Header: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Schnittstellen für die Ausdrucksauswertung](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)