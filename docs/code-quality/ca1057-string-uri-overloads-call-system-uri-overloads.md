---
title: 'CA1057: URI-Überladungen der Zeichenfolge aufrufen System.Uri-Überladungen'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: cc113abf5fc1f0d47b37643c404dffade26d0899
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53891189"
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057: URI-Überladungen der Zeichenfolge aufrufen System.Uri-Überladungen

|||
|-|-|
|TypeName|StringUriOverloadsCallSystemUriOverloads|
|CheckId|CA1057|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Ein Typ deklariert methodenüberladungen, die nur durch die Ersetzung eines Zeichenfolgenparameters mit unterscheiden sich ein <xref:System.Uri?displayProperty=fullName> Parameter und die Überladung, die den Zeichenfolgenparameter akzeptiert ruft nicht die Überladung, akzeptiert die <xref:System.Uri> Parameter.

## <a name="rule-description"></a>Regelbeschreibung
 Da die Überladungen nur durch die Zeichenfolge unterscheiden oder <xref:System.Uri> Parameter die Zeichenfolge wird davon ausgegangen, dass einen uniform Resource Identifier (URI) darstellen. Eine Zeichenfolgendarstellung eines URIs ist anfällig für Analyse- und Codierungsfehler und kann zu Sicherheitsmängeln führen. Die <xref:System.Uri> Klasse stellt diese Dienste auf sichere Weise. Um die Vorteile der Nutzen der <xref:System.Uri> -Klasse, die zeichenfolgenüberladung sollte Aufrufen der <xref:System.Uri> überladen, mit dem Zeichenfolgenargument.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Erneut implementieren die Methode, die die Zeichenfolgendarstellung des URI verwendet werden, sodass es sich um eine Instanz erstellt die <xref:System.Uri> Klasse mit dem Zeichenfolgenargument und übergibt dann die <xref:System.Uri> Objekt an die Überladung, die die <xref:System.Uri> Parameter.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Es ist sicher eine Warnung dieser Regel zu unterdrücken, wenn der Zeichenfolgenparameter keinen URI darstellt.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine ordnungsgemäß implementierte überlädt.

 [!code-csharp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CSharp/ca1057-string-uri-overloads-call-system-uri-overloads_1.cs)]
 [!code-cpp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CPP/ca1057-string-uri-overloads-call-system-uri-overloads_1.cpp)]
 [!code-vb[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/VisualBasic/ca1057-string-uri-overloads-call-system-uri-overloads_1.vb)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2234: Übergeben Sie System.Uri-Objekte anstelle von Zeichenfolgen](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1056: URI-Eigenschaften dürfen keine Zeichenfolgen sein.](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: URI-Parameter dürfen keine Zeichenfolgen sein.](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: URI-Rückgabewerte sollten keine Zeichenfolgen sein](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)