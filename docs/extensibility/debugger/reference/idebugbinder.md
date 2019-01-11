---
title: IDebugBinder | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBinder
helpviewer_keywords:
- IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d0e425a1790c2452e56061c8f4adee3c473e4b58
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53859254"
---
# <a name="idebugbinder"></a>IDebugBinder
> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Diese Schnittstelle bindet ein Symbolfeld, in der Regel zurückgegeben wird, durch die symbolanbieter, um einen Speicherkontext oder ein Objekt, das das Symbol für den aktuellen Wert enthält.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugBinder : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Diese Schnittstelle unterstützt die Auswertung von Ausdrücken und muss von der Debug-Engine (DE) implementiert werden.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Diese Schnittstelle wird verwendet, während der Auswertung des Ausdrucks und wird normalerweise verwendet, bei der Implementierung der [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) und [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md).  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugBinder`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)|Ruft den Speicherkontext oder das Objekt, das das Symbol für den aktuellen Wert enthält.|  
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|Bestimmt den Laufzeittyp eines Objekts an.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|Konvertiert eine Objekt Speicherort oder Arbeitsspeicher-Adresse für einen Speicherkontext.|  
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|Ruft eine [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) Objekt verwendet, um Funktionsparameter zu erstellen.|  
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|Ruft den exakten Typ für eine Variable ab.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Schnittstelle gibt zurück, dass von der ausdrucksauswertung in verwendeten Objekte Strukturen analysieren. Die ausdrucksauswertung wertet einen Ausdruck mit dem symbolanbieter konvertieren Sie die Symbole in den Ausdruck auf Instanzen von [IDebugField](../../../extensibility/debugger/reference/idebugfield.md), welche jedes Symbol im Hinblick auf seine Typ und die Position im Quellcode beschreiben. Die [binden](../../../extensibility/debugger/reference/idebugbinder-bind.md) Methode konvertiert `IDebugField` Objekte [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Geben Sie die Objekte, die eine Verbindung herstellen, oder binden ein Symbol in einen tatsächlichen Wert im Arbeitsspeicher. Diese `IDebugObject` Objekte werden dann in eine Analysestruktur für die spätere Auswertung gespeichert.  
  
## <a name="requirements"></a>Anforderungen  
 Header: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen für die Ausdrucksauswertung](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)