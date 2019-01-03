---
title: Implementieren einer Ausdrucksauswertung | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d51762eb2d26c39eab5d803384adfed216e5bd89
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53882324"
---
# <a name="implement-an-expression-evaluator"></a>Implementieren einer ausdrucksauswertung
> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zum Implementieren von CLR-ausdrucksauswertungen finden Sie unter [CLR ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Auswertung (Beispiel) verwaltete Ausdruck](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Die Auswertung eines Ausdrucks ist ein komplexes Zusammenspiel zwischen die Debug-Engine (DE), die Symbol-Dienstanbieter (SP), das binderobjekt und die ausdrucksauswertung (EE). Diese vier Komponenten werden durch Schnittstellen verbunden, die durch eine Komponente implementiert und von einem anderen genutzt werden.  
  
 Die EE verwendet einen Ausdruck aus der DE in Form einer Zeichenfolge und analysiert und wertet es. Die EE führt die folgenden Schnittstellen, die von der DE genutzt werden:  
  
- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
  Die EE Ruft den binderobjekt, das vom DE, um den Wert der Symbole und Objekte abzurufen. Die EE verwendet die folgenden Schnittstellen, die von der DE implementiert werden:  
  
- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)  
  
- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)  
  
- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)  
  
- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)  
  
- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)  
  
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
  Führt die EE [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md). `IDebugProperty2` Stellt den Mechanismus bereit, beschreibt das Ergebnis der Auswertung eines Ausdrucks, z. B. eine lokale Variable, ein primitiver Typ oder ein Objekt, das Visual Studio, die die entsprechende Informationen in dann zeigt die **"lokal"**, **ansehen** , oder **direkt** Fenster.  
  
  Die SP wird durch die DE auf die EE gewährt, wenn Informationen aufgefordert wird. Schnittstellen, die Adressen und Felder, z. B. die folgenden Schnittstellen und zugehörige ableitungen beschreiben die gespeicherte Prozedur wird ausgeführt:  
  
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)  
  
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
  Die EE verbraucht jede dieser Schnittstellen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Implementierungsstrategie für die ausdrucksauswertung](../../extensibility/debugger/expression-evaluator-implementation-strategy.md)  
 Definiert einen dreistufigen Prozess für die Implementierungsstrategie für die ausdrucksauswertung (EE).  
  
## <a name="see-also"></a>Siehe auch  
 [Schreiben Sie eine CLR-ausdrucksauswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)