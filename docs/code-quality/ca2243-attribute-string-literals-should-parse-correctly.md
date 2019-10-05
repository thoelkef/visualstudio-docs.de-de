---
title: 'CA2243: Attribute-Zeichenfolgenliterale müssen stets richtig analysiert werden.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2243
- AttributeStringLiteralsShouldParseCorrectly
helpviewer_keywords:
- AttributeStringLiteralsShouldParseCorrectly
- CA2243
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2627e94dbdd0504b164fee3ecd95dc99b3094db7
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237817"
---
# <a name="ca2243-attribute-string-literals-should-parse-correctly"></a>CA2243: Attribute-Zeichenfolgenliterale müssen stets richtig analysiert werden.

|||
|-|-|
|TypeName|AttributeStringLiteralsShouldParseCorrectly|
|CheckId|CA2243|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
Der zeichenfolgenliteralparameter eines Attributs wird für eine URL, eine GUID oder eine Version nicht ordnungsgemäß analysiert.

## <a name="rule-description"></a>Regelbeschreibung
Da Attribute von <xref:System.Attribute?displayProperty=fullName>abgeleitet werden und Attribute zur Kompilierzeit verwendet werden, können nur konstante Werte an Ihre Konstruktoren übergeben werden. Attribut Parameter, die URLs, GUIDs und Versionen darstellen müssen, können nicht als <xref:System.Uri?displayProperty=fullName>, <xref:System.Guid?displayProperty=fullName>und <xref:System.Version?displayProperty=fullName>eingegeben werden, da diese Typen nicht als Konstanten dargestellt werden können. Stattdessen müssen Sie durch Zeichen folgen dargestellt werden.

Da der-Parameter als Zeichenfolge typisiert ist, kann es vorkommen, dass ein falsch formatierter Parameter zum Zeitpunkt der Kompilierung übergeben werden kann.

Diese Regel verwendet eine namens-Heuristik, um Parameter zu suchen, die einen URI (Uniform Resource Identifier), einen global eindeutigen Bezeichner (GUID) oder eine Version darstellen, und überprüft, ob der bestandene Wert korrekt ist.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Ändern Sie die Parameter Zeichenfolge in eine ordnungsgemäß formatierte URL, GUID oder Version.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn der Parameter keine URL, GUID oder Version darstellt.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt den Code für das AssemblyFileVersionAttribute, das gegen diese Regel verstößt.

[!code-csharp[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../code-quality/codesnippet/CSharp/ca2243-attribute-string-literals-should-parse-correctly_1.cs)]

Die Regel wird durch die folgenden Parameter ausgelöst:

- Parameter, die ' Version ' enthalten und nicht in System. Version analysiert werden können.

- Parameter, die ' GUID ' enthalten und nicht in ' System. GUID ' analysiert werden können.

- Parameter, die ' URI ', ' urn ' oder ' URL ' enthalten und nicht in ' System. URI ' analysiert werden können.

## <a name="see-also"></a>Siehe auch

- [CA1054: URI-Parameter dürfen keine Zeichen folgen sein.](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)