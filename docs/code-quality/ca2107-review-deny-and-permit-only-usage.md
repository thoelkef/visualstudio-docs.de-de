---
title: 'CA2107: Verwendung von Deny und PermitOnly überprüfen.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2107
- ReviewDenyAndPermitOnlyUsage
helpviewer_keywords:
- ReviewDenyAndPermitOnlyUsage
- CA2107
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9c7f3bdc6351f30d5cad60a7ed9663824fa3d434
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714713"
---
# <a name="ca2107-review-deny-and-permit-only-usage"></a>CA2107: Verwendung von Deny und PermitOnly überprüfen.

|||
|-|-|
|TypeName|ReviewDenyAndPermitOnlyUsage|
|CheckId|CA2107|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Eine Methode enthält eine sicherheitsüberprüfung, die angibt, die Sicherheitsaktion PermitOnly "oder" ablehnen.

## <a name="rule-description"></a>Regelbeschreibung

Die <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> Sicherheitsaktion sollte nur von Personen mit Kenntnissen der Sicherheit von .NET verwendet werden. Code, in dem diese Sicherheitsaktionen verwendet werden, sollte einer Sicherheitsüberprüfung unterzogen werden.

Verweigern ändert das Standardverhalten des Stackwalks, die als Reaktion auf eine sicherheitsforderung auftritt. Sie können Berechtigungen angeben, die für die Dauer der Deny-Methode, unabhängig von den tatsächlichen Berechtigungen der Aufrufer in der Aufrufliste nicht gewährt werden müssen. Wenn der Stackwalk erkennt eine Methode, die durch das Verweigern gesichert ist, und der Stackwalk schlägt, wenn die geforderte Berechtigung in der verweigerten Berechtigungen enthalten ist fehl. PermitOnly ändert auch das Standardverhalten des Stackwalks. Sie können Code nur die Berechtigungen an, die gewährt werden können, unabhängig von den Berechtigungen des Aufrufers. Wenn der Stackwalk erkennt eine Methode, die durch PermitOnly gesichert ist, und der Stackwalk schlägt, wenn die angeforderte Berechtigung nicht mit den Berechtigungen enthalten ist, die durch die PermitOnly angegeben werden fehl.

Sicherheitsrisiken aufgrund ihrer begrenzten nutzen und ein leicht unterschiedliches Verhalten sollte der Code, der für diese Aktionen beruht sorgfältig bewertet werden. Nehmen wir einmal die folgende Situation:

- [Linkaufrufe](/dotnet/framework/misc/link-demands) durch Deny oder PermitOnly nicht betroffen sind.

- Im Falle Deny oder PermitOnly im gleichen Stapelrahmen wie die Anforderung, bei dem der Stapeldurchlauf, haben die Sicherheitsaktionen keine Auswirkungen.

- Werte, die zum Erstellen der pfadbasierten Berechtigungen verwendet werden, können in der Regel auf unterschiedliche Weise angegeben werden. Verweigern des Zugriffs auf eine Form des Pfads wird Zugriff auf alle Formulare nicht verweigert werden. Wenn eine Dateifreigabe beispielsweise \\\Server\Share zugeordnet ist, auf einem Netzlaufwerk X:, zum Verweigern von Zugriff auf eine Datei auf der Freigabe, Sie müssen verweigert \\\Server\Share\File X:\File und alle anderen Pfade, die auf die Datei zugreift.

- Ein <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> kann einen Stackwalk beendet, bevor Deny oder PermitOnly erreicht wird.

- Wenn Deny keine Auswirkung hat, beispielsweise kann Wenn ein Aufrufer eine Berechtigung verfügt, die durch das verweigern, blockiert ist der Aufrufer direkt auf die geschützte Ressource zugreifen unter Umgehung der. Wenn der Aufrufer nicht über die verweigerte Berechtigung verfügt, würde der Stackwalk ohne Deny fehlschlagen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Jede Verwendung dieser Aktionen Sicherheit bewirkt eine Verletzung. Um einen Verstoß zu beheben, verwenden Sie nicht diese Sicherheitsaktionen.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Unterdrücken Sie eine Warnung dieser Regel, nur nach dem Durchführen einer sicherheitsüberprüfung.

## <a name="example-1"></a>Beispiel 1

Das folgende Beispiel zeigt einige Einschränkungen der verweigern. Die Bibliothek enthält eine Klasse mit zwei Methoden, die mit Ausnahme von sicherheitsanforderungen identisch sind, die sie schützen.

[!code-csharp[FxCop.Security.PermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_1.cs)]

## <a name="example-2"></a>Beispiel 2

Die folgende Anwendung zeigt die Auswirkungen von Deny auf die geschützten Methoden aus der Bibliothek.

[!code-csharp[FxCop.Security.TestPermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_2.cs)]

Dieses Beispiel erzeugt die folgende Ausgabe:

```txt
Demand: Caller's Deny has no effect on Demand with the asserted permission.
LinkDemand: Caller's Deny has no effect on LinkDemand with the asserted permission.
LinkDemand: Caller's Deny has no effect with LinkDemand-protected code.
LinkDemand: This Deny has no effect with LinkDemand-protected code.
```

## <a name="see-also"></a>Siehe auch

- <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName>
- <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
- <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>
- <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>
- [Richtlinien für das Schreiben von sicherem Code](/dotnet/standard/security/secure-coding-guidelines)