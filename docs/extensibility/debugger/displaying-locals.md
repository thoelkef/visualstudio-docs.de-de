---
title: Anzeigen von lokalen Variablen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ea6345ef56cec8e3a7d90ed964c320f96fdbcdcd
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56711240"
---
# <a name="display-locals"></a>Anzeige "lokal"
> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zum Implementieren von CLR-ausdrucksauswertungen finden Sie unter [CLR ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Auswertung (Beispiel) verwaltete Ausdruck](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Ausführung immer findet im Kontext einer Methode, auch bekannt als der enthaltenden Methode oder die aktuelle Methode. Wenn die Ausführung angehalten wird, ruft Visual Studio die Debug-Engine (DE), um eine Liste der lokalen Variablen abzurufen und Argumente bezeichnen die lokalen Variablen der Methode. Visual Studio zeigt an, diese lokalen Variablen und deren Werte in der **"lokal"** Fenster.

 Um lokal zu anzuzeigen, die DE Ruft die [von GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) Methode die EE und weist ihm ein Evaluierungskontext wird, das ist, ein symbolanbieter (SP), die aktuelle Ausführung-Adresse und ein binderobjekt. Weitere Informationen finden Sie unter [Evaluierungskontext](../../extensibility/debugger/evaluation-context.md). Wenn der Aufruf erfolgreich ist, die `IDebugExpressionEvaluator::GetMethodProperty` Methode gibt ein [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) Objekt, das die Methode darstellt, die die aktuelle Ausführung Adresse enthält.

 Die DE-Aufrufe [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) zum Abrufen einer [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) Objekt, das gefiltert, damit nur lokale Variablen zurückgegeben wird, und aufgelistet, um eine Liste der [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md)Strukturen. Jede Struktur enthält die Namen, Typ und Wert eines lokalen Elements. Der Typ und Wert werden als geeignet für die Anzeige formatierte Zeichenfolgen gespeichert. Der Name, Typ und Wert sind in der Regel zusammen in einer einzigen Codezeile angezeigt der **"lokal"** Fenster.

> [!NOTE]
>  Die **Schnellüberwachung** und **Watch** Windows auch Variablen mit dem gleichen Format der Namen, Wert und Typ angezeigt. Allerdings werden diese Werte durch den Aufruf abgerufen [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) anstelle von `IDebugProperty2::EnumChildren`.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Beispiel für die Implementierung der lokalen Variablen](../../extensibility/debugger/sample-implementation-of-locals.md) werden Beispiele verwendet, um den Prozess der Implementierung von "lokal" zu durchlaufen.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Evaluierungskontext](../../extensibility/debugger/evaluation-context.md) wird erklärt, dass wenn die Debug-Engine (DE) die ausdrucksauswertung (EE) aufruft, er drei Argumente übergibt.

## <a name="see-also"></a>Siehe auch
 [Schreiben Sie eine CLR-ausdrucksauswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)