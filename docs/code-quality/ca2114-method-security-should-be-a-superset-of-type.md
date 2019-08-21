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
ms.openlocfilehash: d83da42a029d746899bfaccf5d62f8856a040611
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921121"
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114: Methodensicherheit sollte Superset des Typs sein.

|||
|-|-|
|TypeName|MethodSecurityShouldBeASupersetOfType|
|CheckId|CA2114|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
Ein Typ verfügt über deklarative Sicherheit, und eine seiner Methoden verfügt über deklarative Sicherheit für dieselbe Sicherheitsaktion, und die Sicherheitsaktion ist kein [Verknüpfungsaufruf](/dotnet/framework/misc/link-demands), und die vom-Typ überprüften Berechtigungen sind keine Teilmenge der Berechtigungen, die von der Methode überprüft werden.

## <a name="rule-description"></a>Regelbeschreibung
Eine Methode sollte nicht sowohl eine deklarative Sicherheit auf Methoden Ebene als auch auf Typebene für dieselbe Aktion aufweisen. Die beiden Überprüfungen werden nicht kombiniert. nur die Anforderung auf Methoden Ebene wird angewendet. Wenn z. b. ein Typ die `X`-Berechtigung erfordert und eine der Methoden die `Y`-Berechtigung erfordert, muss der Code nicht `X` über die Berechtigung zum Ausführen der Methode verfügen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Überprüfen Sie den Code, um sicherzustellen, dass beide Aktionen erforderlich sind. Wenn beide Aktionen erforderlich sind, stellen Sie sicher, dass die Aktion auf Methoden Ebene die auf der Typebene angegebene Sicherheit einschließt. Wenn `X` `Y` derTyp`Y`beispielsweise die-Berechtigung erfordert und seine-Methode auch die -Berechtigunganfordernmuss,solltedie-Methodeundexplizitaufrufen.`X`

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn die-Methode nicht die vom-Typ angegebene Sicherheit erfordert. Dies ist jedoch kein normales Szenario und deutet möglicherweise auf eine sorgfältige Entwurfs Überprüfung hin.

## <a name="example-1"></a>Beispiel 1

Im folgenden Beispiel werden Umgebungs Berechtigungen verwendet, um die Gefahren bei Verstößen gegen diese Regel zu veranschaulichen. In diesem Beispiel erstellt der Anwendungscode eine Instanz des gesicherten Typs, bevor die Berechtigung verweigert wird, die für den Typ erforderlich ist. In einem realen Bedrohungsszenario benötigt die Anwendung eine andere Möglichkeit zum Abrufen einer Instanz des Objekts.

Im folgenden Beispiel fordert die Bibliothek Schreibberechtigungen für einen Typ und eine Leseberechtigung für eine Methode an.

[!code-csharp[FxCop.Security.MethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_1.cs)]

## <a name="example-2"></a>Beispiel 2

Der folgende Anwendungscode veranschaulicht das Sicherheitsrisiko der Bibliothek, indem die-Methode aufgerufen wird, obwohl Sie die Sicherheitsanforderung auf Typebene nicht erfüllt.

[!code-csharp[FxCop.Security.TestMethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_2.cs)]

Dieses Beispiel erzeugt die folgende Ausgabe:

```txt
[All permissions] Personal information: 6/16/1964 12:00:00 AM
[No write permission (demanded by type)] Personal information: 6/16/1964 12:00:00 AM
[No read permission (demanded by method)] Could not access personal information: Request failed.
```

## <a name="see-also"></a>Siehe auch

- [Richtlinien für das Schreiben von sicherem Code](/dotnet/standard/security/secure-coding-guidelines)
- [Link Aufrufe](/dotnet/framework/misc/link-demands)
- [Daten und Modellierung](/dotnet/framework/data/index)