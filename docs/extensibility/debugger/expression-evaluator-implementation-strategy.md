---
title: "Strategie für die Implementierung von Expression Evaluator | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 48b871eeccb5ff561ef4b95689f12a9f58302bc9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="expression-evaluator-implementation-strategy"></a>Strategie für die Implementierung von Expression Evaluator
> [!IMPORTANT]
>  In Visual Studio 2015 wird diese Möglichkeit zum Implementieren von ausdruckauswertung veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Eine Möglichkeit, schnell eine ausdrucksauswertung (EE) erstellen, implementieren Sie zunächst die erforderliche zum Anzeigen von lokaler Variablen im Code wird die **"lokal"** Fenster. Es ist sinnvoll, beachten Sie, die jede Zeile in der **"lokal"** Fenster zeigt die Namen, Typ und Wert einer lokalen Variablen und alle drei dargestellte ein [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) Objekt. Der Name, Typ und Wert einer lokalen Variablen können von abgerufen werden ein `IDebugProperty2` Objekt durch Aufrufen seiner [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) Methode. Weitere Informationen zur Vorgehensweise beim Anzeigen von lokaler Variablen in der **"lokal"** Fenster finden Sie unter [anzeigen "lokal"](../../extensibility/debugger/displaying-locals.md).  
  
## <a name="discussion"></a>Diskussion  
 Eine mögliche Implementierung Sequenz beginnt bei der Implementierung von [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). Die [analysieren](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) und [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) Methoden müssen implementiert werden, um "lokal" anzuzeigen. Aufrufen `IDebugExpressionEvaluator::GetMethodProperty` gibt eine `IDebugProperty2` -Objekt, das eine Methode darstellt: d. h. eine [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) Objekt. Methoden selbst werden nicht angezeigt, der **"lokal"** Fenster.  
  
 Die [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) Methode sollte als Nächstes implementiert werden. Debugging-Modul (DE) ruft diese Methode, um eine Liste von lokalen Variablen und Argumenten durch Übergabe abrufen `IDebugProperty2::EnumChildren` eine `guidFilter` Argument `guidFilterLocalsPlusArgs`. `IDebugProperty2::EnumChildren`Aufrufe [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) und [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), Zusammenfassen der Ergebnisse in einer einzelnen-Enumeration. Finden Sie unter [anzeigen "lokal"](../../extensibility/debugger/displaying-locals.md) Weitere Details.  
  
## <a name="see-also"></a>Siehe auch  
 [Implementieren eine Ausdrucksauswertung](../../extensibility/debugger/implementing-an-expression-evaluator.md)   
 [Anzeigen von lokalen Variablen](../../extensibility/debugger/displaying-locals.md)