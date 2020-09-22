---
title: Idebugparamein dexpression | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugParsedExpression
helpviewer_keywords:
- IDebugParsedExpression interface
ms.assetid: be6486ed-b070-4898-95b1-58581bcb4447
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4756a346cc059b1f80aba98439b993ac84f1136f
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/07/2020
ms.locfileid: "90841138"
---
# <a name="idebugparsedexpression"></a>IDebugParsedExpression
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Diese Schnittstelle stellt einen analysierten Ausdruck dar, der für die Auswertung bereit ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugParsedExpression : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Eine Ausdrucks Auswertung implementiert diese Schnittstelle, um einen analysierten Ausdruck darzustellen, der für die Auswertung bereit ist.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 [Bei einem](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) aufzurufenden Befehl wird diese Schnittstelle zurückgegeben.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 In der folgenden Tabelle wird die-Methode von gezeigt `IDebugParsedExpression` .  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)|Wertet den analysierten Ausdruck aus.|  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn der Aufrufer zum Auswerten des Ausdrucks bereit ist, ruft er [evaluatesync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) auf, um ein [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) -Objekt zurückzugeben, das das Ergebnis der Auswertung enthält. Dieser zweiteilige Ansatz zum Auswerten, analysieren und Auswerten von ermöglicht es, dass der analysierte Ausdruck mehrmals ausgewertet wird, wobei der zeitaufwändige Prozess der Analyse des Ausdrucks umgangen wird.  
  
## <a name="requirements"></a>Anforderungen  
 Header: EE. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Analysieren](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)   
 [Evaluatesync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
