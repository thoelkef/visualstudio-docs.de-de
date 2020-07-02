---
title: 'CA2142: transparenter Code darf nicht mit LinkDemand geschützt werden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2142
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: aa6bd9dcacc5fb863199c740a71c824f14739052
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546431"
---
# <a name="ca2142-transparent-code-should-not-be-protected-with-linkdemands"></a>CA2142: Transparenter Code darf nicht mit LinkDemands geschützt werden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|Transparentmethodsschulter dnotbeprotectedwithlinkdemand|
|CheckId|CA2142|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine transparente Methode erfordert eine <xref:System.Security.Permissions.SecurityAction> oder eine andere Sicherheitsanforderung.

## <a name="rule-description"></a>Beschreibung der Regel
 Diese Regel wird für transparente Methoden ausgelöst, die einen Zugriff durch LinkDemands erfordern. Sicherheitstransparenter Code sollte nicht für das Überprüfen der Sicherheit einer Operation zuständig sein und sollte daher keine Berechtigungen fordern. Da transparente Methoden Sicherheits neutral sein sollen, sollten Sie keine Sicherheitsentscheidungen treffen. Außerdem sollte sicherer kritischer Code, der Sicherheitsentscheidungen trifft, nicht auf transparentem Code beruhen, der zuvor eine solche Entscheidung getroffen hat.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den Link Aufruf für die transparente Methode, oder markieren Sie die Methode mit dem- <xref:System.Security.SecuritySafeCriticalAttribute> Attribut, wenn Sie Sicherheitsüberprüfungen durchführt, z. b. Sicherheitsanforderungen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird die-Regel für die-Methode ausgelöst, da die-Methode transparent ist und mit einem LinkDemand gekennzeichnet ist <xref:System.Security.PermissionSet> , der eine enthält <xref:System.Security.Permissions.SecurityAction> .

 [!code-csharp[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2142.transparentmethodsshouldnotbeprotectedwithlinkdemands/cs/ca2142 -transparentmethodsshouldnotbeprotectedwithlinkdemands.cs#1)]

 Unterdrücken Sie keine Warnung dieser Regel.
