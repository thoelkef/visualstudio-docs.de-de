---
title: Implementierungsstrategie der Ausdrucks Auswertung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a9c2ded111c371fc1a42c8f1ee08769f5b06aeda
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841219"
---
# <a name="expression-evaluator-implementation-strategy"></a>Implementierungsstrategie für die Ausdrucksauswertung
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucks auswergratoren veraltet. Weitere Informationen zum Implementieren von CLR-Ausdrucks Auswerters finden Sie unter [CLR-Ausdrucks](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) Auswertungen und [Beispiel für verwaltete Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Ein Ansatz zum schnellen Erstellen eines Ausdrucks Auswerters (EE) besteht darin, zuerst den minimalen Code zu implementieren, der erforderlich ist, um lokale Variablen **im Fenster "** lokal" anzuzeigen. Es ist hilfreich zu wissen, dass jede Zeile im **Fenster "** lokal" den Namen, den Typ und den Wert einer lokalen Variablen anzeigt und alle drei durch ein [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) -Objekt dargestellt werden. Der Name, der Typ und der Wert einer lokalen Variablen können `IDebugProperty2` durch Aufrufen der [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) -Methode von einem Objekt abgerufen werden. Weitere Informationen zum Anzeigen von lokalen Variablen **im Fenster "** lokal" finden Sie unter [anzeigen](../../extensibility/debugger/displaying-locals.md)von lokalen Variablen.  
  
## <a name="discussion"></a>Diskussion (Discussion)  
 Eine mögliche Implementierungs Sequenz beginnt mit der Implementierung von [idebugexpressionevaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). Die [Methoden](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) "Analyse" und " [getmethodproperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) " müssen implementiert werden, um lokale anzuzeigen. Beim Aufrufen von `IDebugExpressionEvaluator::GetMethodProperty` wird ein Objekt zurückgegeben `IDebugProperty2` , das eine Methode darstellt, d. h. ein [idebugmethodfield](../../extensibility/debugger/reference/idebugmethodfield.md) -Objekt. Die Methoden selbst werden nicht **im Fenster "** lokal" angezeigt.  
  
 Die [enumchildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) -Methode sollte als Nächstes implementiert werden. Die Debug-Engine (de) ruft diese Methode auf, um eine Liste der lokalen Variablen und Argumente durch übergeben `IDebugProperty2::EnumChildren` eines- `guidFilter` Arguments von zu erhalten `guidFilterLocalsPlusArgs` . `IDebugProperty2::EnumChildren` Ruft [enumarguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) und [enumlocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)auf und kombiniert die Ergebnisse in einer einzelnen Enumeration. Weitere Informationen finden Sie unter [Anzeigen von lokalen](../../extensibility/debugger/displaying-locals.md) Variablen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Implementieren einer Ausdrucks Auswertung](../../extensibility/debugger/implementing-an-expression-evaluator.md)   
 [Anzeigen von lokalen Variablen](../../extensibility/debugger/displaying-locals.md)
