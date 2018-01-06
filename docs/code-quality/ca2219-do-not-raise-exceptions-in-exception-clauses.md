---
title: "CA2219: Keine Ausnahmen in Ausnahmeklauseln auslösen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
helpviewer_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
ms.assetid: 7b9b0bee-4e8e-49a4-8c40-52142b49061f
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8c5a4ee1d4425b3967928171648453a631aea815
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219: Keine Ausnahmen in Ausnahmeklauseln auslösen
|||  
|-|-|  
|TypeName|DoNotRaiseExceptionsInExceptionClauses|  
|CheckId|CA2219|  
|Kategorie|Microsoft.Usage|  
|Unterbrechende Änderung|Wichtige nicht unterbrechende Änderung|  
  
## <a name="cause"></a>Ursache  
 Eine Ausnahme wird ausgelöst, aus einer `finally`, Filter- oder Fault-Klausel.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Wenn eine Ausnahme in einer Ausnahmeklausel ausgelöst wird, wird die Schwierigkeit des Debuggens erheblich erhöht.  
  
 Wenn eine Ausnahme ausgelöst wird, einem `finally` oder Fault-Klausel, der neuen Ausnahme verdeckt die aktive Ausnahme, falls vorhanden. Dies ist der ursprüngliche Fehler schwer zu erkennen und zu debuggen.  
  
 Wenn eine Ausnahme in einer Filterklausel ausgelöst wird, die Laufzeit automatisch fängt die Ausnahme ab, und bewirkt, dass den Filter auf "false" ausgewertet. Es gibt keine Möglichkeit, um den Unterschied zwischen der Filter auswerten auf "false" und eine Ausnahme, die von einem Filter ausgelöst wird. Dies ist schwer zu erkennen und Debuggen von Fehlern in die Filterlogik.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um diese Verstoß gegen diese Regel zu beheben, führen Sie nicht explizit löst eine Ausnahme aus einer `finally`, Filter- oder Fault-Klausel.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel. Es gibt keine Szenarien, die unter denen eine Ausnahme ausgelöst, die in einer Ausnahmeklausel an einen Vorteil gegenüber dem ausgeführten Code enthält.  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1065: Keine Ausnahmen an unerwarteten Speicherorten auslösen](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Entwurfswarnungen](../code-quality/design-warnings.md)