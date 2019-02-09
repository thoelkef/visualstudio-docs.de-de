---
title: 'CA2114: Methodensicherheit sollte Superset des Typs sein.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MethodSecurityShouldBeASupersetOfType
- CA2114
helpviewer_keywords:
- CA2114
- MethodSecurityShouldBeASupersetOfType
ms.assetid: 663f7aa4-8be5-4bd5-be92-4e9444f07077
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 623416e557759ace1ad6403ef8ef977df01da39e
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55911129"
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114: Methodensicherheit sollte Superset des Typs sein.

|||
|-|-|
|TypeName|MethodSecurityShouldBeASupersetOfType|
|CheckId|CA2114|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Typ verfügt über die deklarative Sicherheit und eine seiner Methoden die deklarative Sicherheit für die gleiche Aktion für die Sicherheit hat und die Sicherheitsaktion nicht [Verknüpfungsaufrufe](/dotnet/framework/misc/link-demands), und die Berechtigungen vom Typ überprüft sind keine Teilmenge der Berechtigungen überprüft, von der Methode.

## <a name="rule-description"></a>Regelbeschreibung
 Eine Methode sollte nicht sowohl eine Methode auf und Typebene deklarative Sicherheit für die gleiche Aktion aufweisen. Die zwei Überprüfungen sind nicht kombiniert werden; Es wird nur auf die Anforderung auf Methodenebene angewendet. Angenommen, ein Berechtigung anfordert `X`, und eine seiner Methoden fordert die Berechtigung `Y`, Code verfügt nicht über die Berechtigung verfügen über `X` zum Ausführen der Methode.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Überprüfen Sie Ihren Code, um sicherzustellen, dass beide Aktionen erforderlich sind. Wenn beide Aktionen erforderlich sind, stellen Sie sicher, dass die Aktion auf Methodenebene, die Sicherheit auf Typebene angegeben enthält. Wenn Ihr Typ Berechtigung erfordert z. B. `X`, und die Methode muss auch die Berechtigung anfordern `Y`, die Methode sollte explizit anfordern `X` und `Y`.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Es ist sicher, die mit dieser Regel eine Warnung zu unterdrücken, wenn die Methode nicht die Sicherheit, die vom angegebenen Typ erforderlich ist. Dies ist jedoch keinem normalen Szenario und möglicherweise die Notwendigkeit von Entwurf sorgfältig zu überprüfen.

## <a name="example-1"></a>Beispiel 1

Im folgenden Beispiel wird die Umgebungsberechtigungen die Gefahren des Verstoßes gegen diese Regel veranschaulicht. In diesem Beispiel erstellt der Anwendungscode eine Instanz des gesicherten Typs vor dem Verweigern der Berechtigung, die durch den Typ erforderlich. In einem Bedrohungsszenario mit echten benötigt die Anwendung eine andere Möglichkeit, eine Instanz des Objekts abzurufen.

Im folgenden Beispiel fordert die Bibliothek Schreibberechtigungen für einen Typ und read-Berechtigung für eine Methode.

[!code-csharp[FxCop.Security.MethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_1.cs)]

## <a name="example-2"></a>Beispiel 2

Der folgende Code veranschaulicht die Sicherheitsrisiken für die Bibliothek durch Aufrufen der Methode, obwohl sie die Sicherheit auf Zeilenebene Typ Anforderungen nicht erfüllt.

[!code-csharp[FxCop.Security.TestMethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_2.cs)]

Dieses Beispiel erzeugt die folgende Ausgabe:

```txt
[All permissions] Personal information: 6/16/1964 12:00:00 AM
[No write permission (demanded by type)] Personal information: 6/16/1964 12:00:00 AM
[No read permission (demanded by method)] Could not access personal information: Request failed.
```

## <a name="see-also"></a>Siehe auch

- [Richtlinien für das Schreiben von sicherem Code](/dotnet/standard/security/secure-coding-guidelines)
- [Verknüpfungsaufrufe](/dotnet/framework/misc/link-demands)
- [Daten und Modellierung](/dotnet/framework/data/index)