---
title: 'CA2143: transparente Methoden dürfen keine Sicherheitsanforderungen verwenden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2143
ms.assetid: 5d3923d7-cf40-4512-bc5c-0db0e0d6e25a
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ca8f049da83b99da7d36ebf74e756dd95f738d64
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546470"
---
# <a name="ca2143-transparent-methods-should-not-use-security-demands"></a>CA2143: Transparente Methoden dürfen keine Sicherheitsanforderungen verwenden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|Transparentmethodsschuldnotdemand|
|CheckId|CA2143|
|Category|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein übergeordneter Typ oder eine übergeordnete Methode wird deklarativ mit einem Bedarf gekennzeichnet, oder die-Methode <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> `.Demand` Ruft die- <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> Methode auf.

## <a name="rule-description"></a>Beschreibung der Regel
 Sicherheitstransparenter Code sollte nicht für das Überprüfen der Sicherheit einer Operation zuständig sein und sollte daher keine Berechtigungen fordern. Sicherheitstransparenter Code sollte mithilfe von vollständigen Anforderungen Sicherheitsentscheidungen fällen, und sicherheitskritischer Code sollte für die vollständige Anforderung nicht auf transparentem Code beruhen. Jeder Code, der Sicherheitsüberprüfungen durchführt, wie z. b. Sicherheitsanforderungen, sollte stattdessen sicherheitsrelevant sein.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, markieren Sie die Methode im Allgemeinen mit dem- <xref:System.Security.SecuritySafeCriticalAttribute> Attribut. Sie können auch die Anforderung entfernen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Die Regel Dateien für den folgenden Code, da eine transparente Methode eine deklarative Sicherheitsanforderung durchführt.

 [!code-csharp[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2143.transparentmethodsshouldnotdemand/cs/ca2143 - transparentmethodsshouldnotdemand.cs#1)]

## <a name="see-also"></a>Weitere Informationen
 [CA2142: Transparenter Code darf nicht mit LinkDemands geschützt werden.](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)
