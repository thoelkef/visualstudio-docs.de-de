---
title: 'CA2219: Keine Ausnahmen in Ausnahmeklauseln auslösen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
helpviewer_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
ms.assetid: 7b9b0bee-4e8e-49a4-8c40-52142b49061f
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3f3ea7368026e2e120e877a8689319762fa2b55e
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "47524997"
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219: Keine Ausnahmen in Ausnahmeklauseln auslösen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [CA2219: keine Ausnahmen in Ausnahmeklauseln auslösen](https://docs.microsoft.com/visualstudio/code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses).

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

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie eine Warnung für diese Regel. Es gibt keine Szenarios, die unter denen eine Ausnahme, die in-Ausnahmeklausel eine ausgelöst, einen Vorteil für die Ausführung von Code bereitstellt.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1065: Keine Ausnahmen an unerwarteten Speicherorten auslösen](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)

## <a name="see-also"></a>Siehe auch
 [Entwurfswarnungen](../code-quality/design-warnings.md)



