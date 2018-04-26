---
title: 'CA1057: URI-Überladungen vom Typ string rufen Überladungen vom Typ System.Uri auf'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1057
- StringUriOverloadsCallSystemUriOverloads
helpviewer_keywords:
- StringUriOverloadsCallSystemUriOverloads
- CA1057
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 63386e73cee4d2e0c1c34f31f0042312fef4869f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057: URI-Überladungen vom Typ string rufen Überladungen vom Typ System.Uri auf
|||
|-|-|
|TypeName|StringUriOverloadsCallSystemUriOverloads|
|CheckId|CA1057|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Typ deklariert methodenüberladungen, die sich nur durch die Ersetzung eines Zeichenfolgenparameters mit unterscheiden eine <xref:System.Uri?displayProperty=fullName> Parameter und die Überladung, die den Zeichenfolgenparameter akzeptiert rufen nicht die Überladung, akzeptiert der <xref:System.Uri> Parameter.

## <a name="rule-description"></a>Regelbeschreibung
 Da die Überladungen nur durch die Zeichenfolge unterscheiden /<xref:System.Uri> Parameter, die Zeichenfolge wird davon ausgegangen, dass einen uniform Resource Identifier (URI) darstellen. Eine Zeichenfolgendarstellung eines URIs ist anfällig für Analyse- und Codierungsfehler und kann zu Sicherheitsmängeln führen. Die <xref:System.Uri> Klasse stellt diese Dienste auf sichere Weise bereit. Um die Vorteile der Nutzen der <xref:System.Uri> -Klasse, die zeichenfolgenüberladung sollte Aufrufen der <xref:System.Uri> überladen, mit dem Zeichenfolgenargument.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Erneut implementieren Sie die Methode, die die Darstellung des URIS wird verwendet, sodass Erstellung einer Instanz von der <xref:System.Uri> Klasse mit dem Zeichenfolgenargument und übergibt dann die <xref:System.Uri> Objekt, das die Überladung der <xref:System.Uri> Parameter.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Sie können ruhig zum Unterdrücken einer Warnung dieser Regel, wenn der Parameter keinen URI darstellt.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen ordnungsgemäß implementierte zeichenfolgenüberladung.

 [!code-csharp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CSharp/ca1057-string-uri-overloads-call-system-uri-overloads_1.cs)]
 [!code-cpp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CPP/ca1057-string-uri-overloads-call-system-uri-overloads_1.cpp)]
 [!code-vb[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/VisualBasic/ca1057-string-uri-overloads-call-system-uri-overloads_1.vb)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2234: Übergeben Sie System.Uri-Objekte anstelle von Zeichenfolgen](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1056: URI-Eigenschaften dürfen keine Zeichenfolgen sein](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: URI-Parameter dürfen keine Zeichenfolgen sein](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: URI-Rückgabewerte dürfen keine Zeichenfolgen sein](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)