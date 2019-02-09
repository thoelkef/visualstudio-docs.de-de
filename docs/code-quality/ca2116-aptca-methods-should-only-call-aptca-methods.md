---
title: 'CA2116: APTCA-Methoden sollten nur APTCA-Methoden aufrufen.'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 03948506d928f7d638b21c1fa4bc0a35818ec09a
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55926909"
---
# <a name="ca2116-aptca-methods-should-only-call-aptca-methods"></a>CA2116: APTCA-Methoden sollten nur APTCA-Methoden aufrufen.

|||
|-|-|
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|
|CheckId|CA2116|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Eine Methode in einer Assembly mit der <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> Attribut Ruft eine Methode in einer Assembly, die nicht über das Attribut verfügt.

## <a name="rule-description"></a>Regelbeschreibung

Standardmäßig öffentliche oder geschützte Methoden in Assemblys mit starken Namen implizit durch geschützt sind eine [Verknüpfungsaufrufe](/dotnet/framework/misc/link-demands) für volle Vertrauenswürdigkeit, ausschließlich vollständig vertrauenswürdige Aufrufer auf eine Assembly mit starkem Namen zugreifen können. Assemblys mit starkem Namen gekennzeichnet werden, mit der <xref:System.Security.AllowPartiallyTrustedCallersAttribute> -Attribut (APTCA) müssen sich nicht auf diesen Schutz. Das Attribut deaktiviert den Linkaufruf, damit die Assembly Aufrufern, die keine volle Vertrauenswürdigkeit, z. B. Code ausführen, die aus einem Intranet oder dem Internet zugegriffen werden kann.

Wenn das APTCA-Attribut in einer voll vertrauenswürdigen Assembly vorhanden ist und die Assembly Code ausführt, in einer anderen Assembly, die keine teilweise vertrauenswürdigen Aufrufer zulässt, kann diese Sicherheitslücke ausgenutzt werden. Wenn zwei Methoden `M1` und `M2` folgende Bedingungen erfüllt, können böswillige Aufrufer der Methode `M1` den Linkaufruf implizite volle Vertrauenswürdigkeit zu umgehen, die schützt `M2`:

- `M1` in einer voll vertrauenswürdigen Assembly, die über das APTCA-Attribut verfügt, wird eine öffentliche Methode deklariert werden.

- `M1` Ruft eine Methode `M2` außerhalb `M1`der Assembly.

- `M2`die Assembly verfügt nicht über das APTCA-Attribut, und aus diesem Grund sollten nicht ausgeführt werden durch oder im Auftrag von Aufrufern, die teilweise vertrauenswürdig sind.

Ein teilweise vertrauenswürdiger Aufrufer `X` Methode aufrufen `M1`, und bewirkt, `M1` aufzurufende `M2`. Da `M2` verfügt nicht über das APTCA-Attribut angegeben haben, wird ihr unmittelbarer Aufrufer (`M1`) erfüllen müssen, einen Linkaufruf voll vertrauenswürdig sind. `M1` ist voll vertrauenswürdig und erfüllt daher diese Überprüfung. Das Sicherheitsrisiko liegt daran, dass `X` nicht beteiligt, die schützt Verknüpfungsaufrufs `M2` von nicht vertrauenswürdigen Aufrufern. Methoden mit dem APTCA-Attribut müssen daher keine Methoden aufrufen, die nicht mit das Attribut verfügen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Wenn das APTCA-Attribut erforderlich ist, verwenden Sie eine Anforderung, um die Methode zu schützen, die voll vertrauenswürdige Assembly aufruft. Die genauen Berechtigungen, die Sie bei Bedarf hängt von die Funktionalität, die durch die Methode verfügbar gemacht. Wenn es möglich ist, schützen Sie die Methode mit einer Anforderung für volle Vertrauenswürdigkeit, um sicherzustellen, dass die zugrunde liegende Funktionalität nicht für teilweise vertrauenswürdige Aufrufer verfügbar gemacht wird. Wenn dies nicht möglich ist, wählen Sie einen Satz von Berechtigungen, der effektiv die verfügbar gemachte Funktionalität schützt.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Um problemlos eine Warnung dieser Regel zu unterdrücken, müssen Sie sicherstellen, dass die Funktionalität verfügbar gemacht werden, indem Sie die Methode nicht direkt oder indirekt zulässt Aufrufer Zugriff auf vertrauliche Informationen, Vorgänge oder Ressourcen, die auf schädigende Weise verwendet werden können.

## <a name="example-1"></a>Beispiel 1
 Im folgenden Beispiel wird die zwei Assemblys und einer testanwendung, um das Sicherheitsrisiko, das von dieser Regel erkannte zu veranschaulichen. Die erste Assembly verfügt nicht über das APTCA-Attribut, und sollte nicht für teilweise vertrauenswürdige Aufrufer verfügbar sein (dargestellt durch `M2` aus dem vorherigen Beispiel).

 [!code-csharp[FxCop.Security.NoAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_1.cs)]

## <a name="example-2"></a>Beispiel 2
 Die zweite Assembly ist voll vertrauenswürdig und lässt teilweise vertrauenswürdige Aufrufer (dargestellt durch `M1` aus dem vorherigen Beispiel).

 [!code-csharp[FxCop.Security.YesAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_2.cs)]

## <a name="example-3"></a>Beispiel 3
 Die Anwendung zu testen (dargestellt durch `X` aus dem vorherigen Beispiel) ist teilweise vertrauenswürdig.

 [!code-csharp[FxCop.Security.TestAptcaMethods#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_3.cs)]

Dieses Beispiel erzeugt die folgende Ausgabe:

```txt
Demand for full trust:Request failed.
ClassRequiringFullTrust.DoWork was called.
```

## <a name="related-rules"></a>Verwandte Regeln

- [CA2117: APTCA-Typen sollten nur APTCA-Basistypen erweitern.](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)

## <a name="see-also"></a>Siehe auch

- [Richtlinien für das Schreiben von sicherem Code](/dotnet/standard/security/secure-coding-guidelines)
- [Verwenden von Bibliotheken aus teilweise vertrauenswürdigem Code](/dotnet/framework/misc/using-libraries-from-partially-trusted-code)
- [Verknüpfungsaufrufe](/dotnet/framework/misc/link-demands)
- [Daten und Modellierung](/dotnet/framework/data/index)