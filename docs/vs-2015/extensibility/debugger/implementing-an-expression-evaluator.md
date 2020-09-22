---
title: Implementieren einer Ausdrucks Auswertung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e82e6f1fb4e6f78c7fb1f614144f9a836d9676fb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840913"
---
# <a name="implementing-an-expression-evaluator"></a>Implementieren einer Ausdrucksauswertung
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Das Auswerten eines Ausdrucks ist ein komplexes Zusammenspiel zwischen der Debug-Engine (de), dem Symbol Anbieter (SP), dem Binder Objekt und der Ausdrucks Auswertung (EE) selbst. Diese vier Komponenten sind Durchschnitt stellen verbunden, die von einer Komponente implementiert und von einer anderen Komponente genutzt werden.  
  
 Der EE nimmt einen Ausdruck aus der de in Form einer Zeichenfolge an und analysiert oder wertet ihn aus. Der EE implementiert die folgenden Schnittstellen, die von de verwendet werden:  
  
- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
  Der EE Ruft das Binder Objekt auf, das von der de zur Verfügung gestellt wird, um den Wert von Symbolen und Objekten zu erhalten. Der EE verwendet die folgenden Schnittstellen, die von der de implementiert werden:  
  
- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)  
  
- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)  
  
- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)  
  
- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)  
  
- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)  
  
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
  Der EE implementiert [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md). `IDebugProperty2` stellt den Mechanismus bereit, mit dem das Ergebnis einer Ausdrucks Auswertung (z. b. eine lokale Variable, ein primitiv oder ein Objekt) für Visual Studio beschrieben wird. daraufhin **werden die entsprechenden**Informationen im Fenster Lokal, **Überwachung**oder **direkt** angezeigt.  
  
  Die SP wird dem ee von der "de" übergeben, wenn Sie Informationen anfordert. Der SP implementiert Schnittstellen, die Adressen und Felder beschreiben, wie z. b. die folgenden Schnittstellen und deren Ableitungen:  
  
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)  
  
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
  Der EE nutzt alle diese Schnittstellen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Implementierungsstrategie für die Ausdrucksauswertung](../../extensibility/debugger/expression-evaluator-implementation-strategy.md)  
 Definiert einen dreistufigen Prozess für die Strategie zur Implementierung der Ausdrucks Auswertung (EE Auswertung, EE).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schreiben einer CLR-Ausdrucksauswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
