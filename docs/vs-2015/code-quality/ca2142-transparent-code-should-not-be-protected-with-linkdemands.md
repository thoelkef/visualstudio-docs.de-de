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
ms.openlocfilehash: a9d8986e9d1e6fc3f614e23fff3f6a24c1cc6e91
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602776"
---
# <a name="ca2142-transparent-code-should-not-be-protected-with-linkdemands"></a>CA2142: Transparenter Code darf nicht mit LinkDemands geschützt werden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|Transparentmethodsschulter dnotbeprotectedwithlinkdemand|
|CheckId|CA2142|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine transparente Methode erfordert eine <xref:System.Security.Permissions.SecurityAction> oder eine andere Sicherheitsanforderung.

## <a name="rule-description"></a>Regelbeschreibung
 Diese Regel wird für transparente Methoden ausgelöst, die einen Zugriff durch LinkDemands erfordern. Sicherheitstransparenter Code sollte nicht für das Überprüfen der Sicherheit einer Operation zuständig sein und sollte daher keine Berechtigungen fordern. Da transparente Methoden Sicherheits neutral sein sollen, sollten Sie keine Sicherheitsentscheidungen treffen. Außerdem sollte sicherer kritischer Code, der Sicherheitsentscheidungen trifft, nicht auf transparentem Code beruhen, der zuvor eine solche Entscheidung getroffen hat.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den Link Aufruf für die transparente Methode, oder markieren Sie die Methode mit <xref:System.Security.SecuritySafeCriticalAttribute>-Attribut, wenn es Sicherheitsüberprüfungen durchführt, z. b. Sicherheitsanforderungen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird die-Regel für die-Methode ausgelöst, da die-Methode transparent ist und mit einem LinkDemand-<xref:System.Security.PermissionSet> gekennzeichnet ist, der einen-<xref:System.Security.Permissions.SecurityAction> enthält.

 [!code-csharp[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2142.transparentmethodsshouldnotbeprotectedwithlinkdemands/cs/ca2142 -transparentmethodsshouldnotbeprotectedwithlinkdemands.cs#1)]

 Unterdrücken Sie keine Warnung dieser Regel.
