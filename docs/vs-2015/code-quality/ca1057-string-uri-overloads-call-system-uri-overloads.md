---
title: 'CA1057: URI-über Ladungen vom Typ String werden System. URI-über Ladungen aufgerufen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1057
- StringUriOverloadsCallSystemUriOverloads
helpviewer_keywords:
- StringUriOverloadsCallSystemUriOverloads
- CA1057
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: bcdb4d8333b0a4d2d06580d882cf736d4527eca4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539528"
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057: URI-Überladungen vom Typ string rufen Überladungen vom Typ System.Uri auf.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|StringUriOverloadsCallSystemUriOverloads|
|CheckId|CA1057|
|Category|Microsoft. Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Typ deklariert Methoden Überladungen, die sich nur durch die Ersetzung eines Zeichen folgen Parameters mit einem Parameter unterscheiden <xref:System.Uri?displayProperty=fullName> , und die Überladung, die den Zeichen folgen Parameter annimmt, ruft nicht die Überladung auf, die den- <xref:System.Uri> Parameter annimmt.

## <a name="rule-description"></a>Beschreibung der Regel
 Da sich die über Ladungen nur durch die Zeichenfolge/den Parameter unterscheiden <xref:System.Uri> , wird davon ausgegangen, dass die Zeichenfolge einen URI (Uniform Resource Identifier) darstellt. Eine Zeichenfolgendarstellung eines URIs ist anfällig für Analyse- und Codierungsfehler und kann zu Sicherheitsmängeln führen. Die <xref:System.Uri> -Klasse stellt diese Dienste auf sichere und sichere Weise bereit. <xref:System.Uri>Die Zeichen folgen Überladung sollte die-Überladung mithilfe des Zeichen folgen Arguments aufrufen, um die Vorteile der-Klasse zu nutzen <xref:System.Uri> .

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Implementieren Sie die-Methode, die die Zeichen folgen Darstellung des URI verwendet, so, dass eine Instanz der- <xref:System.Uri> Klasse mithilfe des Zeichen folgen Arguments erstellt wird, und übergeben Sie dann das- <xref:System.Uri> Objekt an die-Überladung, die den- <xref:System.Uri> Parameter aufweist.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn der Zeichen folgen Parameter keinen URI darstellt.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine ordnungsgemäß implementierte Zeichen folgen Überladung.

 [!code-cpp[FxCop.Design.CallUriOverload#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/cpp/FxCop.Design.CallUriOverload.cpp#1)]
 [!code-csharp[FxCop.Design.CallUriOverload#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/cs/FxCop.Design.CallUriOverload.cs#1)]
 [!code-vb[FxCop.Design.CallUriOverload#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/vb/FxCop.Design.CallUriOverload.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2234: Übergeben Sie System.Uri-Objekte anstelle von Zeichenfolgen.](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1056: URI-Eigenschaften dürfen keine Zeichenfolgen sein.](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: URI-Parameter dürfen keine Zeichenfolgen sein.](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: URI-Rückgabewerte dürfen keine Zeichenfolgen sein.](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
