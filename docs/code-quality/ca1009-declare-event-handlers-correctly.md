---
title: 'CA1009: Ereignishandler korrekt deklarieren.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 900eca590a87cc45a2859becd4a6a70c09d57bc7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54990913"
---
# <a name="ca1009-declare-event-handlers-correctly"></a>CA1009: Ereignishandler korrekt deklarieren.

|||
|-|-|
|TypeName|DeclareEventHandlersCorrectly|
|CheckId|CA1009|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Delegat, der eine öffentliche oder geschützte Ereignisbehandlung muss nicht die richtige Signatur, Typ oder Namen zurückgeben.

## <a name="rule-description"></a>Regelbeschreibung
 Ereignishandlermethoden nehmen zwei Parameter an. Die erste ist vom Typ <xref:System.Object?displayProperty=fullName> und ist mit dem Namen "Sender". Dies ist das Objekt, durch das das Ereignis ausgelöst wurde. Der zweite Parameter ist vom Typ <xref:System.EventArgs?displayProperty=fullName> und trägt die Bezeichnung 'e'. Dies sind die Daten, die dem Ereignis zugeordnet sind. Wenn das Ereignis ausgelöst wird, wenn eine Datei geöffnet ist, enthält die Daten z. B. in der Regel den Namen der Datei.

 Ereignishandlermethoden sollten keinen Wert zurückgibt. In der Programmiersprache c# wird dies durch den Rückgabetyp angegeben `void`. Ein Ereignishandler kann mehrere Methoden in mehrere Objekte aufrufen. Wenn die Methoden zum Zurückgeben eines Werts zulässig wäre, würde würde die Rückgabe mehrerer Werte für jedes Ereignis auftreten, und nur der Wert der letzten Methode, die aufgerufen wurde verfügbar.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, korrigieren Sie die Signatur, Rückgabetyp oder Parameternamen des Delegaten. Weitere Informationen finden Sie im folgende Beispiel.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt ein Delegat, der zur Behandlung von Ereignissen geeignet ist. Die Methoden, die von diesem Ereignishandler aufgerufen werden können, entsprechen mit der Signatur, die in den Entwurfsrichtlinien angegeben wird. `AlarmEventHandler` ist der Typname des Delegaten. `AlarmEventArgs` leitet sich von der Basisklasse für die Ereignisdaten <xref:System.EventArgs>, und enthält alarm Ereignisdaten.

 [!code-cpp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CPP/ca1009-declare-event-handlers-correctly_1.cpp)]
 [!code-csharp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CSharp/ca1009-declare-event-handlers-correctly_1.cs)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/VisualBasic/ca1009-declare-event-handlers-correctly_1.vb)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2109: Sichtbare Ereignishandler überprüfen](../code-quality/ca2109-review-visible-event-handlers.md)

## <a name="see-also"></a>Siehe auch

- <xref:System.EventArgs?displayProperty=fullName>
- <xref:System.Object?displayProperty=fullName>
- [Behandeln und Auslösen von Ereignissen](/dotnet/standard/events/index)