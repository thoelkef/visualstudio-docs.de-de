---
title: Ändern des Werts eines Lokalen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 98e40e4b6ea10bb6ff1242f23f1b6dd83ce0c0cd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739137"
---
# <a name="change-the-value-of-a-local"></a>Ändern des Werts eines lokalen
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucksevaluatoren veraltet. Informationen zum Implementieren von CLR-Ausdrucksevaluatoren finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Beispiel für den Auswertungsbeispiel für managed expression evaluator](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Wenn ein neuer Wert in das Wertfeld des **Locals-Fensters** eingegeben wird, übergibt das Debugpaket die Zeichenfolge als typisiert an den Ausdrucksevaluator (EE). Der EE wertet diese Zeichenfolge aus, die entweder einen einfachen Wert oder einen Ausdruck enthalten kann, und speichert den resultierenden Wert im zugeordneten lokalen.

 Dies ist ein Überblick über den Prozess der Änderung des Wertes eines lokalen:

1. Nachdem der Benutzer den neuen Wert eingibt, ruft Visual Studio [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) für das [IDebugProperty2-Objekt auf,](../../extensibility/debugger/reference/idebugproperty2.md) das dem lokalen Objekt zugeordnet ist.

2. `IDebugProperty2::SetValueAsString` führt die folgenden Aufgaben durch:

   1. Wertet die Zeichenfolge aus, um einen Wert zu erzeugen.

   2. Bindet das zugeordnete [IDebugField-Objekt,](../../extensibility/debugger/reference/idebugfield.md) um ein [IDebugObject-Objekt](../../extensibility/debugger/reference/idebugobject.md) abzuerhalten.

   3. Konvertiert den Wert in eine Reihe von Bytes.

   4. Ruft [SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md) auf, um die Bytes des Werts in den Arbeitsspeicher zu übertragen, damit das zu debuggende Programm darauf zugreifen kann.

3. Visual Studio aktualisiert die **Locals-Anzeige** (Details finden Sie unter [Anzeigen von Locals).](../../extensibility/debugger/displaying-locals.md)

   Diese Prozedur wird auch verwendet, um den Wert einer Variablen `IDebugProperty2` im **Überwachungsfenster** zu ändern, außer es `IDebugProperty2` ist das Objekt, das dem Wert des lokalen objektassoziiert ist, das anstelle des Objekts verwendet wird, das dem lokalen Objekt selbst zugeordnet ist.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Beispielimplementierung sich ändernder Werte](../../extensibility/debugger/sample-implementation-of-changing-values.md) Verwendet das MyCEE-Beispiel, um den Prozess der Werteänderung zu durchlaufen.

## <a name="see-also"></a>Weitere Informationen
- [Schreiben eines CLR-Ausdrucksevaluators](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Anzeigen von Einheimischen](../../extensibility/debugger/displaying-locals.md)
