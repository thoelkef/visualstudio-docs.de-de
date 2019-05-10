---
title: 'CA2243: Attribute-Zeichenfolgenliterale müssen stets richtig analysiert | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2243
- AttributeStringLiteralsShouldParseCorrectly
helpviewer_keywords:
- AttributeStringLiteralsShouldParseCorrectly
- CA2243
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f23db8a9674de621090be70067a555ef4fca2b99
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60061423"
---
# <a name="ca2243-attribute-string-literals-should-parse-correctly"></a>CA2243: Attribute-Zeichenfolgenliterale müssen stets richtig analysiert werden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AttributeStringLiteralsShouldParseCorrectly|
|CheckId|CA2243|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Ein Attribut des Zeichenfolgenliteral-Parameter wird für eine URL, GUID oder Version nicht ordnungsgemäß analysiert.

## <a name="rule-description"></a>Regelbeschreibung
 Da Attribute abgeleitet werden <xref:System.Attribute?displayProperty=fullName>, und Attribute werden zum Zeitpunkt der Kompilierung verwendet, nur konstante Werte, die an ihre Konstruktoren übergeben werden können. Zuordnen von Parametern, die URLs, die GUIDs und -Versionen darstellen müssen, können nicht als eingegeben werden <xref:System.Uri?displayProperty=fullName>, <xref:System.Guid?displayProperty=fullName>, und <xref:System.Version?displayProperty=fullName>, da diese Typen als Konstanten dargestellt werden können. Sie müssen stattdessen durch Zeichenfolgen dargestellt werden.

 Da der Parameter als Zeichenfolge typisiert ist, ist es möglich, dass zum Zeitpunkt der Kompilierung ein falsch formatierter Parameter übergeben werden kann.

 Diese Regel wird eine Benennungskonvention Heuristik verwendet wird, um Parameter zu finden, die einen uniform Resource Identifier (URI), eine GUID (GLOBALLY Unique Identifier) oder eine Version darstellen, und stellt sicher, dass der übergebene Wert richtig ist.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Ändern Sie die Zeichenfolge in eine ordnungsgemäß formatierte URL, GUID oder Version an.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, die mit dieser Regel eine Warnung zu unterdrücken, wenn der Parameter keine URL, GUID oder Version darstellt.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt Code für die AssemblyFileVersionAttribute, die gegen diese Regel verstößt.

 [!code-csharp[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly/cs/FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly.cs#1)]

 Die Regel wird durch Folgendes ausgelöst:

- Parameter, 'Version' enthalten und können nicht analysiert werden, um System.Version.

- Parameter, "Guid" enthalten und können nicht analysiert werden, um System.Guid.

- Parameter, "Uri", "Urn" oder "Url" enthalten und können nicht analysiert werden, in System.Uri.

## <a name="see-also"></a>Siehe auch
 [CA1054: URI-Parameter dürfen keine Zeichenfolgen sein.](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)
