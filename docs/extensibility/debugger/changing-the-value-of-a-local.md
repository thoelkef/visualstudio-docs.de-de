---
title: Ändern des Werts eines lokalen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf90a2c03112cb2d3a935a9721f455ec976803c7
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60041742"
---
# <a name="change-the-value-of-a-local"></a>Ändern Sie den Wert eines lokalen Elements
> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Auswertung (Beispiel) verwaltete Ausdruck](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Wenn ein neuer Wert eingegeben wird, klicken Sie im Feld mit Wert der **"lokal"** Fenster, das debugpaket übergibt die Zeichenfolge wie eingegeben werden, um die ausdrucksauswertung (EE). Die EE wertet diese Zeichenfolge, die kann entweder einen einfachen Wert oder einen Ausdruck enthalten, und speichert den resultierenden Wert in der zugehörigen lokalen.

 Dies ist eine Übersicht über den Prozess zum Ändern des Werts eines lokalen Elements:

1. Nachdem der neue Wert eingegeben wurde, ruft Visual Studio [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) auf die [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) Objekt, mit der lokalen verknüpft ist.

2. `IDebugProperty2::SetValueAsString` führt folgende Ausgaben aus:

   1. Wertet die Zeichenfolge, um einen Wert zu erzeugen.

   2. Bindet das zugeordnete [IDebugField](../../extensibility/debugger/reference/idebugfield.md) Objekt zum Abrufen einer [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) Objekt.

   3. Konvertiert den Wert in eine Reihe von Bytes an.

   4. Aufrufe [SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md) den Wert des Bytes in den Arbeitsspeicher eingefügt wird, damit das derzeit debuggte Programm darauf zugreifen kann.

3. Visual Studio aktualisiert die **"lokal"** anzuzeigen (finden Sie unter [anzeigen "lokal"](../../extensibility/debugger/displaying-locals.md) Einzelheiten).

   Dieses Verfahren dient auch zum Ändern des Werts einer Variablen in der **Überwachen** Fenster mit der Ausnahme ist die `IDebugProperty2` Objekt verknüpft ist, mit dem Wert der lokalen, die anstelle von verwendet wird die `IDebugProperty2` Objekt verknüpft ist, mit der lokalen sich selbst.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Beispiel für die Implementierung Ändern der Werte](../../extensibility/debugger/sample-implementation-of-changing-values.md) im MyCEE-Beispiel verwendet, um den Prozess des Umschaltens Werte zu durchlaufen.

## <a name="see-also"></a>Siehe auch
- [Schreiben Sie eine CLR-ausdrucksauswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Anzeigen von lokalen Variablen](../../extensibility/debugger/displaying-locals.md)