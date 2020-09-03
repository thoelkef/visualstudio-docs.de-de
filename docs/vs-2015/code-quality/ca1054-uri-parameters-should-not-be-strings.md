---
title: 'CA1054: URI-Parameter dürfen keine Zeichen folgen sein | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1054
- UriParametersShouldNotBeStrings
helpviewer_keywords:
- CA1054
- UriParametersShouldNotBeStrings
ms.assetid: 8e99d72b-a658-47a7-8dd5-9784ce2c30b8
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: babef652bbfa55d6549cf0e43ddae0920b3ff302
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539489"
---
# <a name="ca1054-uri-parameters-should-not-be-strings"></a>CA1054: URI-Parameter dürfen keine Zeichenfolgen sein.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|UriParametersShouldNotBeStrings|
|CheckId|CA1054|
|Category|Microsoft. Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Typ deklariert eine Methode mit einem Zeichen folgen Parameter, dessen Name "URI", "URI", "urn", "urn", "URL" oder "URL" enthält, und der Typ deklariert keine entsprechende Überladung, die einen- <xref:System.Uri?displayProperty=fullName> Parameter annimmt.

## <a name="rule-description"></a>Beschreibung der Regel
 Diese Regel teilt den Parameternamen auf Grundlage der Camel-Schreibweise in Token auf und überprüft, ob jedes Token mit "URI", "URI", "urn", "urn", "URL" oder "URL" übereinstimmen. Wenn eine Entsprechung vorhanden ist, geht die Regel davon aus, dass der Parameter einen URI (Uniform Resource Identifier) darstellt. Eine Zeichenfolgendarstellung eines URIs ist anfällig für Analyse- und Codierungsfehler und kann zu Sicherheitsmängeln führen. Wenn eine Methode eine Zeichen folgen Darstellung eines URIs annimmt, sollte eine entsprechende Überladung bereitgestellt werden, die eine Instanz der <xref:System.Uri> -Klasse annimmt, die diese Dienste auf sichere und sichere Weise bereitstellt.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den-Parameter in einen- <xref:System.Uri> Typ. Dies ist eine Breaking Change. Alternativ dazu können Sie eine Überladung der-Methode bereitstellen, die einen- <xref:System.Uri> Parameter annimmt. Dies ist eine nicht unterbrechende Änderung.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn der Parameter keinen URI darstellt.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, `ErrorProne` , der gegen diese Regel verstößt, und einen Typ, `SaferWay` , der die Regel erfüllt.

 [!code-cpp[FxCop.Design.UriNotString#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cpp/FxCop.Design.UriNotString.cpp#1)]
 [!code-csharp[FxCop.Design.UriNotString#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cs/FxCop.Design.UriNotString.cs#1)]
 [!code-vb[FxCop.Design.UriNotString#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/vb/FxCop.Design.UriNotString.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1056: URI-Eigenschaften dürfen keine Zeichenfolgen sein.](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1055: URI-Rückgabewerte dürfen keine Zeichenfolgen sein.](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)

 [CA2234: Übergeben Sie System.Uri-Objekte anstelle von Zeichenfolgen.](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1057: URI-Überladungen vom Typ string rufen Überladungen vom Typ System.Uri auf.](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)
