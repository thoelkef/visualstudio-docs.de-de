---
title: IDebugObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject
helpviewer_keywords:
- IDebugObject interface
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6801176964a47646f03091131e1be89cf63c97f8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726310"
---
# <a name="idebugobject"></a>IDebugObject
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucksevaluatoren veraltet. Informationen zum Implementieren von CLR-Expressionsevaluatoren finden Sie unter [CLR Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) and [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Diese Schnittstelle stellt ein Objekt dar, das der Binder erstellt, um die Werte von Symbolen und Ausdrücken zu kapseln.

## <a name="syntax"></a>Syntax

```
IDebugObject : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein Ausdrucksauswertungswert implementiert diese Schnittstelle, um ein Objekt darzustellen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Diese Schnittstelle ist die Basisklasse für alle Objekte, die der Ausdrucksauswertungsor in analysierten Ausdrücken verwendet. Sie wird durch einen Aufruf der [Bind-Methode](../../../extensibility/debugger/reference/idebugbinder-bind.md) zurückgegeben. [QueryInterface](/cpp/atl/queryinterface) ruft die spezialisierteren Schnittstellen von dieser Schnittstelle ab.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugObject`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|Ruft die Größe des Objekts ab.|
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|Ruft den Wert des Objekts als eine fortlaufende Reihe von Bytes ab.|
|[SetValue](../../../extensibility/debugger/reference/idebugobject-setvalue.md)|Legt den Wert des Objekts aus einer aufeinanderfolgenden Reihe von Bytes fest.|
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|Legt den Referenzwert dieses Objekts fest.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|Ruft den Speicherkontext ab, der die Adresse des Objektwerts darstellt.|
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|Erstellt eine Kopie des verwalteten Objekts im Adressraum des Debugmoduls.|
|[IsNullReference](../../../extensibility/debugger/reference/idebugobject-isnullreference.md)|Testet, ob es sich bei diesem Objekt um einen Nullverweis handelt.|
|[IsEqual](../../../extensibility/debugger/reference/idebugobject-isequal.md)|Vergleicht ein Objekt mit diesem Objekt.|
|[IsReadOnly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|Bestimmt, ob dieses Objekt schreibgeschützt ist.|
|[IsProxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|Bestimmt, ob es sich bei dem Objekt um einen transparenten Proxy handelt.|

## <a name="remarks"></a>Bemerkungen
 Der Ausdrucksauswertungswert verwendet diese Schnittstelle als Basisklasse, um Objekte in einer Analysestruktur darzustellen.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)
- [Binden](../../../extensibility/debugger/reference/idebugbinder-bind.md)
