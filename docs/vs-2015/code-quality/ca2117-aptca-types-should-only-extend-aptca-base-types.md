---
title: 'CA2117: APTCA-Typen sollten nur APTCA-Basistypen erweitern | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2117
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
helpviewer_keywords:
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
- CA2117
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4b069674827ab266b4a4b7a99f81e039d487f6da
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49922645"
---
# <a name="ca2117-aptca-types-should-only-extend-aptca-base-types"></a>CA2117: APTCA-Typen sollten nur APTCA-Basistypen erweitern
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AptcaTypesShouldOnlyExtendAptcaBaseTypes|
|CheckId|CA2117|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder geschützter Typ in einer Assembly mit der <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> -Attribut erbt von einem Typ deklariert, die in einer Assembly, die nicht über das Attribut verfügt.

## <a name="rule-description"></a>Regelbeschreibung
 Standardmäßig werden öffentliche oder geschützte Typen in Assemblys mit starken Namen implizit durch geschützt ein [Vererbungsanforderungen](http://msdn.microsoft.com/en-us/28b9adbb-8f08-4f10-b856-dbf59eb932d9) für volle Vertrauenswürdigkeit. Assemblys mit starkem Namen gekennzeichnet werden, mit der <xref:System.Security.AllowPartiallyTrustedCallersAttribute> -Attribut (APTCA) müssen sich nicht auf diesen Schutz. Das Attribut wird die vererbungsanforderung deaktiviert. Auf diese Weise verfügbar gemachten Typen in der Assembly deklarierten vererbbar von Typen, die keine volle Vertrauenswürdigkeit haben.

 Wenn das APTCA-Attribut in einer voll vertrauenswürdigen Assembly vorhanden ist und ein Typ in der Assembly erbt von einem Typ, der keine teilweise vertrauenswürdigen Aufrufer zulässt, kann diese Sicherheitslücke ausgenutzt werden. Wenn zwei Typen `T1` und `T2` folgende Bedingungen erfüllt, können böswillige Aufrufer den Typ `T1` die vererbungsanforderung implizite volle Vertrauenswürdigkeit zu umgehen, die schützt `T2`:

- `T1` in einer voll vertrauenswürdigen Assembly, die über das APTCA-Attribut verfügt, wird ein öffentlicher Typ deklariert werden.

- `T1` von einem Typ erbt `T2` außerhalb der Assembly.

- `T2`die Assembly verfügt nicht über das APTCA-Attribut, und daher sollte nicht vererbt werden von Typen in teilweise vertrauenswürdigen Assemblys.

  Ein teilweise vertrauenswürdiger `X` erben können `T1`, ermöglicht er Zugriff auf geerbte Member deklariert `T2`. Da `T2` verfügt nicht über das APTCA-Attribut, dessen sofortige abgeleiteten Typ (`T1`) erfüllen müssen, eine vererbungsanforderung voll vertrauenswürdig sind. `T1` ist voll vertrauenswürdig und erfüllt daher diese Überprüfung. Das Sicherheitsrisiko liegt daran, dass `X` nicht erfüllen die vererbungsanforderung, die schützt beteiligt `T2` aus nicht vertrauenswürdigen-Unterklasse. Aus diesem Grund müssen Typen, mit dem APTCA-Attribut nicht Typen erweitern, die nicht mit das Attribut verfügen.

  Ein anderes Sicherheitsproblem, und ein eher üblich ist, die den abgeleiteten Typ (`T1`) können über Programmierfehler, verfügbar machen geschützte Member des Typs, die volle Vertrauenswürdigkeit erfordert (`T2`). In diesem Fall erhalten Sie nicht vertrauenswürdige Aufrufer den Zugriff auf Informationen, die nur für vollständig vertrauenswürdige Typen verfügbar sein sollen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Wenn der Typ, der den Verstoß in einer Assembly, die nicht über das APTCA-Attribut erfordert ist, entfernen Sie sie.

 Wenn das APTCA-Attribut erforderlich ist, fügen Sie in den Typ einer vererbungsanforderung für volle Vertrauenswürdigkeit. Dies schützt vor Vererbung durch nicht vertrauenswürdige Typen.

 Es ist möglich, einen Verstoß zu beheben, indem Sie das APTCA-Attribut hinzufügen, auf die Assemblys der Basistypen von den Verstoß gemeldet. Verwenden Sie keine ohne Durchführung von einer intensiven sicherheitsüberprüfung der gesamte Code in den Assemblys und der gesamte Code, von der die Assemblys abhängig.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Um problemlos eine Warnung dieser Regel zu unterdrücken, müssen Sie sicherstellen, geschützte Member, die von Ihrem Typ verfügbar gemacht werden, nicht direkt oder indirekt erlaubt, werden nicht vertrauenswürdige Aufrufern Zugriff auf vertrauliche Informationen, Vorgänge oder Ressourcen, die auf schädigende Weise verwendet werden können.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird die zwei Assemblys und einer testanwendung, um das Sicherheitsrisiko, das von dieser Regel erkannte zu veranschaulichen. Die erste Assembly verfügt nicht über das APTCA-Attribut, und sollte nicht von teilweise vertrauenswürdigen Typen geerbt (dargestellt durch `T2` aus dem vorherigen Beispiel).

 [!code-csharp[FxCop.Security.NoAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.NoAptcaInherit/cs/FxCop.Security.NoAptcaInherit.cs#1)]

## <a name="example"></a>Beispiel
 Die zweite Assembly, dargestellt durch `T1` in der vorherigen Beschreibung ist voll vertrauenswürdig und kann von teilweise vertrauenswürdigen Aufrufern.

 [!code-csharp[FxCop.Security.YesAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptcaInherit/cs/FxCop.Security.YesAptcaInherit.cs#1)]

## <a name="example"></a>Beispiel
 Testtyp, dargestellt durch `X` in der vorherigen Beschreibung befindet sich in einer teilweise vertrauenswürdigen Assembly.

 [!code-csharp[FxCop.Security.TestAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaInherit/cs/FxCop.Security.TestAptcaInherit.cs#1)]

 Folgende Ergebnisse werden zurückgegeben:

 **Auf der Illegales vor Glen erfüllen 2/22/2003 12:00:00 Uhr. ** 
 **Von Test: sonnigen Wiese**
**erfüllen, auf die sonnigen Wiese 2/22/2003 12:00:00 Uhr.**
## <a name="related-rules"></a>Verwandte Regeln
 [CA2116: APTCA-Methoden sollten nur APTCA-Methoden aufrufen](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)

## <a name="see-also"></a>Siehe auch
 [Sichern Sie die Richtlinien für das Codieren](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [.NET Framework-Assemblys aufgerufen durch teilweise vertrauenswürdigen Code](http://msdn.microsoft.com/en-us/a417fcd4-d3ca-4884-a308-3a1a080eac8d) [Verwenden von Bibliotheken aus teilweise vertrauenswürdigem Code](http://msdn.microsoft.com/library/dd66cd4c-b087-415f-9c3e-94e3a1835f74) [Vererbungsanforderungen](http://msdn.microsoft.com/en-us/28b9adbb-8f08-4f10-b856-dbf59eb932d9)




