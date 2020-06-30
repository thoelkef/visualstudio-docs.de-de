---
title: 'CA2117: APTCA-Typen sollten nur APTCA-Basis Typen erweitern | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2117
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
helpviewer_keywords:
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
- CA2117
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 90c1f66f36fc689ee077ec66f154487d65ee13a1
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543610"
---
# <a name="ca2117-aptca-types-should-only-extend-aptca-base-types"></a>CA2117: APTCA-Typen sollten nur APTCA-Basistypen erweitern.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|AptcaTypesShouldOnlyExtendAptcaBaseTypes|
|CheckId|CA2117|
|Category|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder geschützter Typ in einer Assembly mit dem- <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> Attribut erbt von einem Typ, der in einer Assembly deklariert ist, die nicht über das-Attribut verfügt.

## <a name="rule-description"></a>Beschreibung der Regel
 Standardmäßig werden öffentliche oder geschützte Typen in Assemblys mit starken Namen implizit durch [Vererbungs Anforderungen](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) für volle Vertrauenswürdigkeit geschützt. Assemblys mit starkem Namen, die mit dem- <xref:System.Security.AllowPartiallyTrustedCallersAttribute> Attribut (APTCA) gekennzeichnet sind, verfügen nicht über diesen Schutz. Das-Attribut deaktiviert den Vererbungs Bedarf. Dadurch werden von Typen, die keine volle Vertrauenswürdigkeit aufweisen, die in der Assembly deklarierten verfügbar gemachten Typen vererbt.

 Wenn das APTCA-Attribut in einer voll vertrauenswürdigen Assembly vorhanden ist und ein Typ in der Assembly von einem Typ erbt, der keine teilweise vertrauenswürdigen Aufrufer zulässt, kann eine Sicherheitslücke ausgenutzt werden. Wenn zwei Typen `T1` und `T2` die folgenden Bedingungen erfüllen, können böswillige Aufrufer den-Typ verwenden, `T1` um die implizite Vererbungs-Vererbungs Anforderung zu umgehen, die schützt `T2` :

- `T1`ein öffentlicher Typ, der in einer voll vertrauenswürdigen Assembly mit dem APTCA-Attribut deklariert ist.

- `T1`erbt von einem Typ `T2` außerhalb der Assembly.

- `T2`die Assembly verfügt nicht über das APTCA-Attribut und sollte daher nicht durch Typen in teilweise vertrauenswürdigen Assemblys vererbt werden können.

  Ein teilweise vertrauenswürdiger Typ `X` kann von Erben `T1` . Dadurch erhält er Zugriff auf geerbte Member, die in deklariert werden `T2` . Da `T2` nicht über das APTCA-Attribut verfügt, muss der unmittelbar abgeleitete Typ ( `T1` ) einen Vererbungs Bedarf für volle Vertrauenswürdigkeit erfüllen; `T1` hat volle Vertrauenswürdigkeit und erfüllt daher diese Überprüfung. Das Sicherheitsrisiko besteht darin `X` , dass nicht an der Erfüllung des Vererbungs Bedarfs beteiligt ist, der `T2` von nicht vertrauenswürdigen Unterklassen geschützt wird. Aus diesem Grund dürfen Typen mit dem APTCA-Attributtypen, die nicht über das-Attribut verfügen, nicht erweitern.

  Ein weiteres Sicherheitsproblem und ggf. ein allgemeineres Problem besteht darin, dass der abgeleitete Typ ( `T1` ) mithilfe von Programmierfehlern geschützte Member von dem Typ verfügbar machen kann, der volle Vertrauenswürdigkeit erfordert ( `T2` ). In diesem Fall erhalten nicht vertrauenswürdige Aufrufer Zugriff auf Informationen, die nur für voll vertrauenswürdige Typen verfügbar sein sollten.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Wenn sich der von der Verletzung gemeldete Typ in einer Assembly befindet, die das APTCA-Attribut nicht benötigt, entfernen Sie ihn.

 Wenn das APTCA-Attribut erforderlich ist, fügen Sie dem Typ eine Vererbungs Anforderung für volle Vertrauenswürdigkeit hinzu. Dies schützt vor der Vererbung durch nicht vertrauenswürdige Typen.

 Es ist möglich, eine Verletzung durch Hinzufügen des APTCA-Attributs zu den Assemblys der von der Verletzung gemeldeten Basis Typen zu beheben. Verwenden Sie dies nicht, ohne zuerst eine intensive Sicherheitsüberprüfung für den gesamten Code in den Assemblys und sämtlichen Code durchzuführen, der von den Assemblys abhängt.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Um eine Warnung aus dieser Regel sicher zu unterdrücken, müssen Sie sicherstellen, dass geschützte Member, die von Ihrem Typ verfügbar gemacht werden, nicht direkt oder indirekt nicht vertrauenswürdigen Aufrufern Zugriff auf vertrauliche Informationen, Vorgänge oder Ressourcen gewähren, die auf zerstörerische Weise verwendet werden können.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel werden zwei Assemblys und eine Testanwendung verwendet, um das Sicherheitsrisiko zu veranschaulichen, das von dieser Regel erkannt wird. Die erste Assembly verfügt nicht über das APTCA-Attribut und sollte von teilweise vertrauenswürdigen Typen (dargestellt durch `T2` in der vorherigen Diskussion) nicht vererbbar sein.

 [!code-csharp[FxCop.Security.NoAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.NoAptcaInherit/cs/FxCop.Security.NoAptcaInherit.cs#1)]

## <a name="example"></a>Beispiel
 Die zweite Assembly, die `T1` in der vorherigen Diskussion dargestellt wird, ist voll vertrauenswürdig und ermöglicht teilweise vertrauenswürdigen Aufrufern.

 [!code-csharp[FxCop.Security.YesAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptcaInherit/cs/FxCop.Security.YesAptcaInherit.cs#1)]

## <a name="example"></a>Beispiel
 Der `X` in der vorherigen Diskussion dargestellte Testtyp befindet sich in einer teilweise vertrauenswürdigen Assembly.

 [!code-csharp[FxCop.Security.TestAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaInherit/cs/FxCop.Security.TestAptcaInherit.cs#1)]

 Folgende Ergebnisse werden zurückgegeben:

 **Treffen Sie am schattigen Glen 2/22/2003 12:00:00 am!** 
 **Aus Test: sonnige Wiese** 
 **Treffen Sie auf der sonnigen Wiese 2/22/2003 12:00:00 Uhr!**
## <a name="related-rules"></a>Verwandte Regeln
 [CA2116: APTCA-Methoden sollten nur APTCA-Methoden aufrufen.](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)

## <a name="see-also"></a>Weitere Informationen
 [Sichere Codierungs Richtlinien](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) .NET Framework Assemblys, die [von teilweise vertrauenswürdigem Code mithilfe von](https://msdn.microsoft.com/a417fcd4-d3ca-4884-a308-3a1a080eac8d) [Bibliotheken aus teilweise vertrauenswürdigen Code](https://msdn.microsoft.com/library/dd66cd4c-b087-415f-9c3e-94e3a1835f74) [Vererbungs Anforderungen](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9)
