---
title: IDebugFunctionObject | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject
helpviewer_keywords:
- IDebugFunctionObject interface
ms.assetid: 8d94e97c-a9d1-400c-8a98-a44b5385b33a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5fb0d969268e7765abe5c3ebdc9fc000a10a3aa0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313447"
---
# <a name="idebugfunctionobject"></a>IDebugFunctionObject
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Diese Schnittstelle stellt eine Funktion dar.

## <a name="syntax"></a>Syntax

```
IDebugFunctionObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Eine ausdrucksauswertung implementiert diese Schnittstelle, um die Funktion dar.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Diese Schnittstelle ist eine Spezialisierung der [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) -Schnittstelle und wird über [QueryInterface](/cpp/atl/queryinterface) auf die `IDebugObject` Schnittstelle.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den von geerbten Methoden [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), `IDebugFunctionObject` Schnittstelle verfügbar macht, die folgenden Methoden.

|Methode|Beschreibung|
|------------|-----------------|
|[CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)|Erstellt ein Objekt des primitiven Datentyps.|
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)|Erstellt ein Objekt, das über einen Konstruktor.|
|[CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)|Erstellt ein Objekt mit keinen Konstruktor.|
|[CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)|Erstellt ein Arrayobjekt.|
|[CreateStringObject](../../../extensibility/debugger/reference/idebugfunctionobject-createstringobject.md)|Erstellt ein String-Objekt.|
|[Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)|Ruft die Funktion und der resultierende Wert als Objekt zurückgegeben.|

## <a name="remarks"></a>Hinweise
 Diese Schnittstelle ermöglicht die ausdrucksauswertung zur Darstellung von Funktionen in eine Analysestruktur. Die `Create` Methoden in dieser Schnittstelle werden verwendet, um das Erstellen von Objekten, die die Eingabeparameter der Methode darstellen. Die Funktion kann dann ausgeführt werden, durch den Aufruf der [auswerten](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) -Methode, die gibt ein Objekt, das den Rückgabewert der Funktion darstellt.

## <a name="requirements"></a>Anforderungen
 Header: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Schnittstellen für die Ausdrucksauswertung](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)