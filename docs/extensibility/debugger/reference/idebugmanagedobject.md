---
title: IDebugManagedObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject
helpviewer_keywords:
- IDebugManagedObject interface
ms.assetid: 3ae09d34-112c-4285-80ee-9f7f8dc414d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6fbd270aa1b65f05f308d41d22f154fb53b8833d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727693"
---
# <a name="idebugmanagedobject"></a>IDebugManagedObject
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucksevaluatoren veraltet. Informationen zum Implementieren von CLR-Expressionsevaluatoren finden Sie unter [CLR Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) and [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Diese Schnittstelle ermöglicht es dem Ausdrucksevaluator (EE), Eigenschaften oder `System.Decimal`Methoden für Wertklasseninstanzen aufzurufen (z. B. ) und deren Wert festzulegen, ohne [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) für das zu debuggende Programm aufzurufen.

## <a name="syntax"></a>Syntax

```
IDebugManagedObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein Ausdrucksauswertungswert implementiert diese Schnittstelle, um ein verwaltetes Codeobjekt wie eine Variable darzustellen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Um diese Schnittstelle abzurufen, rufen Sie [GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md) für ein [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) auf, das eine Instanz einer Wertklasse darstellt.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den von [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)geerbten Methoden macht die `IDebugManagedObject` Schnittstelle die folgenden Methoden verfügbar.

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-getmanagedobject.md)|Gibt eine Schnittstelle zurück, die das verwaltete Codeobjekt darstellt und von der eine entsprechende verwaltete Codeschnittstelle abgerufen werden kann.|
|[SetFromManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-setfrommanagedobject.md)|Legt den Wert dieses Objekts auf den Wert eines angegebenen verwalteten Codeobjekts fest.|

## <a name="remarks"></a>Bemerkungen
 Ein Ausdrucksauswertungswert verwendet diese Schnittstelle, um ein verwaltetes Codeobjekt in einer Analysestruktur zu speichern.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [Auswerten](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)
