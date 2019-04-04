---
title: 'CA1009: Ereignishandler korrekt deklarieren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1009
- DeclareEventHandlersCorrectly
helpviewer_keywords:
- CA1009
- DeclareEventHandlersCorrectly
ms.assetid: ab65c471-1449-49d2-9896-7b9af74284b4
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9f3764e7e7965fb9efe46a8404273de9adde4a34
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58959656"
---
# <a name="ca1009-declare-event-handlers-correctly"></a>CA1009: Ereignishandler korrekt deklarieren.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt ein Delegat, der zur Behandlung von Ereignissen geeignet ist. Die Methoden, die von diesem Ereignishandler aufgerufen werden können, entsprechen mit der Signatur, die in den Entwurfsrichtlinien angegeben wird. `AlarmEventHandler` ist der Typname des Delegaten. `AlarmEventArgs` leitet sich von der Basisklasse für die Ereignisdaten <xref:System.EventArgs>, und enthält alarm Ereignisdaten.

 [!code-cpp[FxCop.Design.EventsTwoParams#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/cpp/FxCop.Design.EventsTwoParams.cpp#1)]
 [!code-csharp[FxCop.Design.EventsTwoParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/cs/FxCop.Design.EventsTwoParams.cs#1)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/vb/FxCop.Design.EventsTwoParams.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2109: Sichtbare Ereignishandler überprüfen](../code-quality/ca2109-review-visible-event-handlers.md)

## <a name="see-also"></a>Siehe auch
 <xref:System.EventArgs?displayProperty=fullName> <xref:System.Object?displayProperty=fullName>
 [NIB: Ereignisse und Delegaten](http://msdn.microsoft.com/d98fd58b-fa4f-4598-8378-addf4355a115)
