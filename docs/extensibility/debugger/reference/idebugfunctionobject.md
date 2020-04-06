---
title: IDebugFunctionObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject
helpviewer_keywords:
- IDebugFunctionObject interface
ms.assetid: 8d94e97c-a9d1-400c-8a98-a44b5385b33a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6433c1f2c540b040a3b3beccc264377e69592387
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728488"
---
# <a name="idebugfunctionobject"></a>IDebugFunctionObject
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucksevaluatoren veraltet. Informationen zum Implementieren von CLR-Expressionsevaluatoren finden Sie unter [CLR Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) and [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Diese Schnittstelle stellt eine Funktion dar.

## <a name="syntax"></a>Syntax

```
IDebugFunctionObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein Ausdrucksauswertungsgeber implementiert diese Schnittstelle, um eine Funktion darzustellen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Diese Schnittstelle ist eine Spezialisierung der [IDebugObject-Schnittstelle](../../../extensibility/debugger/reference/idebugobject.md) und `IDebugObject` wird mithilfe von [QueryInterface](/cpp/atl/queryinterface) auf der Schnittstelle abgerufen.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den von [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)geerbten Methoden macht die `IDebugFunctionObject` Schnittstelle die folgenden Methoden verfügbar.

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)|Erstellt ein primitives Datenobjekt.|
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)|Erstellt ein Objekt mit einem Konstruktor.|
|[CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)|Erstellt ein Objekt ohne Konstruktor.|
|[CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)|Erstellt ein Arrayobjekt.|
|[CreateStringObject](../../../extensibility/debugger/reference/idebugfunctionobject-createstringobject.md)|Erstellt ein Zeichenfolgenobjekt.|
|[Auswerten](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)|Ruft die Funktion auf und gibt den resultierenden Wert als Objekt zurück.|

## <a name="remarks"></a>Bemerkungen
 Diese Schnittstelle ermöglicht es dem Ausdrucksevaluator, Funktionen in einer Analysestruktur darzustellen. Die `Create` Methoden in dieser Schnittstelle werden verwendet, um Objekte zu erstellen, die die Eingabeparameter für die Methode darstellen. Die Funktion kann dann ausgeführt werden, indem die [Evaluate-Methode](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) aufgerufen wird, die ein Objekt zurückgibt, das den Rückgabewert der Funktion darstellt.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
