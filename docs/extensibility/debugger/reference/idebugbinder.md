---
title: IDebugBinder | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugBinder
helpviewer_keywords:
- IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: f3377ade8cc4301e1d8a5be19c5d828755934ce9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugbinder"></a>IDebugBinder
> [!IMPORTANT]
>  In Visual Studio 2015 wird diese Möglichkeit zum Implementieren von ausdruckauswertung veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Diese Schnittstelle bindet ein Symbolfeld, in der Regel von den Symbol-Anbieter für einen Speicherkontext oder ein Objekt, das den aktuellen Symbolwert enthält zurückgegeben.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugBinder : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Diese Schnittstelle unterstützt die Auswertung von Ausdrücken und muss von der Debugging-Modul (DE) implementiert werden.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Diese Schnittstelle wird verwendet, bei der Auswertung von Ausdrücken und wird normalerweise verwendet, in der Implementierung der [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) und [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md).  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugBinder`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Binden](../../../extensibility/debugger/reference/idebugbinder-bind.md)|Ruft ab, die Arbeitsspeicher-Kontext oder ein Objekt, das den aktuellen Symbolwert enthält.|  
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|Bestimmt den Laufzeittyp eines Objekts an.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|Konvertiert eine Objektadresse Speicherort oder Speicher für einen Speicherkontext.|  
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|Ruft eine [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) Objekt verwendet, um Funktionsparameter zu erstellen.|  
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|Ruft den genauen Typ für eine Variable ab.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Schnittstelle gibt zurück, dass Objekte, die in der ausdrucksauswertung verwendeten Strukturen analysieren. Die ausdrucksauswertung wertet einen Ausdruck mit dem Symbol-Anbieter konvertieren Sie die Symbole im Ausdruck auf Instanzen von [IDebugField](../../../extensibility/debugger/reference/idebugfield.md), die jedes Symbol im Hinblick auf seine Typ und den Ort im Quellcode beschreiben. Die [binden](../../../extensibility/debugger/reference/idebugbinder-bind.md) -Methode konvertiert `IDebugField` -Objekte [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Objekte, die eine Verbindung herstellen, oder binden ein Symbol zu geben, um einen tatsächlichen Wert im Arbeitsspeicher. Diese `IDebugObject` werden dann in eine Analysestruktur für die spätere Auswertung gespeichert.  
  
## <a name="requirements"></a>Anforderungen  
 Header: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Ausdruck Auswertung Schnittstellen](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)