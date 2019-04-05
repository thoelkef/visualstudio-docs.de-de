---
title: 'CA1054: URI-Parameter dürfen keine Zeichenfolgen sein | Microsoft-Dokumentation'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f7af579cf92a785f9850805ae06743a15364eade
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58946596"
---
# <a name="ca1054-uri-parameters-should-not-be-strings"></a>CA1054: URI-Parameter dürfen keine Zeichenfolgen sein.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UriParametersShouldNotBeStrings|
|CheckId|CA1054|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Typ deklariert eine Methode mit einem Zeichenfolgenparameter, deren Name, "Uri", "Uri", "Urn", "Urn", "Url" oder "Url enthält" und der Typ deklariert keine entsprechende Überladung, die akzeptiert eine <xref:System.Uri?displayProperty=fullName> Parameter.

## <a name="rule-description"></a>Regelbeschreibung
 Diese Regel wird der Name des Parameters in Token auf Grundlage der Konvention Kamel-Schreibweise und überprüft, ob jedes Token "Uri", "Uri", "Urn", "Urn", "Url" oder "Url" entspricht. Wenn eine Übereinstimmung vorliegt, wird die Regel davon ausgegangen, dass der Parameter einen uniform Resource Identifier (URI) darstellt. Eine Zeichenfolgendarstellung eines URIs ist anfällig für Analyse- und Codierungsfehler und kann zu Sicherheitsmängeln führen. Wenn eine Methode eine Zeichenfolgendarstellung eines URIs annimmt, eine entsprechende Überladung bereitgestellt werden sollen, eine Instanz von akzeptiert die <xref:System.Uri> Klasse, die diese Dienste auf sichere Weise bereitstellt.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Parameter, um eine <xref:System.Uri> -Typ. Dies ist eine wichtige Änderung. Klicken Sie alternativ Geben Sie eine Überladung der Methode die akzeptiert eine <xref:System.Uri> -Parameter ist; dies ist eine nicht unterbrechende Änderung.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher eine Warnung dieser Regel zu unterdrücken, wenn der Parameter keinen URI darstellt.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, `ErrorProne`, die gegen diese Regel und einen Typ, `SaferWay`, die die Regel erfüllt.

 [!code-cpp[FxCop.Design.UriNotString#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cpp/FxCop.Design.UriNotString.cpp#1)]
 [!code-csharp[FxCop.Design.UriNotString#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cs/FxCop.Design.UriNotString.cs#1)]
 [!code-vb[FxCop.Design.UriNotString#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/vb/FxCop.Design.UriNotString.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1056: URI-Eigenschaften dürfen keine Zeichenfolgen sein.](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1055: URI-Rückgabewerte sollten keine Zeichenfolgen sein](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)

 [CA2234: Übergeben Sie System.Uri-Objekte anstelle von Zeichenfolgen](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1057: URI-Überladungen der Zeichenfolge aufrufen System.Uri-Überladungen](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)
