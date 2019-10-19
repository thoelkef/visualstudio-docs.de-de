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
ms.openlocfilehash: ba7e7de4f3ef6336ed3d82dc1e1da03ec0bf2575
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603076"
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057: URI-Überladungen vom Typ string rufen Überladungen vom Typ System.Uri auf
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|StringUriOverloadsCallSystemUriOverloads|
|CheckId|CA1057|
|Kategorie|Microsoft. Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Typ deklariert Methoden Überladungen, die sich nur durch die Ersetzung eines Zeichen folgen Parameters mit einem <xref:System.Uri?displayProperty=fullName>-Parameter unterscheiden, und die Überladung, die den Zeichen folgen Parameter annimmt, ruft nicht die Überladung auf, die den <xref:System.Uri>-Parameter annimmt.

## <a name="rule-description"></a>Regelbeschreibung
 Da die über Ladungen sich nur durch den String/<xref:System.Uri>-Parameter unterscheiden, wird davon ausgegangen, dass die Zeichenfolge einen URI (Uniform Resource Identifier) darstellt. Eine Zeichenfolgendarstellung eines URIs ist anfällig für Analyse- und Codierungsfehler und kann zu Sicherheitsmängeln führen. Die Klasse <xref:System.Uri> stellt diese Dienste auf sichere und sichere Weise bereit. Um die Vorteile der <xref:System.Uri>-Klasse zu nutzen, sollte die Zeichen folgen Überladung die <xref:System.Uri>-Überladung mithilfe des Zeichen folgen Arguments aufrufen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Implementieren Sie die-Methode, die die Zeichen folgen Darstellung des URI verwendet, so, dass Sie mithilfe des Zeichen folgen Arguments eine Instanz der <xref:System.Uri>-Klasse erstellt, und übergeben Sie dann das <xref:System.Uri>-Objekt an die-Überladung mit dem <xref:System.Uri>-Parameter.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn der Zeichen folgen Parameter keinen URI darstellt.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine ordnungsgemäß implementierte Zeichen folgen Überladung.

 [!code-cpp[FxCop.Design.CallUriOverload#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/cpp/FxCop.Design.CallUriOverload.cpp#1)]
 [!code-csharp[FxCop.Design.CallUriOverload#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/cs/FxCop.Design.CallUriOverload.cs#1)]
 [!code-vb[FxCop.Design.CallUriOverload#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/vb/FxCop.Design.CallUriOverload.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2234: Übergeben Sie System.Uri-Objekte anstelle von Zeichenfolgen](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1056: URI-Eigenschaften dürfen keine Zeichenfolgen sein](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: URI-Parameter dürfen keine Zeichenfolgen sein](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: URI-Rückgabewerte dürfen keine Zeichenfolgen sein](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
