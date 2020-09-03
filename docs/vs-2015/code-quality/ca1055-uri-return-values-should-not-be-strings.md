---
title: 'CA1055: URI-Rückgabewerte dürfen keine Zeichen folgen sein. Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1055
- UriReturnValuesShouldNotBeStrings
helpviewer_keywords:
- UriReturnValuesShouldNotBeStrings
- CA1055
ms.assetid: 40e39873-7872-4988-8195-9eb0ade9ece0
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 522534d81ef9c87fc93d16a7ee880c7743a3268c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539658"
---
# <a name="ca1055-uri-return-values-should-not-be-strings"></a>CA1055: URI-Rückgabewerte dürfen keine Zeichenfolgen sein.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|UriReturnValuesShouldNotBeStrings|
|CheckId|CA1055|
|Category|Microsoft. Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Der Name einer Methode enthält "URI", "URI", "urn", "urn", "URL" oder "URL", und die Methode gibt eine Zeichenfolge zurück.

## <a name="rule-description"></a>Beschreibung der Regel
 Diese Regel teilt den Methodennamen in Token auf der Grundlage der Pascal-Schreibweise und überprüft, ob jedes Token mit "URI", "URI", "urn", "urn", "URL" oder "URL" übereinstimmen. Wenn eine Entsprechung vorliegt, geht die Regel davon aus, dass die Methode einen URI (Uniform Resource Identifier) zurückgibt. Eine Zeichenfolgendarstellung eines URIs ist anfällig für Analyse- und Codierungsfehler und kann zu Sicherheitsmängeln führen. Die <xref:System.Uri?displayProperty=fullName> -Klasse stellt diese Dienste auf sichere und sichere Weise bereit.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Rückgabetyp in <xref:System.Uri> .

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn der Rückgabewert keinen URI darstellt.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, `ErrorProne` , der gegen diese Regel verstößt, und einen Typ, `SaferWay` , der die Regel erfüllt.

 [!code-cpp[FxCop.Design.UriNotString#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cpp/FxCop.Design.UriNotString.cpp#1)]
 [!code-csharp[FxCop.Design.UriNotString#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cs/FxCop.Design.UriNotString.cs#1)]
 [!code-vb[FxCop.Design.UriNotString#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/vb/FxCop.Design.UriNotString.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1056: URI-Eigenschaften dürfen keine Zeichenfolgen sein.](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: URI-Parameter dürfen keine Zeichenfolgen sein.](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA2234: Übergeben Sie System.Uri-Objekte anstelle von Zeichenfolgen.](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1057: URI-Überladungen vom Typ string rufen Überladungen vom Typ System.Uri auf.](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)
