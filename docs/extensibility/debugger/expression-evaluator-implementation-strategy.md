---
title: Implementierungsstrategie für Ausdrucksevaluator | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3922689c20c839b3c0c2b2440bc9fefd5d25c80a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738671"
---
# <a name="expression-evaluator-implementation-strategy"></a>Implementierungsstrategie für Ausdrucksevaluator
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucksevaluatoren veraltet. Informationen zum Implementieren von CLR-Ausdrucksevaluatoren finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Beispiel für den Auswertungsbeispiel für managed expression evaluator](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Ein Ansatz zum schnellen Erstellen eines Ausdrucksevaluators (EE) besteht darin, zunächst den Minimalcode zu implementieren, der erforderlich ist, um lokale Variablen im **Locals-Fenster** anzuzeigen. Es ist nützlich zu erkennen, dass jede Zeile im **Fenster Locals** den Namen, typ und Denwert einer lokalen Variablen anzeigt und dass alle drei durch ein [IDebugProperty2-Objekt](../../extensibility/debugger/reference/idebugproperty2.md) dargestellt werden. Der Name, der Typ und der Wert `IDebugProperty2` einer lokalen Variablen werden von einem Objekt abgerufen, indem die [GetPropertyInfo-Methode](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) aufgerufen wird. Weitere Informationen zum Anzeigen lokaler Variablen im Fenster **Locals** finden Sie unter [Anzeigen von Locals](../../extensibility/debugger/displaying-locals.md).

## <a name="discussion"></a>Diskussion
 Eine mögliche Implementierungssequenz beginnt mit der Implementierung von [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). Die [Methoden Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) und [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) müssen implementiert werden, um Locals anzuzeigen. Beim `IDebugExpressionEvaluator::GetMethodProperty` Aufrufen `IDebugProperty2` wird ein Objekt zurückgegeben, das eine Methode darstellt, d. h. ein [IDebugMethodField-Objekt.](../../extensibility/debugger/reference/idebugmethodfield.md) Methoden selbst werden im **Fenster "Locals"** nicht angezeigt.

 Die [EnumChildren-Methode](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) sollte als Nächstes implementiert werden. Das Debugmodul (DE) ruft diese Methode auf, um `IDebugProperty2::EnumChildren` eine `guidFilter` Liste `guidFilterLocalsPlusArgs`lokaler Variablen und Argumente abzudateien, indem ein Argument von übergeben wird. `IDebugProperty2::EnumChildren`ruft [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) und [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)auf, die die Ergebnisse in einer einzigen Enumeration kombinieren. Weitere Informationen finden Sie unter [Lokale anzeigen.](../../extensibility/debugger/displaying-locals.md)

## <a name="see-also"></a>Weitere Informationen
- [Implementieren eines Ausdrucksevaluators](../../extensibility/debugger/implementing-an-expression-evaluator.md)
- [Lokale anzeigen](../../extensibility/debugger/displaying-locals.md)
