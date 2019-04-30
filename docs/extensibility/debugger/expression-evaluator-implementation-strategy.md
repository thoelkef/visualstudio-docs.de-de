---
title: Implementierungsstrategie für die Ausdrucksauswertung | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1dabf4406752d04c0beec39d7f5997b09e3a5fc1
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63409886"
---
# <a name="expression-evaluator-implementation-strategy"></a>Implementierungsstrategie für die ausdrucksauswertung
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zum Implementieren von CLR-ausdrucksauswertungen finden Sie unter [CLR ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Auswertung (Beispiel) verwaltete Ausdruck](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Ein Ansatz zum schnellen Erstellen einer ausdrucksauswertung (EE) ist, implementieren Sie zunächst den Code mindestens erforderlich ist, zum Anzeigen von lokaler Variablen in der **"lokal"** Fenster. Es empfiehlt sich Folgendes beachtet werden: jede Zeile in der **"lokal"** Fenster zeigt die Namen, Typ und Wert einer lokalen Variablen, und alle drei durch dargestellt eine [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) Objekt. Der Name, Typ und Wert einer lokalen Variablen aus einer eine `IDebugProperty2` -Objekt durch Aufrufen der [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) Methode. Weitere Informationen zur Vorgehensweise beim Anzeigen von lokaler Variablen in der **"lokal"** Fenster finden Sie unter [anzeigen "lokal"](../../extensibility/debugger/displaying-locals.md).

## <a name="discussion"></a>Diskussion
 Eine mögliche Implementierung Sequenz beginnt bei der Implementierung von [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). Die [analysieren](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) und [von GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) Methoden implementiert werden müssen, um lokale Variablen anzuzeigen. Aufrufen von `IDebugExpressionEvaluator::GetMethodProperty` gibt ein `IDebugProperty2` -Objekt, das eine Methode darstellt:, also eine [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) Objekt. Methoden selbst werden nicht angezeigt, der **"lokal"** Fenster.

 Die [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) Methode sollte als Nächstes implementiert werden. Die Debug-Engine (DE) ruft diese Methode zum Abrufen von einer Liste von lokalen Variablen und Argumenten übergeben `IDebugProperty2::EnumChildren` eine `guidFilter` Argument `guidFilterLocalsPlusArgs`. `IDebugProperty2::EnumChildren` Aufrufe [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) und [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), kombinieren die Ergebnisse in einer einzelnen Enumeration. Finden Sie unter ["lokal" zeigt](../../extensibility/debugger/displaying-locals.md) Weitere Details.

## <a name="see-also"></a>Siehe auch
- [Implementieren einer ausdrucksauswertung](../../extensibility/debugger/implementing-an-expression-evaluator.md)
- [Anzeige "lokal"](../../extensibility/debugger/displaying-locals.md)