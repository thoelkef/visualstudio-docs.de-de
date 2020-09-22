---
title: Auswertungs Kontext | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7dae6ddcb0c75f0dcbc2207465aed522a4210159
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841275"
---
# <a name="evaluation-context"></a>Auswertungskontext
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Wenn die Debug-Engine (de) die Ausdrucks Auswertung (EE) aufruft, bestimmen drei an [evaluatesync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) weiter gegebene Argumente den Kontext zum Suchen und Auswerten von Symbolen, wie in der folgenden Tabelle dargestellt.  
  
## <a name="arguments"></a>Argumente  
  
|Argument|BESCHREIBUNG|  
|--------------|-----------------|  
|`pSymbolProvider`|Eine [idebugsymbolprovider](../../extensibility/debugger/reference/idebugsymbolprovider.md) -Schnittstelle, die den Symbol Handler (SH) angibt, der zum Identifizieren des Symbols verwendet werden soll.|  
|`pAddress`|Eine [idebugaddress](../../extensibility/debugger/reference/idebugaddress.md) -Schnittstelle, die den aktuellen Ausführungs Punkt angibt. Dies kann verwendet werden, um die Methode zu suchen, die den ausgeführten Code enthält.|  
|`pBinder`|Eine [idebugbinder](../../extensibility/debugger/reference/idebugbinder.md) -Schnittstelle, die verwendet werden kann, um den Wert und den Typ eines Symbols anhand seines Namens zu suchen.|  
  
 `IDebugParsedExpression::EvaluateSync` gibt eine [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) -Schnittstelle zurück, die den resultierenden Wert und seinen Typ darstellt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schnittstellen für die Schlüssel Ausdrucks Auswertung](../../extensibility/debugger/key-expression-evaluator-interfaces.md)   
 [Anzeigen von lokalen Variablen](../../extensibility/debugger/displaying-locals.md)   
 [Evaluatesync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)   
 [Idebugsymbolprovider](../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [Idebugaddress](../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)
