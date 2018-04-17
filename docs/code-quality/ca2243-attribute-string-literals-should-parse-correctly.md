---
title: 'CA2243: Attribute-Zeichenfolgenliterale analysieren soll, ordnungsgemäß | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2243
- AttributeStringLiteralsShouldParseCorrectly
helpviewer_keywords:
- AttributeStringLiteralsShouldParseCorrectly
- CA2243
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0715624391b766649e48775470ed9e27f47f9613
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ca2243-attribute-string-literals-should-parse-correctly"></a>CA2243: Attribute-Zeichenfolgenliterale müssen stets richtig analysiert werden
|||  
|-|-|  
|TypeName|AttributeStringLiteralsShouldParseCorrectly|  
|CheckId|CA2243|  
|Kategorie|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechende Änderung|  
  
## <a name="cause"></a>Ursache  
 Ein Attribut Zeichenfolgenliteral-Parameter wird für eine URL, GUID oder Version nicht ordnungsgemäß analysiert.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Da Attribute abgeleitet sind <xref:System.Attribute?displayProperty=fullName>, und Attribute werden zum Zeitpunkt der Kompilierung verwendet, nur konstante Werte an ihre Konstruktoren übergeben werden können. Attributparameter, die URLs, die GUIDs und -Versionen darstellen müssen nicht typisiert werden, als <xref:System.Uri?displayProperty=fullName>, <xref:System.Guid?displayProperty=fullName>, und <xref:System.Version?displayProperty=fullName>, da diese Typen nicht als Konstanten dargestellt werden können. Stattdessen müssen sie durch Zeichenfolgen dargestellt werden.  
  
 Da der Parameter als Zeichenfolge typisiert ist, ist es möglich, dass zum Zeitpunkt der Kompilierung ein falsch formatierter Parameter übergeben werden könnte.  
  
 Diese Regel verwendet eine Benennungskonvention Heuristik, um Parameter zu finden, die einen uniform Resource Identifier (URI), eine GUID (GLOBALLY Unique Identifier) oder eine Version darstellen und stellt sicher, dass der übergebene Wert richtig ist.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Ändern Sie die Parameterzeichenfolge eine ordnungsgemäß formatierte URL, GUID oder Version.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können ruhig zum Unterdrücken einer Warnung dieser Regel, wenn der Parameter keine URL, GUID oder Version darstellt.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt den Code für die AssemblyFileVersionAttribute, die mit dieser Regel verletzt.  
  
 [!code-csharp[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../code-quality/codesnippet/CSharp/ca2243-attribute-string-literals-should-parse-correctly_1.cs)]  
  
 Die Regel wird durch die folgenden ausgelöst:  
  
-   Parameter, die "Version" enthalten und können nicht analysiert werden, um System.Version.  
  
-   Parameter, "Guid" enthalten und können nicht analysiert werden, um System.Guid.  
  
-   Parameter, die "Uri", "Urn" oder "Url" enthalten und können nicht in System.Uri analysiert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [CA1054: URI-Parameter dürfen keine Zeichenfolgen sein](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)