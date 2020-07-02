---
title: 'CA2243: Attribut Zeichenfolgenliterale sollten ordnungsgemäß analysiert werden | Microsoft-Dokumentation'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 09e932651576f9b6d595657ad024b8f2697ad016
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535745"
---
# <a name="ca2243-attribute-string-literals-should-parse-correctly"></a>CA2243: Attribute-Zeichenfolgenliterale müssen stets richtig analysiert werden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|AttributeStringLiteralsShouldParseCorrectly|
|CheckId|CA2243|
|Kategorie|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Der zeichenfolgenliteralparameter eines Attributs wird für eine URL, eine GUID oder eine Version nicht ordnungsgemäß analysiert.

## <a name="rule-description"></a>Beschreibung der Regel
 Da Attribute von abgeleitet werden <xref:System.Attribute?displayProperty=fullName> und Attribute zur Kompilierzeit verwendet werden, können nur konstante Werte an Ihre Konstruktoren übergeben werden. Attribut Parameter, die URLs, GUIDs und Versionen darstellen müssen, können nicht als <xref:System.Uri?displayProperty=fullName> , und eingegeben werden <xref:System.Guid?displayProperty=fullName> <xref:System.Version?displayProperty=fullName> , da diese Typen nicht als Konstanten dargestellt werden können. Stattdessen müssen Sie durch Zeichen folgen dargestellt werden.

 Da der-Parameter als Zeichenfolge typisiert ist, kann es vorkommen, dass ein falsch formatierter Parameter zum Zeitpunkt der Kompilierung übergeben werden kann.

 Diese Regel verwendet eine Benennungs-Heuristik, um Parameter zu suchen, die einen URI (Uniform Resource Identifier), einen global eindeutigen Bezeichner (GUID) oder eine Version darstellen, und überprüft, ob der bestandene Wert korrekt ist.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Ändern Sie die Parameter Zeichenfolge in eine ordnungsgemäß formatierte URL, GUID oder Version.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn der Parameter keine URL, GUID oder Version darstellt.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt den Code für das AssemblyFileVersionAttribute, das gegen diese Regel verstößt.

 [!code-csharp[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly/cs/FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly.cs#1)]

 Die Regel wird durch Folgendes ausgelöst:

- Parameter, die ' Version ' enthalten und nicht in System. Version analysiert werden können.

- Parameter, die ' GUID ' enthalten und nicht in ' System. GUID ' analysiert werden können.

- Parameter, die ' URI ', ' urn ' oder ' URL ' enthalten und nicht in ' System. URI ' analysiert werden können.

## <a name="see-also"></a>Weitere Informationen
 [CA1054: URI-Parameter dürfen keine Zeichenfolgen sein.](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)
