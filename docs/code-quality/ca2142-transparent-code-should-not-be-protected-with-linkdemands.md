---
title: 'CA2142: Transparenter Code darf nicht mit LinkDemands geschützt werden.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2142
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf5bb8320a8876582cc325ecf973c83593777193
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920501"
---
# <a name="ca2142-transparent-code-should-not-be-protected-with-linkdemands"></a>CA2142: Transparenter Code darf nicht mit LinkDemands geschützt werden.

|||
|-|-|
|TypeName|TransparentMethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2142|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
Eine transparente Methode erfordert eine <xref:System.Security.Permissions.SecurityAction> oder eine andere Sicherheitsanforderung.

## <a name="rule-description"></a>Regelbeschreibung
Diese Regel wird für transparente Methoden ausgelöst, die LinkDemand benötigen, um darauf zuzugreifen. Sicherheitstransparenter Code sollte nicht für das Überprüfen der Sicherheit einer Operation zuständig sein und sollte daher keine Berechtigungen fordern. Da transparente Methoden Sicherheits neutral sein sollen, sollten Sie keine Sicherheitsentscheidungen treffen. Außerdem sollte sicherer kritischer Code, der Sicherheitsentscheidungen trifft, nicht auf transparentem Code beruhen, der zuvor eine solche Entscheidung getroffen hat.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den Link Aufruf für die transparente Methode, oder markieren <xref:System.Security.SecuritySafeCriticalAttribute> Sie die Methode mit dem-Attribut, wenn Sie Sicherheitsüberprüfungen durchführt, z. b. Sicherheitsanforderungen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
Im folgenden Beispiel wird die-Regel für die-Methode ausgelöst, da die-Methode transparent ist und mit einem LinkDemand <xref:System.Security.PermissionSet> gekennzeichnet ist, der eine <xref:System.Security.Permissions.SecurityAction>enthält.

[!code-csharp[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2142-transparent-code-should-not-be-protected-with-linkdemands_1.cs)]

Unterdrücken Sie keine Warnung dieser Regel.