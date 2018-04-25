---
title: 'CA1054: URI-Parameter dürfen keine Zeichenfolgen sein'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1054
- UriParametersShouldNotBeStrings
helpviewer_keywords:
- CA1054
- UriParametersShouldNotBeStrings
ms.assetid: 8e99d72b-a658-47a7-8dd5-9784ce2c30b8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 98e042d65e0c7530c35134f79357565e1b88f4de
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="ca1054-uri-parameters-should-not-be-strings"></a>CA1054: URI-Parameter dürfen keine Zeichenfolgen sein
|||
|-|-|
|TypeName|UriParametersShouldNotBeStrings|
|CheckId|CA1054|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Typ deklariert eine Methode mit einem String-Parameter, deren Name, "Uri", "Uri", "Urn", "Urn", "Url" oder "Url enthält" und der Typ deklariert eine entsprechende Überladung, die akzeptiert eine <xref:System.Uri?displayProperty=fullName> Parameter.

## <a name="rule-description"></a>Regelbeschreibung
 Diese Regel Token basierend auf der Kamel teilt den Parameternamen und überprüft, ob jedes Token "Uri", "Uri", "Urn", "Urn", "Url" oder "Url" entspricht. Wenn eine Übereinstimmung vorhanden ist, wird die Regel davon ausgegangen, dass der Parameter einen uniform Resource Identifier (URI) darstellt. Eine Zeichenfolgendarstellung eines URIs ist anfällig für Analyse- und Codierungsfehler und kann zu Sicherheitsmängeln führen. Wenn eine Methode eine Zeichenfolgendarstellung eines URIs annimmt, eine entsprechende Überladung sollte angegeben werden, eine Instanz von akzeptiert die <xref:System.Uri> -Klasse, die diese Dienste auf sichere Weise bereitstellt.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Parameter an eine <xref:System.Uri> geben; Dies ist eine wichtige Änderung. Klicken Sie alternativ Geben Sie eine Überladung der Methode nimmt einen <xref:System.Uri> Parameter; Dies ist eine nicht unterbrechende Änderung.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Sie können ruhig zum Unterdrücken einer Warnung dieser Regel, wenn der Parameter keinen URI darstellt.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ `ErrorProne`, die mit dieser Regel und einen Typ, verletzt `SaferWay`, die die Regel erfüllt.

 [!code-csharp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1054-uri-parameters-should-not-be-strings_1.cs)]
 [!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1054-uri-parameters-should-not-be-strings_1.vb)]
 [!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1054-uri-parameters-should-not-be-strings_1.cpp)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1056: URI-Eigenschaften dürfen keine Zeichenfolgen sein](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1055: URI-Rückgabewerte dürfen keine Zeichenfolgen sein](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)

 [CA2234: Übergeben Sie System.Uri-Objekte anstelle von Zeichenfolgen](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1057: URI-Überladungen vom Typ string rufen Überladungen vom Typ System.Uri auf](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)