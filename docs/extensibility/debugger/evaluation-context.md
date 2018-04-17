---
title: Evaluierungskontext | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 266fe85bedeea2c7e3dae7726d113d66a4b2b1e8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="evaluation-context"></a>Evaluierungskontext
> [!IMPORTANT]
>  In Visual Studio 2015 wird diese Möglichkeit zum Implementieren von ausdruckauswertung veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Wenn die Debugging-Modul (DE) die ausdrucksauswertung (EE) aufruft, werden drei Argumente zu übergeben [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) den Kontext zum Suchen und Auswerten von Symbolen zu bestimmen, wie in der folgenden Tabelle gezeigt.  
  
## <a name="arguments"></a>Argumente  
  
|Argument|Beschreibung|  
|--------------|-----------------|  
|`pSymbolProvider`|Ein [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) Schnittstelle, die der Symbol-Handler (SH) gibt an, die verwendet werden, um das Symbol zu identifizieren.|  
|`pAddress`|Ein [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) -Schnittstelle, die den aktuellen Zeitpunkt der Ausführung angibt. Dies kann verwendet werden, um die Methode suchen, die den ausgeführten Code enthält.|  
|`pBinder`|Ein [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) -Schnittstelle, die verwendet werden kann, um den Wert und Typ eines Symbols mit dem angegebenen Namen gefunden.|  
  
 `IDebugParsedExpression::EvaluateSync` Gibt eine [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) Schnittstelle, die der resultierende Wert und dessen Typ darstellt.  
  
## <a name="see-also"></a>Siehe auch  
 [Schlüsselausdruck Evaluator-Schnittstellen](../../extensibility/debugger/key-expression-evaluator-interfaces.md)   
 [Anzeigen von "lokal"](../../extensibility/debugger/displaying-locals.md)   
 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)