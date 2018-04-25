---
title: 'CA2116: APTCA-Methoden sollten nur APTCA-Methoden aufrufen'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
helpviewer_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
ms.assetid: 8b91637e-891f-4dde-857b-bf8012270ec4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 300b08d6fd00a9bf2a38e738a3b4d433111cb8c7
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="ca2116-aptca-methods-should-only-call-aptca-methods"></a>CA2116: APTCA-Methoden sollten nur APTCA-Methoden aufrufen
|||
|-|-|
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|
|CheckId|CA2116|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine Methode in einer Assembly mit dem <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> Attribut Ruft eine Methode in einer Assembly, die nicht das Attribut verfügt.

## <a name="rule-description"></a>Regelbeschreibung
 Standardmäßig werden öffentliche oder geschützte Methoden in Assemblys mit starken Namen implizit durch geschützt eine [Verknüpfungsaufrufe](/dotnet/framework/misc/link-demands) für volle Vertrauenswürdigkeit; nur voll vertrauenswürdige Aufrufer eine Assembly mit starkem Namen zugreifen können. Assemblys mit starken Namen gekennzeichnet, mit dem <xref:System.Security.AllowPartiallyTrustedCallersAttribute> -Attribut (APTCA) verfügen nicht über diesen Schutz. Das Attribut deaktiviert den Linkaufruf machen, die Assembly zu Aufrufern, die keine volle Vertrauenswürdigkeit, z. B. Code in einem Intranet oder im Internet ausgeführt haben.

 Wenn das APTCA-Attribut in einer voll vertrauenswürdigen Assembly vorhanden ist und die Assembly Code ausführt, in einer anderen Assembly, die keine teilweise vertrauenswürdigen Aufrufer zulässt, kann diese Sicherheitslücke ausgenutzt. Wenn zwei Methoden `M1` und `M2` die folgenden Bedingungen erfüllen, können böswillige Aufrufer der Methode verwenden `M1` Linkaufruf implizite volle Vertrauenswürdigkeit umgangen werden, die schützt `M2`:

-   `M1` in einer voll vertrauenswürdigen Assembly, die über das APTCA-Attribut verfügt, ist eine öffentliche Methode deklariert werden.

-   `M1` Ruft eine Methode `M2` außerhalb `M1`der Assembly.

-   `M2`die Assembly verfügt nicht über das APTCA-Attribut, und aus diesem Grund sollte nicht ausgeführt werden durch oder im Auftrag, die teilweise vertrauenswürdigen Aufrufern.

 Eine teilweise vertrauenswürdige Aufrufer `X` Methode aufrufen `M1`, was `M1` Aufrufen `M2`. Da `M2` verfügt nicht über das APTCA-Attribut der unmittelbare Aufrufer (`M1`) erfüllen muss einen Linkaufruf für volle Vertrauenswürdigkeit; `M1` ist voll vertrauenswürdig und erfüllt daher diese Überprüfung. Das Sicherheitsrisiko, da `X` nicht Teil des Linkaufrufs schützt `M2` von nicht vertrauenswürdigen Aufrufern. Methoden mit dem APTCA-Attribut müssen daher keine Methoden aufrufen, die nicht mit das Attribut verfügen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Wenn das APTCA-Attribut erforderlich ist, verwenden Sie eine Anforderung an um die Methode zu schützen, die voll vertrauenswürdige Assembly aufruft. Die genauen Berechtigungen, die Sie bei Bedarf von der durch die Methode verfügbar gemachten Funktionalität abhängig ist. Wenn es möglich ist, schützen Sie die Methode mit einer Anforderung für volle Vertrauenswürdigkeit, um sicherzustellen, dass die zugrunde liegenden Funktionalität nicht für teilweise vertrauenswürdige Aufrufer verfügbar gemacht wird. Wenn dies nicht möglich ist, wählen Sie einen Satz von Berechtigungen, der effektiv die verfügbar gemachten Funktionalität schützt.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Um eine Warnung dieser Regel sicher zu unterdrücken, müssen Sie sicherstellen, die Funktionalität verfügbar gemacht, durch die Methode nicht direkt oder indirekt zulässig, Aufrufern Zugriff auf vertrauliche Informationen, Vorgänge oder Ressourcen, die einen destruktiven Weise verwendet werden können.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird zwei Assemblys und eine testanwendung, um die von dieser Regel erkannte Sicherheitslücke zu veranschaulichen. Die erste Assembly verfügt nicht über das APTCA-Attribut und sollte nicht für teilweise vertrauenswürdige Aufrufer zugegriffen werden (dargestellt durch `M2` im vorherigen Beispiel).

 [!code-csharp[FxCop.Security.NoAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_1.cs)]

## <a name="example"></a>Beispiel
 Die zweite Assembly ist vollständig vertrauenswürdig und lässt teilweise vertrauenswürdige Aufrufer (dargestellt durch `M1` im vorherigen Beispiel).

 [!code-csharp[FxCop.Security.YesAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_2.cs)]

## <a name="example"></a>Beispiel
 Die testanwendung (dargestellt durch `X` im vorherigen Beispiel) ist, teilweise vertrauenswürdig.

 [!code-csharp[FxCop.Security.TestAptcaMethods#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_3.cs)]

 Folgende Ergebnisse werden zurückgegeben:

 **"Demand" für vollständige Vertrauenswürdigkeit: Fehler bei der Anforderung. ** 
 **ClassRequiringFullTrust.DoWork wurde aufgerufen.**
## <a name="related-rules"></a>Verwandte Regeln
 [CA2117: APTCA-Typen sollten nur APTCA-Basistypen erweitern](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)

## <a name="see-also"></a>Siehe auch
 [Schreiben von sicherem Richtlinien](/dotnet/standard/security/secure-coding-guidelines) [Verwenden von Bibliotheken aus teilweise vertrauenswürdigem Code](/dotnet/framework/misc/using-libraries-from-partially-trusted-code) [verknüpfen Forderungen](/dotnet/framework/misc/link-demands) [Daten und Modellierung](/dotnet/framework/data/index)