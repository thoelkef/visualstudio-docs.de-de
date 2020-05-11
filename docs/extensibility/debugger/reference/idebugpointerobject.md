---
title: IDebugPointerObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject
helpviewer_keywords:
- IDebugPointerObject interface
ms.assetid: 257fa167-b46e-4ffb-9a12-272efbf26702
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4b28189b3f0a07a27f5e4478f64963a63d634db5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725491"
---
# <a name="idebugpointerobject"></a>IDebugPointerObject
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucksevaluatoren veraltet. Informationen zum Implementieren von CLR-Expressionsevaluatoren finden Sie unter [CLR Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) and [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Diese Schnittstelle stellt ein Zeigerobjekt dar.

## <a name="syntax"></a>Syntax

```
IDebugPointerObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Der Ausdrucksauswertungswert implementiert diese Schnittstelle, um ein Zeigerobjekt darzustellen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Die [IDebugObject-Schnittstelle](../../../extensibility/debugger/reference/idebugobject.md) kann diese Schnittstelle mithilfe `IDebugObject` von [QueryInterface](/cpp/atl/queryinterface) abrufen, wenn der einen Zeiger darstellt.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den von [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)geerbten Methoden macht die `IDebugPointerObject` Schnittstelle die folgenden Methoden verfügbar.

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Dereference](../../../extensibility/debugger/reference/idebugpointerobject-dereference.md)|Ruft das Objekt ab, auf das die Schnittstelle verweist.|
|[Getbytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)|Ruft den Wert ab, auf den die Schnittstelle als eine Reihe aufeinander folgender Bytes verweist.|
|[Setbytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)|Legt den Wert fest, auf den die Schnittstelle aus einer Reihe aufeinander folgender Bytes verweist.|

## <a name="remarks"></a>Bemerkungen
 Ein Ausdrucksauswertungswert verwendet diese Schnittstelle, um einen Zeiger in einer Analysestruktur darzustellen.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
