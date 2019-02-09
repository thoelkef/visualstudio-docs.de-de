---
title: 'CA2219: Keine Ausnahmen in Ausnahmeklauseln auslösen.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
helpviewer_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
ms.assetid: 7b9b0bee-4e8e-49a4-8c40-52142b49061f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6a644cf3dc934676a14f1c5c59a6582fcd45ae7d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55941152"
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219: Keine Ausnahmen in Ausnahmeklauseln auslösen.

|||
|-|-|
|TypeName|DoNotRaiseExceptionsInExceptionClauses|
|CheckId|CA2219|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechend, wichtige|

## <a name="cause"></a>Ursache
 Eine Ausnahme wird ausgelöst, von einem `finally`, filtern oder Fault-Klausel.

## <a name="rule-description"></a>Regelbeschreibung
 Wenn eine Ausnahme in einer Ausnahmeklausel ausgelöst wird, wird die Schwierigkeit des Debuggens erheblich vergrößert.

 Wenn eine Ausnahme ausgelöst wird, einem `finally` oder Fault-Klausel, verbirgt die neue Ausnahme die aktive Ausnahme, falls vorhanden. Dadurch wird den ursprünglichen Fehler schwer zu erkennen und zu debuggen.

 Wenn in einer Filterklausel eine Ausnahme ausgelöst wird, die Runtime automatisch fängt die Ausnahme ab und führt dazu, dass den Filter auf "false" ausgewertet. Es ist keine Möglichkeit, um den Unterschied zwischen der Filter auswerten auf "false" eine Ausnahme wird von einem Filter ausgelöst. Dadurch wird es schwierig ist, um zu erkennen und Debuggen von Fehlern in der Filterlogik.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um diese Verstoß gegen diese Regel zu beheben, keine explizit auslösen eine Ausnahme eine `finally`, filtern oder Fault-Klausel.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie eine Warnung für diese Regel. Es gibt keine Szenarios, die unter denen eine Ausnahme, die in-Ausnahmeklausel eine ausgelöst, einen Vorteil für die Ausführung von Code bereitstellt.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1065: Keine Ausnahmen an unerwarteten Speicherorten auslösen](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)

## <a name="see-also"></a>Siehe auch
 [Entwurfswarnungen](../code-quality/design-warnings.md)