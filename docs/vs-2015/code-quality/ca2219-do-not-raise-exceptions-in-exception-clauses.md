---
title: 'CA2219: keine Ausnahmen in Ausnahmeklauseln auslöst | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
helpviewer_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
ms.assetid: 7b9b0bee-4e8e-49a4-8c40-52142b49061f
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 960c74625a04b209dc9aa251256e994517a3a52f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538527"
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219: Keine Ausnahmen in Ausnahmeklauseln auslösen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|DoNotRaiseExceptionsInExceptionClauses|
|CheckId|CA2219|
|Category|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechend, unterbrechen|

## <a name="cause"></a>Ursache
 Eine-Ausnahme wird von einer- `finally` , Filter-oder Fault-Klausel ausgelöst.

## <a name="rule-description"></a>Beschreibung der Regel
 Wenn eine Ausnahme in einer Exception-Klausel ausgelöst wird, erhöht Sie die Schwierigkeit des Debuggens erheblich.

 Wenn eine Ausnahme in einer- `finally` oder-Fehler Klausel ausgelöst wird, verbirgt die neue Ausnahme die aktive Ausnahme, falls vorhanden. Dadurch wird der ursprüngliche Fehler schwer zu erkennen und zu debuggen.

 Wenn eine Ausnahme in einer Filter Klausel ausgelöst wird, fängt die Laufzeit die Ausnahme automatisch ab und bewirkt, dass der Filter zu "false" ausgewertet wird. Es gibt keine Möglichkeit, den Unterschied zwischen dem Auswerten des Filters und einer Ausnahme, die von einem Filter ausgelöst wird, zu erkennen. Dadurch wird es schwierig, Fehler in der Logik des Filters zu erkennen und zu debuggen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um diesen Verstoß gegen diese Regel zu beheben, lösen Sie nicht explizit eine Ausnahme von einer- `finally` , Filter-oder Fault-Klausel aus.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung für diese Regel. Es gibt keine Szenarios, in denen eine Ausnahme, die in einer Exception-Klausel ausgelöst wird, den ausführenden Code als Vorteil bietet.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1065: Keine Ausnahmen an unerwarteten Speicherorten auslösen.](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)

## <a name="see-also"></a>Weitere Informationen
 [Entwurfs Warnungen](../code-quality/design-warnings.md)
