---
title: 'CA2234: übergeben Sie System. URI-Objekte anstelle von Zeichen folgen. Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PassSystemUriObjectsInsteadOfStrings
- CA2234
helpviewer_keywords:
- CA2234
- PassSystemUriObjectsInsteadOfStrings
ms.assetid: 14616b37-74c4-4286-b051-115d00aceb5f
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0ce5c076260886def089118a4d7211d75e0185c0
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545209"
---
# <a name="ca2234-pass-systemuri-objects-instead-of-strings"></a>CA2234: Übergeben Sie System.Uri-Objekte anstelle von Zeichenfolgen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|PassSystemUriObjectsInsteadOfStrings|
|CheckId|CA2234|
|Kategorie|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Eine Methode, die einen Zeichen folgen Parameter mit dem Namen "URI", "URI", "urn", "urn", "URL" oder "URL" enthält, wird aufgerufen. und der deklarierende Typ der Methode enthält eine entsprechende Methoden Überladung, die über einen- <xref:System.Uri?displayProperty=fullName> Parameter verfügt.

## <a name="rule-description"></a>Beschreibung der Regel
 Ein Parameter Name wird basierend auf der Camel-Schreibweise in Token aufgeteilt, und dann wird jedes Token dahingehend geprüft, ob es "URI", "URI", "urn", "urn", "URL" oder "URL" entspricht. Wenn eine Entsprechung vorhanden ist, wird davon ausgegangen, dass der Parameter einen URI (Uniform Resource Identifier) darstellt. Eine Zeichenfolgendarstellung eines URIs ist anfällig für Analyse- und Codierungsfehler und kann zu Sicherheitsmängeln führen. Die <xref:System.Uri> -Klasse stellt diese Dienste auf sichere und sichere Weise bereit. Wenn zwischen zwei über Ladungen, die sich nur in Bezug auf die Darstellung eines URIs unterscheiden, eine Auswahl besteht, sollte der Benutzer die-Überladung auswählen, die ein- <xref:System.Uri> Argument annimmt.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, müssen Sie die-Überladung aufrufen, die das- <xref:System.Uri> Argument annimmt.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn der Zeichen folgen Parameter keinen URI darstellt.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine-Methode, `ErrorProne` die gegen die-Regel verstößt, und eine-Methode, die die-Überladung `SaferWay` ordnungsgemäß aufruft <xref:System.Uri> .

 [!code-cpp[FxCop.Usage.PassUri#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/cpp/FxCop.Usage.PassUri.cpp#1)]
 [!code-csharp[FxCop.Usage.PassUri#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/cs/FxCop.Usage.PassUri.cs#1)]
 [!code-vb[FxCop.Usage.PassUri#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/vb/FxCop.Usage.PassUri.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1057: URI-Überladungen vom Typ string rufen Überladungen vom Typ System.Uri auf.](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)

 [CA1056: URI-Eigenschaften dürfen keine Zeichenfolgen sein.](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: URI-Parameter dürfen keine Zeichenfolgen sein.](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: URI-Rückgabewerte dürfen keine Zeichenfolgen sein.](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
