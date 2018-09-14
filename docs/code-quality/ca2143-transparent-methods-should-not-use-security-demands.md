---
title: 'CA2143: Transparente Methoden dürfen keine Sicherheitsanforderungen verwenden'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2143
ms.assetid: 5d3923d7-cf40-4512-bc5c-0db0e0d6e25a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 88e38a2ae9c7cdf1cd8f8e664571add353a87dd7
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551297"
---
# <a name="ca2143-transparent-methods-should-not-use-security-demands"></a>CA2143: Transparente Methoden dürfen keine Sicherheitsanforderungen verwenden
|||
|-|-|
|TypeName|TransparentMethodsShouldNotDemand|
|CheckId|CA2143|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Einer transparenten Typ- oder deklarativ mit markiert einen <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> `.Demand` nach Bedarf, oder die Methode ruft die <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> Methode.

## <a name="rule-description"></a>Regelbeschreibung
 Sicherheitstransparenter Code sollte nicht für das Überprüfen der Sicherheit einer Operation zuständig sein und sollte daher keine Berechtigungen fordern. Sicherheitstransparenter Code sollte mithilfe von vollständigen Anforderungen Sicherheitsentscheidungen fällen, und sicherheitskritischer Code sollte für die vollständige Anforderung nicht auf transparentem Code beruhen. Jeder Code, der Sicherheit, wie z. B. sicherheitsanforderungen prüft, sollte stattdessen sicherheitsgeschützt sein.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, markieren Sie in der Regel die Methode mit dem <xref:System.Security.SecuritySafeCriticalAttribute> Attribut. Sie können auch den Bedarf entfernen.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Die Regel Dateien auf den folgenden Code, da eine transparente Methode eine deklarative Sicherheit-Anforderung ist.

 [!code-csharp[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../code-quality/codesnippet/CSharp/ca2143-transparent-methods-should-not-use-security-demands_1.cs)]

## <a name="see-also"></a>Siehe auch
 [CA2142: Transparenter Code darf nicht mit LinkDemands geschützt werden](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)