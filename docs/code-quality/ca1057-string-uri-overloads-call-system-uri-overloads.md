---
title: 'CA1057: URI-Überladungen vom Typ string rufen Überladungen vom Typ System.Uri auf'
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
ms.openlocfilehash: dd79751c67ca5540cb22eb692b2d11c0941005a6
ms.sourcegitcommit: 1507baf3a336bbb6511d4c3ce73653674831501b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72349037"
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057: URI-Überladungen vom Typ string rufen Überladungen vom Typ System.Uri auf

|||
|-|-|
|TypeName|StringUriOverloadsCallSystemUriOverloads|
|CheckId|CA1057|
|Kategorie|Microsoft. Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Ein Typ deklariert Methoden Überladungen, die sich nur durch die Ersetzung eines Zeichen folgen Parameters mit einem <xref:System.Uri?displayProperty=fullName>-Parameter unterscheiden, und die Überladung, die den Zeichen folgen Parameter annimmt, ruft nicht die Überladung auf, die den <xref:System.Uri>-Parameter annimmt.

## <a name="rule-description"></a>Regelbeschreibung
Da die über Ladungen sich nur durch den String-oder <xref:System.Uri>-Parameter unterscheiden, wird davon ausgegangen, dass die Zeichenfolge einen URI (Uniform Resource Identifier) darstellt. Eine Zeichenfolgendarstellung eines URIs ist anfällig für Analyse- und Codierungsfehler und kann zu Sicherheitsmängeln führen. Die Klasse <xref:System.Uri> stellt diese Dienste auf sichere und sichere Weise bereit. Um die Vorteile der <xref:System.Uri>-Klasse zu nutzen, sollte die Zeichen folgen Überladung die <xref:System.Uri>-Überladung mithilfe des Zeichen folgen Arguments aufrufen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Reimplementieren Sie die Methode, die die Zeichen folgen Darstellung des URI verwendet, damit eine Instanz der <xref:System.Uri>-Klasse mithilfe des Zeichen folgen Arguments erstellt wird, und übergeben Sie dann das <xref:System.Uri>-Objekt an die Überladung mit dem <xref:System.Uri>-Parameter.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn der Zeichen folgen Parameter keinen URI darstellt.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt eine ordnungsgemäß implementierte Zeichen folgen Überladung.

[!code-csharp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CSharp/ca1057-string-uri-overloads-call-system-uri-overloads_1.cs)]
[!code-cpp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CPP/ca1057-string-uri-overloads-call-system-uri-overloads_1.cpp)]
[!code-vb[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/VisualBasic/ca1057-string-uri-overloads-call-system-uri-overloads_1.vb)]

## <a name="related-rules"></a>Verwandte Regeln
[CA2234: Übergeben Sie System.Uri-Objekte anstelle von Zeichenfolgen](../code-quality/ca2234.md)

[CA1056: URI-Eigenschaften dürfen keine Zeichenfolgen sein](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

[CA1054: URI-Parameter dürfen keine Zeichenfolgen sein](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

[CA1055: URI-Rückgabewerte dürfen keine Zeichenfolgen sein](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)