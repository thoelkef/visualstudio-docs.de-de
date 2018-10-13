---
title: Evaluierungskontext | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0bce0ea65aa025d7250c49b5d91f8d075a9720aa
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49253278"
---
# <a name="evaluation-context"></a>Auswertungskontext
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Wenn die Debug-Engine (DE) die ausdrucksauswertung (EE) aufruft, drei Argumente übergeben, um [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) den Kontext für Suchen und Auswerten von Symbolen, zu bestimmen, wie in der folgenden Tabelle gezeigt.  
  
## <a name="arguments"></a>Argumente  
  
|Argument|Beschreibung|  
|--------------|-----------------|  
|`pSymbolProvider`|Ein [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) Schnittstelle, die der Symbol-Handler (SH) gibt, verwendet werden soll, um das Symbol zu identifizieren.|  
|`pAddress`|Ein [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) Schnittstelle, die dem aktuellen Zeitpunkt der Ausführung angibt. Dies kann verwendet werden, um die Methode zu suchen, die den ausgeführten Code enthält.|  
|`pBinder`|Ein [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) -Schnittstelle, die verwendet werden kann, um den Wert und Typ eines Symbols, das anhand des Namens zu finden.|  
  
 `IDebugParsedExpression::EvaluateSync` Gibt eine [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) Schnittstelle, die den sich ergebenden Wert und seinen Typ darstellt.  
  
## <a name="see-also"></a>Siehe auch  
 [Wichtige Schnittstellen für die Ausdrucksauswertung](../../extensibility/debugger/key-expression-evaluator-interfaces.md)   
 [Anzeigen von lokalen Variablen](../../extensibility/debugger/displaying-locals.md)   
 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

