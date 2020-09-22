---
title: Idebugbinder | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBinder
helpviewer_keywords:
- IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dc00c50e3c340ab0685ab1010c6e924e77a18a09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840864"
---
# <a name="idebugbinder"></a>IDebugBinder
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Diese Schnittstelle bindet ein Symbolfeld, das normalerweise vom Symbol Anbieter zurückgegeben wird, an einen Speicher Kontext oder ein Objekt, das den aktuellen Wert des Symbols enthält.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugBinder : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Diese Schnittstelle unterstützt die Auswertung von Ausdrücken und muss von der Debug-Engine (de) implementiert werden.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Diese Schnittstelle wird im Prozess der Ausdrucks Auswertung verwendet und wird in der Regel in der Implementierung von [evaluatesync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) und [evaluateasync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)verwendet.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugBinder` .  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[Zwick](../../../extensibility/debugger/reference/idebugbinder-bind.md)|Ruft den Arbeitsspeicher Kontext oder das Objekt ab, das den aktuellen Wert des Symbols enthält.|  
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|Bestimmt den Lauf Zeittyp eines Objekts.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|Konvertiert einen Objekt Speicherort oder eine Speicheradresse in einen Speicher Kontext.|  
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|Ruft ein [idebugfunctionobject](../../../extensibility/debugger/reference/idebugfunctionobject.md) -Objekt ab, das zum Erstellen von Funktionsparametern verwendet wird.|  
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|Ruft den genauen Typ für eine Variable ab.|  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Schnittstelle gibt Objekte zurück, die von der Ausdrucks Auswertung in Analyse Strukturen verwendet werden. Die Ausdrucks Auswertung analysiert einen Ausdruck mithilfe des Symbol Anbieters, um die Symbole im Ausdruck in Instanzen von [idebugfield](../../../extensibility/debugger/reference/idebugfield.md)zu konvertieren, in denen jedes Symbol in Bezug auf den Typ und die Position im Quellcode beschrieben wird. Die [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md) -Methode konvertiert `IDebugField` Objekte in [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) -Objekte, die einen Symboltyp mit einem tatsächlichen Wert im Arbeitsspeicher verbinden oder binden. Diese `IDebugObject` Objekte werden dann zur späteren Auswertung in einer Analyse Struktur gespeichert.  
  
## <a name="requirements"></a>Anforderungen  
 Header: EE. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausdrucks Bewertungs Schnittstellen](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [Evaluatesync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [Evaluateasync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
