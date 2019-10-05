---
title: 'CA2117: APTCA-Typen sollten nur APTCA-Basistypen erweitern.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2117
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
helpviewer_keywords:
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
- CA2117
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 832d2c9fc1d4b9138a7cd1bc39868b3c4bf1b814
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232643"
---
# <a name="ca2117-aptca-types-should-only-extend-aptca-base-types"></a>CA2117: APTCA-Typen sollten nur APTCA-Basistypen erweitern.

|||
|-|-|
|TypeName|AptcaTypesShouldOnlyExtendAptcaBaseTypes|
|CheckId|CA2117|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Ein öffentlicher oder geschützter Typ in einer Assembly mit dem <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> -Attribut erbt von einem Typ, der in einer Assembly deklariert ist, die nicht über das-Attribut verfügt.

## <a name="rule-description"></a>Regelbeschreibung

Standardmäßig werden öffentliche oder geschützte Typen in Assemblys mit starken Namen implizit durch eine [vererbe Anforderung](xref:System.Security.Permissions.SecurityAction#System_Security_Permissions_SecurityAction_InheritanceDemand) für volle Vertrauenswürdigkeit geschützt. Assemblys mit starkem Namen, <xref:System.Security.AllowPartiallyTrustedCallersAttribute> die mit dem-Attribut (APTCA) gekennzeichnet sind, verfügen nicht über diesen Schutz. Das-Attribut deaktiviert den Vererbungs Bedarf. Verfügbar gemachte Typen, die in einer Assembly ohne Vererbungs Anforderung deklariert werden, sind von Typen, die keine volle Vertrauenswürdigkeit aufweisen, Vererb Bar.

Wenn das APTCA-Attribut in einer voll vertrauenswürdigen Assembly vorhanden ist und ein Typ in der Assembly von einem Typ erbt, der keine teilweise vertrauenswürdigen Aufrufer zulässt, kann eine Sicherheitslücke ausgenutzt werden. Wenn zwei Typen `T1` und `T2` die folgenden Bedingungen erfüllen, können böswillige Aufrufer `T1` den-Typ verwenden, um die implizite Vererbungs `T2`-Vererbungs Anforderung zu umgehen, die schützt:

- `T1`ein öffentlicher Typ, der in einer voll vertrauenswürdigen Assembly mit dem APTCA-Attribut deklariert ist.

- `T1`erbt von einem Typ `T2` außerhalb der Assembly.

- `T2`die Assembly verfügt nicht über das APTCA-Attribut und sollte daher nicht durch Typen in teilweise vertrauenswürdigen Assemblys vererbt werden können.

Ein teilweise vertrauenswürdiger `X` Typ kann von `T1`erben. Dadurch erhält er Zugriff auf geerbte Member `T2`, die in deklariert werden. Da `T2` nicht über das APTCA-Attribut verfügt, muss der unmittelbar abgeleitete Typ (`T1`) einen Vererbungs Bedarf für volle Vertrauenswürdigkeit erfüllen. `T1` hat volle Vertrauenswürdigkeit und erfüllt daher diese Überprüfung. Das Sicherheitsrisiko besteht darin `X` , dass nicht an der Erfüllung des Vererbungs Bedarfs `T2` beteiligt ist, der von nicht vertrauenswürdigen Unterklassen geschützt wird. Aus diesem Grund dürfen Typen mit dem APTCA-Attributtypen, die nicht über das-Attribut verfügen, nicht erweitern.

Ein weiteres Sicherheitsproblem und ggf. ein allgemeineres Problem besteht darin, dass der`T1`abgeleitete Typ () mithilfe von Programmierfehlern geschützte Member von dem Typ verfügbar machen kann`T2`, der volle Vertrauenswürdigkeit erfordert (). Wenn diese Gefährdung auftritt, erhalten nicht vertrauenswürdige Aufrufer Zugriff auf Informationen, die nur für voll vertrauenswürdige Typen verfügbar sein sollten.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Wenn sich der von der Verletzung gemeldete Typ in einer Assembly befindet, die das APTCA-Attribut nicht benötigt, entfernen Sie ihn.

Wenn das APTCA-Attribut erforderlich ist, fügen Sie dem Typ eine Vererbungs Anforderung für volle Vertrauenswürdigkeit hinzu. Der Vererbungs Bedarf schützt vor der Vererbung durch nicht vertrauenswürdige Typen.

Es ist möglich, eine Verletzung durch Hinzufügen des APTCA-Attributs zu den Assemblys der von der Verletzung gemeldeten Basis Typen zu beheben. Verwenden Sie dies nicht, ohne zuerst eine intensive Sicherheitsüberprüfung für den gesamten Code in den Assemblys und sämtlichen Code durchzuführen, der von den Assemblys abhängt.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Um eine Warnung aus dieser Regel sicher zu unterdrücken, müssen Sie sicherstellen, dass geschützte Member, die von Ihrem Typ verfügbar gemacht werden, nicht direkt oder indirekt nicht vertrauenswürdigen Aufrufern Zugriff auf vertrauliche Informationen, Vorgänge oder Ressourcen gewähren, die auf zerstörerische Weise verwendet werden können.

## <a name="example"></a>Beispiel

Im folgenden Beispiel werden zwei Assemblys und eine Testanwendung verwendet, um das Sicherheitsrisiko zu veranschaulichen, das von dieser Regel erkannt wird. Die erste Assembly verfügt nicht über das APTCA-Attribut und sollte von teilweise vertrauenswürdigen Typen (dargestellt durch `T2` in der vorherigen Diskussion) nicht vererbbar sein.

[!code-csharp[FxCop.Security.NoAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_1.cs)]

Die zweite Assembly, die `T1` in der vorherigen Diskussion dargestellt wird, ist voll vertrauenswürdig und ermöglicht teilweise vertrauenswürdigen Aufrufern.

[!code-csharp[FxCop.Security.YesAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_2.cs)]

Der `X` in der vorherigen Diskussion dargestellte Testtyp befindet sich in einer teilweise vertrauenswürdigen Assembly.

[!code-csharp[FxCop.Security.TestAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_3.cs)]

Dieses Beispiel erzeugt die folgende Ausgabe:

```txt
Meet at the shady glen 2/22/2003 12:00:00 AM!
From Test: sunny meadow
Meet at the sunny meadow 2/22/2003 12:00:00 AM!
```

## <a name="related-rules"></a>Verwandte Regeln

[CA2116: APTCA-Methoden sollten nur APTCA-Methoden aufzurufen.](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)

## <a name="see-also"></a>Siehe auch

- [Richtlinien für das Schreiben von sicherem Code](/dotnet/standard/security/secure-coding-guidelines)
- [Verwenden von Bibliotheken aus teilweise vertrauenswürdigem Code](/dotnet/framework/misc/using-libraries-from-partially-trusted-code)
