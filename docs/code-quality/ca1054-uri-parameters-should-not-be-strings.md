---
title: 'CA1054: URI-Parameter dürfen keine Zeichenfolgen sein.'
ms.date: 03/11/2019
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
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 49788b900eb8aed9fac6e4da4844377bae67efbf
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235557"
---
# <a name="ca1054-uri-parameters-should-not-be-strings"></a>CA1054: URI-Parameter dürfen keine Zeichenfolgen sein.

|||
|-|-|
|TypeName|UriParametersShouldNotBeStrings|
|CheckId|CA1054|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Ein Typ deklariert eine Methode mit einem Zeichen folgen Parameter, dessen Name "URI", "URI", "urn", "urn", "URL" oder "URL" enthält, und der Typ deklariert keine entsprechende Überladung, die <xref:System.Uri?displayProperty=fullName> einen-Parameter annimmt.

Standardmäßig betrachtet diese Regel nur extern sichtbare Typen, aber dies ist [konfigurierbar](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

Diese Regel teilt den Parameternamen auf Grundlage der Camel-Schreibweise in Token auf und überprüft, ob jedes Token mit "URI", "URI", "urn", "urn", "URL" oder "URL" übereinstimmen. Wenn eine Entsprechung vorhanden ist, geht die Regel davon aus, dass der Parameter einen URI (Uniform Resource Identifier) darstellt. Eine Zeichenfolgendarstellung eines URIs ist anfällig für Analyse- und Codierungsfehler und kann zu Sicherheitsmängeln führen. Wenn eine Methode eine Zeichen folgen Darstellung eines URIs annimmt, sollte eine entsprechende Überladung bereitgestellt werden, die eine Instanz <xref:System.Uri> der-Klasse annimmt, die diese Dienste auf sichere und sichere Weise bereitstellt.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den- <xref:System.Uri> Parameter in einen-Typ. Dies ist eine Breaking Change. Alternativ dazu können Sie eine Überladung der-Methode bereit <xref:System.Uri> stellen, die einen-Parameter annimmt. Dies ist ein nicht-Breaking Change.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn der Parameter keinen URI darstellt.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel von [FxCop](install-fxcop-analyzers.md) Analyzer (und nicht mit der Legacy Analyse) ausführen, können Sie basierend auf ihrer Barrierefreiheit konfigurieren, für welche Teile Ihrer Codebasis diese Regel ausgeführt werden soll. Um z. b. anzugeben, dass die Regel nur für die nicht öffentliche API-Oberfläche ausgeführt werden soll, fügen Sie das folgende Schlüssel-Wert-Paar in eine Editor config-Datei in Ihrem Projekt ein:

```ini
dotnet_code_quality.ca1054.api_surface = private, internal
```

Sie können diese Option nur für diese Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Entwurf) konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren von FxCop-Analysen](configure-fxcop-analyzers.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt einen Typ `ErrorProne`,, der gegen diese Regel verstößt, und einen Typ, `SaferWay`, der die Regel erfüllt.

[!code-csharp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1054-uri-parameters-should-not-be-strings_1.cs)]
[!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1054-uri-parameters-should-not-be-strings_1.vb)]
[!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1054-uri-parameters-should-not-be-strings_1.cpp)]

## <a name="related-rules"></a>Verwandte Regeln

- [CA1056: Uri-Eigenschaften dürfen keine Zeichen folgen sein.](../code-quality/ca1056-uri-properties-should-not-be-strings.md)
- [CA1055: URI-Rückgabewerte dürfen keine Zeichen folgen sein.](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
- [CA2234: Übergeben Sie System. URI-Objekte anstelle von Zeichen folgen.](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)
- [CA1057: Zeichen folgen-URI-über Ladungen werden System. URI-über Ladungen aufgerufen](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)