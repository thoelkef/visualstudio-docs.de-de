---
title: Anzeigen von Locals | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4d44b276aeb9c6acb0ef34cc186662d49246de7d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738933"
---
# <a name="display-locals"></a>Lokale anzeigen
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucksevaluatoren veraltet. Informationen zum Implementieren von CLR-Ausdrucksevaluatoren finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Beispiel für den Auswertungsbeispiel für managed expression evaluator](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Die Ausführung erfolgt immer im Kontext einer Methode, die auch als enthaltende Methode oder aktuelle Methode bezeichnet wird. Wenn die Ausführung angehalten wird, ruft Visual Studio das Debugmodul (DE) auf, um eine Liste lokaler Variablen und Argumente abzudateien, die gemeinsam als Locals der Methode bezeichnet werden. Visual Studio zeigt diese Locals und ihre Werte im Fenster **Locals** an.

 Um Locals anzuzeigen, ruft die DE die [GetMethodProperty-Methode](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) auf, die zum EE gehört, und gibt ihr einen Evaluierungskontext, d. h. einen Symbolanbieter (SP), die aktuelle Ausführungsadresse und ein Binderobjekt. Weitere Informationen finden Sie unter [Evaluierungskontext](../../extensibility/debugger/evaluation-context.md). Wenn der Aufruf erfolgreich `IDebugExpressionEvaluator::GetMethodProperty` ist, gibt die Methode ein [IDebugProperty2-Objekt](../../extensibility/debugger/reference/idebugproperty2.md) zurück, das die Methode darstellt, die die aktuelle Ausführungsadresse enthält.

 Die DE ruft [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) auf, um ein [IEnumDebugPropertyInfo2-Objekt](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) abzuruft, das gefiltert wird, um nur Locals zurückzugeben und aufzuzählen, um eine Liste [von DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) Strukturen zu erstellen. Jede Struktur enthält den Namen, den Typ und den Wert eines lokalen Orts. Der Typ und der Wert werden als formatierte Zeichenfolgen gespeichert, die für die Anzeige geeignet sind. Name, Typ und Wert werden in der Regel zusammen in einer Zeile des **Fensters "Locals"** angezeigt.

> [!NOTE]
> In den **Fenstern QuickWatch** und **Watch** werden auch Variablen mit demselben Format von Name, Wert und Typ angezeigt. Diese Werte werden jedoch durch Aufrufen von `IDebugProperty2::EnumChildren` [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) anstelle von ermittelt.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Beispielimplementierung von Locals](../../extensibility/debugger/sample-implementation-of-locals.md) Verwendet Beispiele, um den Prozess der Implementierung von Locals zu durchlaufen.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Evaluierungskontext](../../extensibility/debugger/evaluation-context.md) Erläutert, dass das Debugmodul (DE) beim Aufrufen des Ausdrucksevaluators (EE) drei Argumente übergibt.

## <a name="see-also"></a>Weitere Informationen
 [Schreiben eines CLR-Ausdrucksevaluators](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
