---
title: 'CA1056: URI-Eigenschaften dürfen keine Zeichenfolgen sein'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UriPropertiesShouldNotBeStrings
- CA1056
helpviewer_keywords:
- UriPropertiesShouldNotBeStrings
- CA1056
ms.assetid: fdc99d29-0904-4a65-baa8-4f76833c953e
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 71c4428596281abf0ad606624bd67c40a490ee49
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45549377"
---
# <a name="ca1056-uri-properties-should-not-be-strings"></a>CA1056: URI-Eigenschaften dürfen keine Zeichenfolgen sein

|||
|-|-|
|TypeName|UriPropertiesShouldNotBeStrings|
|CheckId|CA1056|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Typ deklariert eine String-Eigenschaft, deren Name "Uri", "Uri", "Urn", "Urn", "Url" oder "Url" enthält.

## <a name="rule-description"></a>Regelbeschreibung
 Diese Regel teilt den Eigenschaftennamen in Token basierend auf der Pascal und überprüft, ob jedes Token "Uri", "Uri", "Urn", "Urn", "Url" oder "Url" entspricht. Wenn eine Übereinstimmung vorliegt, wird die Regel davon ausgegangen, dass die Eigenschaft einen uniform Resource Identifier (URI) darstellt. Eine Zeichenfolgendarstellung eines URIs ist anfällig für Analyse- und Codierungsfehler und kann zu Sicherheitsmängeln führen. Die <xref:System.Uri?displayProperty=fullName> Klasse stellt diese Dienste auf sichere Weise.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie die Eigenschaft, die eine <xref:System.Uri> Typ.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Es ist sicher, die mit dieser Regel eine Warnung zu unterdrücken, wenn die Eigenschaft keinen URI darstellt.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, `ErrorProne`, die gegen diese Regel und einen Typ, `SaferWay`, die die Regel erfüllt.

 [!code-csharp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1056-uri-properties-should-not-be-strings_1.cs)]
 [!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1056-uri-properties-should-not-be-strings_1.vb)]
 [!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1056-uri-properties-should-not-be-strings_1.cpp)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1054: URI-Parameter dürfen keine Zeichenfolgen sein](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: URI-Rückgabewerte dürfen keine Zeichenfolgen sein](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)

 [CA2234: Übergeben Sie System.Uri-Objekte anstelle von Zeichenfolgen](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1057: URI-Überladungen vom Typ string rufen Überladungen vom Typ System.Uri auf](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)