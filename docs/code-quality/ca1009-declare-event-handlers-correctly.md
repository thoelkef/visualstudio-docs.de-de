---
title: 'CA1009: Ereignishandler korrekt deklarieren.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1009
- DeclareEventHandlersCorrectly
helpviewer_keywords:
- CA1009
- DeclareEventHandlersCorrectly
ms.assetid: ab65c471-1449-49d2-9896-7b9af74284b4
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a98ec47688f289fadba66401aca9fcee7b602cdc
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923568"
---
# <a name="ca1009-declare-event-handlers-correctly"></a>CA1009: Ereignishandler korrekt deklarieren.

|||
|-|-|
|TypeName|DeclareEventHandlersCorrectly|
|CheckId|CA1009|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
Ein Delegat, der ein öffentliches oder geschütztes Ereignis behandelt, weist nicht die richtige Signatur, den Rückgabetyp oder die richtigen Parameternamen auf.

## <a name="rule-description"></a>Regelbeschreibung
Ereignishandlermethoden nehmen zwei Parameter an. Der erste ist vom Typ <xref:System.Object?displayProperty=fullName> und hat den Namen "Sender". Dies ist das Objekt, durch das das Ereignis ausgelöst wurde. Der zweite Parameter ist vom Datentyp <xref:System.EventArgs?displayProperty=fullName> und hat den Namen "e". Dies sind die Daten, die dem Ereignis zugeordnet sind. Wenn das Ereignis beispielsweise ausgelöst wird, wenn eine Datei geöffnet wird, enthalten die Ereignisdaten in der Regel den Namen der Datei.

Ereignishandlermethoden sollten keinen Wert zurückgeben. In der C# Programmiersprache wird dies durch den Rückgabetyp `void`angegeben. Ein Ereignishandler kann mehrere Methoden in mehreren Objekten aufrufen. Wenn die Methoden einen Wert zurückgeben können, werden mehrere Rückgabewerte für jedes Ereignis auftreten, und nur der Wert der letzten aufgerufenen Methode wäre verfügbar.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, korrigieren Sie die Signatur, den Rückgabetyp oder die Parameternamen des Delegaten. Weitere Informationen finden Sie im folgenden Beispiel.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt einen Delegaten, der für die Behandlung von Ereignissen geeignet ist. Die Methoden, die von diesem Ereignishandler aufgerufen werden können, entsprechen der Signatur, die in den Entwurfs Richtlinien angegeben ist. `AlarmEventHandler`der Typname des Delegaten. `AlarmEventArgs`wird von der-Basisklasse für Ereignisdaten <xref:System.EventArgs>abgeleitet und enthält Alarmereignis Daten.

[!code-cpp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CPP/ca1009-declare-event-handlers-correctly_1.cpp)]
[!code-csharp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CSharp/ca1009-declare-event-handlers-correctly_1.cs)]
[!code-vb[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/VisualBasic/ca1009-declare-event-handlers-correctly_1.vb)]

## <a name="related-rules"></a>Verwandte Regeln
[CA2109: Sichtbare Ereignishandler überprüfen](../code-quality/ca2109-review-visible-event-handlers.md)

## <a name="see-also"></a>Siehe auch

- <xref:System.EventArgs?displayProperty=fullName>
- <xref:System.Object?displayProperty=fullName>
- [Behandeln und Auswerfen von Ereignissen](/dotnet/standard/events/index)