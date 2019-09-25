---
title: 'CA1057: URI-Überladungen vom Typ string rufen Überladungen vom Typ System.Uri auf.'
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e6bd77a49690979ea7ab3c4619fdd578a80bb77c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235520"
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057: URI-Überladungen vom Typ string rufen Überladungen vom Typ System.Uri auf.

|||
|-|-|
|TypeName|StringUriOverloadsCallSystemUriOverloads|
|CheckId|CA1057|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Ein Typ deklariert Methoden Überladungen, die sich nur durch die Ersetzung eines Zeichen folgen Parameters mit <xref:System.Uri?displayProperty=fullName> einem Parameter unterscheiden, und die Überladung, die den Zeichen folgen Parameter annimmt, ruft <xref:System.Uri> nicht die Überladung auf, die den-Parameter annimmt.

## <a name="rule-description"></a>Regelbeschreibung
Da sich die über Ladungen nur durch die Zeichenfolge <xref:System.Uri> oder den Parameter unterscheiden, wird davon ausgegangen, dass die Zeichenfolge einen URI (Uniform Resource Identifier) darstellt. Eine Zeichenfolgendarstellung eines URIs ist anfällig für Analyse- und Codierungsfehler und kann zu Sicherheitsmängeln führen. Die <xref:System.Uri> -Klasse stellt diese Dienste auf sichere und sichere Weise bereit. Die Zeichen folgen Überladung sollte <xref:System.Uri> die-Überladung mithilfe des Zeichen folgen <xref:System.Uri> Arguments aufrufen, um die Vorteile der-Klasse zu nutzen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Reimplement die Methode, die die Zeichen folgen Darstellung des URI verwendet, damit eine Instanz der <xref:System.Uri> -Klasse mithilfe des Zeichen folgen Arguments erstellt wird, und übergibt dann das <xref:System.Uri> -Objekt an die- <xref:System.Uri> Überladung, die den-Parameter aufweist.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn der Zeichen folgen Parameter keinen URI darstellt.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt eine ordnungsgemäß implementierte Zeichen folgen Überladung.

[!code-csharp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CSharp/ca1057-string-uri-overloads-call-system-uri-overloads_1.cs)]
[!code-cpp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CPP/ca1057-string-uri-overloads-call-system-uri-overloads_1.cpp)]
[!code-vb[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/VisualBasic/ca1057-string-uri-overloads-call-system-uri-overloads_1.vb)]

## <a name="related-rules"></a>Verwandte Regeln
[CA2234: Übergeben Sie System. URI-Objekte anstelle von Zeichen folgen.](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

[CA1056: Uri-Eigenschaften dürfen keine Zeichen folgen sein.](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

[CA1054: URI-Parameter dürfen keine Zeichen folgen sein.](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

[CA1055: URI-Rückgabewerte dürfen keine Zeichen folgen sein.](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)