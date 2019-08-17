---
title: 'CA1055: URI-Rückgabewerte dürfen keine Zeichenfolgen sein.'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1055
- UriReturnValuesShouldNotBeStrings
helpviewer_keywords:
- UriReturnValuesShouldNotBeStrings
- CA1055
ms.assetid: 40e39873-7872-4988-8195-9eb0ade9ece0
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 45d9874316ec2a22f875e2ba4fe7d5406ff916c6
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547339"
---
# <a name="ca1055-uri-return-values-should-not-be-strings"></a>CA1055: URI-Rückgabewerte dürfen keine Zeichenfolgen sein.

|||
|-|-|
|TypeName|UriReturnValuesShouldNotBeStrings|
|CheckId|CA1055|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Der Name einer Methode enthält "URI", "URI", "urn", "urn", "URL" oder "URL", und die Methode gibt eine Zeichenfolge zurück.

Standardmäßig prüft diese Regel nur öffentliche Methoden, aber dies ist [konfigurierbar](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

Diese Regel teilt den Methodennamen in Token auf der Grundlage der Pascal-Schreibweise und überprüft, ob jedes Token mit "URI", "URI", "urn", "urn", "URL" oder "URL" übereinstimmen. Wenn eine Entsprechung vorliegt, geht die Regel davon aus, dass die Methode einen URI (Uniform Resource Identifier) zurückgibt. Eine Zeichenfolgendarstellung eines URIs ist anfällig für Analyse- und Codierungsfehler und kann zu Sicherheitsmängeln führen. Die <xref:System.Uri?displayProperty=fullName> -Klasse stellt diese Dienste auf sichere und sichere Weise bereit.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Rückgabetyp in <xref:System.Uri>.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn der Rückgabewert keinen URI darstellt.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel von [FxCop](install-fxcop-analyzers.md) Analyzer (und nicht mit der Legacy Analyse) ausführen, können Sie basierend auf ihrer Barrierefreiheit konfigurieren, für welche Teile Ihrer Codebasis diese Regel ausgeführt werden soll. Um z. b. anzugeben, dass die Regel nur für die nicht öffentliche API-Oberfläche ausgeführt werden soll, fügen Sie das folgende Schlüssel-Wert-Paar in eine Editor config-Datei in Ihrem Projekt ein:

```ini
dotnet_code_quality.ca1055.api_surface = private, internal
```

Sie können diese Option nur für diese Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Entwurf) konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren von FxCop-Analysen](configure-fxcop-analyzers.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt einen Typ `ErrorProne`,, der gegen diese Regel verstößt, und einen Typ, `SaferWay`, der die Regel erfüllt.

[!code-csharp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1055-uri-return-values-should-not-be-strings_1.cs)]
[!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1055-uri-return-values-should-not-be-strings_1.vb)]
[!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1055-uri-return-values-should-not-be-strings_1.cpp)]

## <a name="related-rules"></a>Verwandte Regeln

- [CA1056: Uri-Eigenschaften dürfen keine Zeichen folgen sein.](../code-quality/ca1056-uri-properties-should-not-be-strings.md)
- [CA1054: URI-Parameter dürfen keine Zeichen folgen sein.](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)
- [CA2234: Übergeben Sie System. URI-Objekte anstelle von Zeichen folgen.](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)
- [CA1057: Zeichen folgen-URI-über Ladungen werden System. URI-über Ladungen aufgerufen](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)