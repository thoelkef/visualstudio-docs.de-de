---
title: 'CA2219: Keine Ausnahmen in Ausnahmeklauseln auslösen'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4403ab65be60000bc758cf1a127e6b589c764702
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53857707"
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219: Keine Ausnahmen in Ausnahmeklauseln auslösen

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