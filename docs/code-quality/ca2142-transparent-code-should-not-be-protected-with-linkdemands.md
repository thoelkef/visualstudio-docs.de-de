---
title: 'CA2142: Transparenter Code darf nicht mit LinkDemands geschützt werden'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2142
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 508d9606b07798a1aaa788d3d7ee87da4797dcad
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53899901"
---
# <a name="ca2142-transparent-code-should-not-be-protected-with-linkdemands"></a>CA2142: Transparenter Code darf nicht mit LinkDemands geschützt werden

|||
|-|-|
|TypeName|TransparentMethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2142|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine transparente Methode erfordert eine <xref:System.Security.Permissions.SecurityAction> oder andere sicherheitsanforderung.

## <a name="rule-description"></a>Regelbeschreibung
 Mit dieser Regel wird für transparente Methoden, die für den Zugriff LinkDemands erfordern ausgelöst. Sicherheitstransparenter Code sollte nicht für das Überprüfen der Sicherheit einer Operation zuständig sein und sollte daher keine Berechtigungen fordern. Da sind transparente Methoden, die Sicherheit neutral sein sollen, sollten sie keine sicherheitsentscheidungen vornehmen. Darüber hinaus sollten sichere Kritischer Code, der sicherheitsentscheidungen zu treffen, nicht auf transparentem Code bereits eine solche Entscheidung getroffen haben verlassen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den Linkaufruf für die transparente Methode aus, oder markieren Sie die Methode mit <xref:System.Security.SecuritySafeCriticalAttribute> Attribut, wenn sie Sicherheit ausgeführt werden überprüft, wie z. B. sicherheitsanforderungen.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel die Regel für die Methode wird ausgelöst, da die Methode transparent ist und durch LinkDemand gekennzeichnet ist <xref:System.Security.PermissionSet> , enthält ein <xref:System.Security.Permissions.SecurityAction>.

 [!code-csharp[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2142-transparent-code-should-not-be-protected-with-linkdemands_1.cs)]

 Unterdrücken Sie keine Warnung dieser Regel.