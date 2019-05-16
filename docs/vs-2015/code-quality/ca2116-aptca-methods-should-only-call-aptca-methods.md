---
title: 'CA2116: APTCA-Methoden sollten nur APTCA-Methoden aufrufen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
helpviewer_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
ms.assetid: 8b91637e-891f-4dde-857b-bf8012270ec4
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ac5877ecf22ca8d0d8cc15095d354973ece29eaa
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687357"
---
# <a name="ca2116-aptca-methods-should-only-call-aptca-methods"></a>CA2116: APTCA-Methoden sollten nur APTCA-Methoden aufrufen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|
|CheckId|CA2116|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine Methode in einer Assembly mit der <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> Attribut Ruft eine Methode in einer Assembly, die nicht über das Attribut verfügt.

## <a name="rule-description"></a>Regelbeschreibung
 Standardmäßig öffentliche oder geschützte Methoden in Assemblys mit starken Namen implizit durch geschützt sind eine [Verknüpfungsaufrufe](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) für volle Vertrauenswürdigkeit, ausschließlich vollständig vertrauenswürdige Aufrufer auf eine Assembly mit starkem Namen zugreifen können. Assemblys mit starkem Namen gekennzeichnet werden, mit der <xref:System.Security.AllowPartiallyTrustedCallersAttribute> -Attribut (APTCA) müssen sich nicht auf diesen Schutz. Das Attribut deaktiviert den Linkaufruf, damit die Assembly Aufrufern, die keine volle Vertrauenswürdigkeit, z. B. Code ausführen, die aus einem Intranet oder dem Internet zugegriffen werden kann.

 Wenn das APTCA-Attribut in einer voll vertrauenswürdigen Assembly vorhanden ist und die Assembly Code ausführt, in einer anderen Assembly, die keine teilweise vertrauenswürdigen Aufrufer zulässt, kann diese Sicherheitslücke ausgenutzt werden. Wenn zwei Methoden `M1` und `M2` folgende Bedingungen erfüllt, können böswillige Aufrufer der Methode `M1` den Linkaufruf implizite volle Vertrauenswürdigkeit zu umgehen, die schützt `M2`:

- `M1` in einer voll vertrauenswürdigen Assembly, die über das APTCA-Attribut verfügt, wird eine öffentliche Methode deklariert werden.

- `M1` Ruft eine Methode `M2` außerhalb `M1`der Assembly.

- `M2`die Assembly verfügt nicht über das APTCA-Attribut, und aus diesem Grund sollten nicht ausgeführt werden durch oder im Auftrag von Aufrufern, die teilweise vertrauenswürdig sind.

  Ein teilweise vertrauenswürdiger Aufrufer `X` Methode aufrufen `M1`, und bewirkt, `M1` aufzurufende `M2`. Da `M2` verfügt nicht über das APTCA-Attribut angegeben haben, wird ihr unmittelbarer Aufrufer (`M1`) erfüllen müssen, einen Linkaufruf voll vertrauenswürdig sind. `M1` ist voll vertrauenswürdig und erfüllt daher diese Überprüfung. Das Sicherheitsrisiko liegt daran, dass `X` nicht beteiligt, die schützt Verknüpfungsaufrufs `M2` von nicht vertrauenswürdigen Aufrufern. Methoden mit dem APTCA-Attribut müssen daher keine Methoden aufrufen, die nicht mit das Attribut verfügen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Wenn das APTCA-Attribut erforderlich ist, verwenden Sie eine Anforderung, um die Methode zu schützen, die voll vertrauenswürdige Assembly aufruft. Die genauen Berechtigungen, die Sie bei Bedarf hängt von die Funktionalität, die durch die Methode verfügbar gemacht. Wenn es möglich ist, schützen Sie die Methode mit einer Anforderung für volle Vertrauenswürdigkeit, um sicherzustellen, dass die zugrunde liegende Funktionalität nicht für teilweise vertrauenswürdige Aufrufer verfügbar gemacht wird. Wenn dies nicht möglich ist, wählen Sie einen Satz von Berechtigungen, der effektiv die verfügbar gemachte Funktionalität schützt. Weitere Informationen zu Anforderungen, finden Sie unter [Anforderungen](https://msdn.microsoft.com/e5283e28-2366-4519-b27d-ef5c1ddc1f48).

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Um problemlos eine Warnung dieser Regel zu unterdrücken, müssen Sie sicherstellen, dass die Funktionalität verfügbar gemacht werden, indem Sie die Methode nicht direkt oder indirekt zulässt Aufrufer Zugriff auf vertrauliche Informationen, Vorgänge oder Ressourcen, die auf schädigende Weise verwendet werden können.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird die zwei Assemblys und einer testanwendung, um das Sicherheitsrisiko, das von dieser Regel erkannte zu veranschaulichen. Die erste Assembly verfügt nicht über das APTCA-Attribut, und sollte nicht für teilweise vertrauenswürdige Aufrufer verfügbar sein (dargestellt durch `M2` aus dem vorherigen Beispiel).

 [!code-csharp[FxCop.Security.NoAptca#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.NoAptca/cs/FxCop.Security.NoAptca.cs#1)]

## <a name="example"></a>Beispiel
 Die zweite Assembly ist voll vertrauenswürdig und lässt teilweise vertrauenswürdige Aufrufer (dargestellt durch `M1` aus dem vorherigen Beispiel).

 [!code-csharp[FxCop.Security.YesAptca#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptca/cs/FxCop.Security.YesAptca.cs#1)]

## <a name="example"></a>Beispiel
 Die Anwendung zu testen (dargestellt durch `X` aus dem vorherigen Beispiel) ist teilweise vertrauenswürdig.

 [!code-csharp[FxCop.Security.TestAptcaMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaMethods/cs/FxCop.Security.TestAptcaMethods.cs#1)]

 Folgende Ergebnisse werden zurückgegeben:

 **Fordern Sie für vollständige Vertrauenswürdigkeit: Fehler bei der Anforderung. ** 
 **ClassRequiringFullTrust.DoWork wurde aufgerufen.**
## <a name="related-rules"></a>Verwandte Regeln
 [CA2117: APTCA-Typen sollten nur APTCA-Basistypen erweitern.](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)

## <a name="see-also"></a>Siehe auch
 [Sichern Sie die Richtlinien für das Codieren](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [.NET Framework-Assemblys aufgerufen durch teilweise vertrauenswürdigen Code](https://msdn.microsoft.com/a417fcd4-d3ca-4884-a308-3a1a080eac8d) [Verwenden von Bibliotheken aus teilweise vertrauenswürdigem Code](https://msdn.microsoft.com/library/dd66cd4c-b087-415f-9c3e-94e3a1835f74) [Anforderungen](https://msdn.microsoft.com/e5283e28-2366-4519-b27d-ef5c1ddc1f48) [Linkaufrufe](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [Daten und Modellierung](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
