---
title: Implementierungsstrategie für die Ausdrucksauswertung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9bb9135dda7b5c8240517efabb3a899022ba1d3d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47509428"
---
# <a name="expression-evaluator-implementation-strategy"></a>Implementierungsstrategie für die Ausdrucksauswertung
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Implementierungsstrategie für die Ausdrucksauswertung](https://docs.microsoft.com/visualstudio/extensibility/debugger/expression-evaluator-implementation-strategy).  
  
> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Ein Ansatz zum schnellen Erstellen einer ausdrucksauswertung (EE) ist, implementieren Sie zunächst den Code mindestens erforderlich ist, zum Anzeigen von lokaler Variablen in der **"lokal"** Fenster. Es empfiehlt sich Folgendes beachtet werden: jede Zeile in der **"lokal"** Fenster zeigt die Namen, Typ und Wert einer lokalen Variablen, und alle drei durch dargestellt eine [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) Objekt. Der Name, Typ und Wert einer lokalen Variablen können entnommen werden ein `IDebugProperty2` -Objekt durch Aufrufen der [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) Methode. Weitere Informationen zur Vorgehensweise beim Anzeigen von lokaler Variablen in der **"lokal"** Fenster finden Sie unter [anzeigen "lokal"](../../extensibility/debugger/displaying-locals.md).  
  
## <a name="discussion"></a>Diskussion  
 Eine mögliche Implementierung Sequenz beginnt bei der Implementierung von [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). Die [analysieren](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) und [von GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) müssen Methoden implementiert werden, um "lokal" angezeigt. Aufrufen von `IDebugExpressionEvaluator::GetMethodProperty` gibt ein `IDebugProperty2` -Objekt, das eine Methode darstellt:, also eine [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) Objekt. Methoden selbst werden nicht angezeigt, der **"lokal"** Fenster.  
  
 Die [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) Methode sollte als Nächstes implementiert werden. Die Debug-Engine (DE) ruft diese Methode zum Abrufen von einer Liste von lokalen Variablen und Argumenten übergeben `IDebugProperty2::EnumChildren` eine `guidFilter` Argument `guidFilterLocalsPlusArgs`. `IDebugProperty2::EnumChildren` Aufrufe [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) und [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), kombinieren die Ergebnisse in einer einzelnen Enumeration. Finden Sie unter [anzeigen "lokal"](../../extensibility/debugger/displaying-locals.md) Weitere Details.  
  
## <a name="see-also"></a>Siehe auch  
 [Implementieren einer Ausdrucksauswertung](../../extensibility/debugger/implementing-an-expression-evaluator.md)   
 [Anzeigen von lokalen Variablen](../../extensibility/debugger/displaying-locals.md)

